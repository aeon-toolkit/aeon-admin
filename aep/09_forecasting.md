# AEP Template

Contributors: @TonyBagnall, Leo, Adam, Alex

## Overview

We have recently removed the whole legacy forecasting module. We wish to start again 
with a more tightly focussed goal in forecasting. Our priority is to develop a 
simple model for implementing forecasters from stats, machine learning and deep 
learning in a consistent way. We want to start simple and build things up, so we 
start with the following assumptions.

1. We will begin with a focus on forecasting with a single series.
2. We will use numpy input only.
3. We focus on forecasting for longer series with longer windows.
4. We look for a clean train/test devision in fit/predict and will mostly avoid 
   recursive models: forecasters trained on a given horizon are meant to forecast on 
   that horizon

## Problem Statement and Use Cases

the problem is to provide a simple interface for forecasting. This involves fitting 
a model on some training data, then making forecasts. 

There are three classes of algorithm for forecasting: statistical, machine learning 
and deep learning. The main difference is that machine learning and deep learning 
algorithms are primarily a reduction to regression through a sliding window. 

Some notes on other implementations here
https://hackmd.io/@aeon-toolkit/rJZFioiJJe

The standard interfaces for forecasting, can be summarised as follows:


```
y = a time series, usually a pd.DataFrame with requirements on columns
fcst = Forecaster(horizon) usually with a long set of parameters
fcst.fit(y) # fit the model
pred = fcst.predict(horizon) # predict horizon steps ahead
``` 
pred would usually be an array contaning horizon predictions assumed to be the time 
points directly after the end of y. Predictions are made 
recursively (by using predicted values as inputs to the next prediction).

An alternative is to combine fit and predict into a single function, forecast
```
y = a time series, usually a pd.DataFrame with requirements on columns
fcst = Forecaster() usually with a long set of parameters
fcst.fit(y) # fit the model
pred = fcst.forecast(horizon) # predict horizon steps ahead
``` 

the basic issue I have is that predict is temporally linked with fit and the 
horizon is set in fit. 
1. It makes little sense to me to embed the ability to forecast a different horizon 
   to that trained on. It can be done through some wrapper for sure, but it is 
   counter iintuitive to me
2. You cannot call  predict and pass the actual series to predict the next value for.
   For regression algorithms, there is no need for the temporal link. A regressor 
   built on a sliding window can predict a series for any window.
3. Its all built around pandas, but ultimately involves pulling them all into arrays.
   Since the aeon developers are mostly CS facing and not users of data frames, it 
   would be better to just use arrays. 

I like the distinction between learning a model from train data, then deploying it 
for new data. This is what I am going for, not sure though whether to have one or 
both. 

## Design and uses

Base class model:

```python

class BaseForecaster(BaseSeriesEstimator, ABC):
    """
    Abstract base class for time series forecasters.

    The base forecaster specifies the methods and method signatures that all
    forecasters have to implement. Attributes with an underscore suffix are set in the
    method fit.

    Parameters
    ----------
    horizon : int, default =1
        The number of time steps ahead to forecast. If horizon is one, the forecaster
        will learn to predict one point ahead
    window : int or None
        The window prior to the current time point to use in forecasting. So if
        horizon is one, forecaster will train using points $i$ to $window+i-1$ to
        predict value $window+i$. If horizon is 4, forecaster will used points $i$
        to $window+i-1$ to predict value $window+i+3$. If None, the algorithm will
        internally determine what data to use to predict `horizon` steps ahead.

    To Do
    -----
    axis
    """

    def __init__(self, horizon=1, window=None):
        self.horizon = horizon
        self.window = window
        self._is_fitted = False
        super().__init__(axis=1)

    @abstractmethod
    def fit(self, X):
        """Fit forecaster to series X.

        Parameters
        -------
        X : np.ndarray
            A time Time series on which to learn a forecaster
        Returns
        -------
        self
            Fitted estimator
        """
        ...

    @abstractmethod
    def predict(self, X):
        """

        Parameters
        -------
        X : np.ndarray
            A time Time series to forecast the next horizon value of 

        Returns
        -------
        float
            single prediction.
        """
        ...

    @abstractmethod
    def forecast(self, X):
        """

        basically fit_predict
        Returns
        -------
        np.ndarray
            single prediction directly after the last point in X.
        """
        ...

```

## Examples code/structure (if applicable)

[Include any example code or structure that would be used to implement the AEP. Links
to a pull request are also acceptable]

## Considerations and Alternatives

[Describe any considerations i.e. backwards compatability and alternatives that 
were considered]

## Discussion

[Include or link to any discussion points that were raised during the AEP process]

## References

[Include any references to external resources or publications that are pointed to 
in the AEP]