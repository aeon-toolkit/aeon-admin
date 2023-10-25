# Time Series Similarity Search Module

Contributors: @MatthewMiddlehurst @TonyBagnall @baraline @hadifawaz1999

## Overview

This AEP introduces a new module and base cass for time series similarity search.

## Problem Statement and Use Cases

At its simplest, similarity search is the task of finding the closest subseries in 
series X to given series q (<= length of X) given a similarity measure.

To obtain the most similar subserie, a distance vector, often called distance
profile, must be computed. This distance profile will store the similarity
between the query and all candidate subseries. In this context, the most 
similar subseries will be the one with maximize the similarity measure ( or
minimize the distance or dissimilarity).

The main research challenge for the distance profiles is the computational 
complexity. Most of the contributions in the litterature are aimed toward
optimizing the (di)similarity functions (e.g. Mueen algortihm for the 
normalized euclidean distance), proposing lower bounds to prune subseries,
or approximations methods. 

In terms of use cases, distance profiles are the base component of the matrix 
profile methods[1]. They are also used in shapelets methods, where the
shapelet is viewed as the query), convolutional kernels (e.g. Rocket) or 
more generaly, any method using a sliding window to compute a function between
a fixed query (a kernel, a shapelet, ...) and a (collection of) time series.

Altough, the computational optimizations used in the similarity search 
litterature have not been widely adopted or explored in other the less
"obvious" contexts such as shapelets.

## Implementation

The current implementation is designed around a new module named
`similarity_search`, which contains `BaseSimilaritySearch`, a 
base class for all applications that use a distance profile to
extract a set of subseries. One subclass is `TopKSimilaritySearch`,
which given a collection of time series and a query, will return 
the most `k` similar subseries given a distance function.

A submodule named `distance_profiles` contains the methods used
to compute distance profiles for different distance functions.
One additional goal of this submodule would be to provide optimized
methods to compute distance profiles for other tasks that do not fit
the similarity search module (e.g. shapelets).

## Examples code/structure (if applicable)

Base class: 

- BaseSimilaritySearch
    - methods:
      - \_\_init\_\_(distance, normalise, store_distance_profile): 
          - takes distance: function, default = euclidean.
          - wheter to use a z-normalized distance
          - if the distance profiles should be stored after calling predict
      - fit(X): 
          - takes X: a 3D array : collection of multivariate series. How other
            modules handle the case where we have a 2D array as input ? (i.e.
            is it a collection of univariate series or a multivariate series)
          - fetch the distance profile function linked to the distance and normalize parameters.
          - returns self
      - predict(q, q_index=None, exclusion_factor=2.0): 
          - takes q: a single multivariate series (internal type?) tbc
          - q_index to as a tuple (id_sample, id_timestamp) to specify if q was extracted from X
          - Initiate the boolean mask of same shape as X given to the child classes and the
            distance profile function, which store the part of the distance profile that should
            not be computed. This can be used to indicate where the query was sampled in X, but
            also during lower bound pruning to indicate which part are prunned.  
          - exlucsion_factor specify the area around q_index (+/- l//exclusion_factor) that should
            be excluded from the distance profile computation and left to np.inf.
          - Compute the means and standard deviations of the subseries in X if normalize was True.
           
    - abstract:
      - \_fit() :
      - \_predict()
      - \_iterator() maybe?

For the `distance_profile` submodule, we can distinguish different type of optimizations:
    - Direct distance function optimization (e.g. Mueen)
    - Early abandon of distance computation (e.g. EA-DTW)
    - Lower bound pruning (e.g. Keogh LB for DTW)
    
## Considerations and Alternatives

- do we even need a base class? Maybe just have a suite of functions?

## Discussion

I think base class can be useful to define the common code between some similarity search
use cases. For example, TopK search or threshold search (i.e. all subseries with a distance
bellow a threshold are returned). We might need to refine it when we extend the scope of
the module (e.g. matrix profile), as I don't think the current `BaseSimilaritySearch` class
would fit all applications.

## References

[1] https://www.cs.ucr.edu/~eamonn/MatrixProfile.html
