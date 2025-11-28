# AEP SSL

## Overview

Introducing self supervised learning for time series data, down stream task can be susbsequently used posterior to training an SSL model, so its
not dependent on classification/regression/forecasting etc. See references below for examples

## Problem Statement and Use Cases

Self-Supervised Learning  (SSL) aims to learn a laten representaiton of input data in an unsupervised mechanism, being independent of the label,
making it less at risk of overfitting the training data

### Use Cases
- semi supervision/linear probing where not enough labeled samples exist
- latent space analysis in medical fields
- can be used then for transfer learnign (see aep 06)

## Implementation

1. Networks design (use any backbone)
2. Define sub module fors techniques (contrastive, distance based, prediction based etc.)
3. Each SSL model will have its own mechanism with its own loss, independent of the backbone network used
4. It will be a sub module of collection transformation, i.e tranformation/collection/self_supervised
5. Example of file structure, assuming a contrastive learning method: aeon/transformation/collection/self_supervised/contrastive/_trilite.py
6. need of `fit` but maybe `transform` instead of `predict` as the output is a feature transformation

## Example Code/Structure

If the input series is of shape (n_samples, n_channels, n_timepoints), the SSL transformation ```X_transform``` will be of shape (n_samples, latent_dimension)

```python
from aeon.datasets import load_classification
from aeon.transformatio.collection.self_supervised.contrastive import Trilite

X, y = load_classification("ECG200")

ssl_model = Trilite()
ssl_model.fit(X)

X_transform = ssl_model.transform(X)
```

For using it in a pipeline for classification zero-shot learning for example, it can be done as follows:

```python
# Load and evaluate a SSL technique using aeon

from aeon.datasets import load_classification
from aeon.transformatio.collection.self_supervised.distance_based import Series2Vec
from aeon.classification.distance_based import KNeighborsTimeSeriesClassifier as KNN

xtrain, ytrain = load_classification("ECG200", split="train")
xtest, ytest = load_classification("ECG200", split="test")

ssl_model = Series2Vec()
ssl_model.fit(xtrain)

xtrain_transform = ssl_model.transform(xtrain)
xtest_transform = ssl_model.transform(xtest)

knn = KNN(n_neighbors=4)
knn.fit(xtrain_transform, ytrain)
score = knn.score(xtest_transform, ytest)
```

## Considerations and Alternatives

N/A

## Discussion

N/A

## References

[1] Ismail-Fawaz, Ali, et al. "Enhancing time series classification with self-supervised learning." International Conference on Agents and Artificial Intelligence (ICAART). SCITEPRESS-Science and Technology Publications, 2023.

[2] Foumani, Navid Mohammadi, et al. "Series2vec: similarity-based self-supervised representation learning for time series classification." Data Mining and Knowledge Discovery (2024): 1-25.
