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

#
## Module structure :
```
- aeon/
|---- similarity_search/
|-------- BaseSimilaritySearch.py
|-------- query_search/
|------------ BaseQuerySearch.py
|-------- series_search/
|------------ BaseSeriesSearch.py
|-------- index_search/
|------------ BaseIndexSearch.py
```

-  Query search : Given a query Q and a series/collection X, evaluate the similarity between Q and each admissible candidate in X.
-  Series search : Given a length parameter (for now, we add techniques that don't require it later) do a query search for all admissible queries in a series/collection X. In the naive case, this is simply a broadcasting of query search, but more optimized algorithms exists for this case (e.g. STUMP/STOMP for Euclidean distance)
-  Index search : Given a series/collection X and a length parameter (again, for now), build an indexing (e.g.what the Faiss library does) of all admissible candidates in X. Then, this indexing can be used as an estimator to answer query search tasks. This is generally used when you have a frozen historical set and want fast answers for new queries / when the inputs do not fit in memory.

## Expected data and internal input conversion :

We could accept series/collection in numpy and series in pd.Series data as input, but we would ideally convert all of it to numpy collection, and make use of the axis argument we introduced in other modules to avoid the channel problem:

For query search, we would implement heavy computation numba functions in a series case and loop over it with the collection. This can for example allow passing down (between series of a collection X) best-so-far values when doing early abandon or pruning with lower bounds.

- The same reasoning apply to series search.
- The indexing case generally work with out-of-memory data, and require updates after loading new parts of the dataset, which are generally made of collections/big series.

## Interaction with other modules:

We would still use the distance module for the naive search cases, which are the one without speed-ups (which can lead to exact or approximative results). It would also be nice to offer some visualisation through the visualisation module.
As for the reverse, which is which aeon estimator could benefit from the similarity search module speed-ups, it is still to be explored.

## Documentation and notebooks:

I would like to continue to have 3 type of notebooks for similarity search :

-  A benchmark notebook, which would show the effect of different speed-up option, and would help us determine which one to put as "default" speed-ups for a given distance function.
-  An example notebook, which shows how to use the estimators on some toy cases and how to visualize the results
-  A more theoretical one, which would explain the maths behind the different speed-ups and the base tasks.

## Discussion

Open to discussion

## References

[1] https://www.cs.ucr.edu/~eamonn/MatrixProfile.html
