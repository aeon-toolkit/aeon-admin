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
profile.

TODO: add more use cases and references

## Implementation

- new package
- new base class
- example subclass

## Examples code/structure (if applicable)

Base class: 

- BaseSimilaritySearch
    - methods:
      - \_\_init\_\_(distance, normalise?): 
          - takes distance: function, default = euclidean. 
      - fit(X): 
          - takes X: a single/multiple univariate/multivariate series (internal type?) tbc
          - returns self
      - predict(q): 
          - takes q: a single/multiple univariate/multivariate series (internal type?) tbc
          - iterate over X, find closest k matches, *some abstract method to do the iteration)
          - returns indexes of closest k /distances/series?
 
    - abstract:
      - \_fit()
      - \_predict()
      - \_iterator() maybe?

Subclasses:
    Optimisations:
        early abandon?
        Distance pruning

## Considerations and Alternatives

do we even need a base class? Maybe just have a suite of functions?

## Discussion

TODO

## References

TODO
