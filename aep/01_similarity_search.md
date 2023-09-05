# Time Series Similarity Search Module

## Overview

This AEP introduces a new module and base cass for time series similarity search.

## Problem Statement and Use Cases

At its simplest, similarity search is the task of finding the closest subseries in 
series X to given series q (<= length of X) given a similarity measure.

TODO: use cases and examples

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
          - iterate over X, find closest k matches, some abstract method to do the iteration
          - returns indexes of closest k /distances/series?
 
    - abstract:
      - \_fit()
      - \_predict()
      - \_iterator()

Subclasses:
    Optimisations:
        early abandon?
        Distance pruning

## Considerations and Alternatives

TODO

## Discussion

TODO

## References

TODO