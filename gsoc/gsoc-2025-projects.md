# GSoC 2025 Project Ideas

`aeon` is an open-source Python toolkit for time series machine learning algorithms, 
evaluation, and other time series related utilities. It based on the `scikit-learn` 
interface and is developed by a community of researchers and practitioners from a range 
of backgrounds. The GitHub repository for `aeon` is [here](https://github.com/aeon-toolkit/aeon/), 
which contains links to our project documentation and communication channels.

As an affiliated project, `aeon` is putting forward [Google Summer of Code (GSoC) 2025](https://summerofcode.withgoogle.com/)
project ideas under the [NumFOCUS](https://numfocus.org/) umbrella. We recommend that
prospective applicants look at the `aeon` [contributor guide](https://www.aeon-toolkit.org/en/latest/contributing.html#)
and [good first issues](https://github.com/aeon-toolkit/aeon/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22). 
Feel free to post and ask questions on our dedicated [GSoC 2025 discussion](https://github.com/aeon-toolkit/aeon/discussions/2530)
or on our community [Slack](https://join.slack.com/t/aeon-toolkit/shared_invite/zt-22vwvut29-HDpCu~7VBUozyfL_8j3dLA).

The projects presented here are our top picks for GSoC 2025. See our general [projects
page](https://www.aeon-toolkit.org/en/stable/mentoring.html) for more project ideas.
We are open for discussion if you are interested in another project, but we recommend
that you contact us early to discuss your ideas.

## Project #1: Clustering - Distance-Based time series clustering algorithms

This project involves implementing clustering algorithms with integration to our
`distances` module.

__Complexity__: High

__Duration__ 350 hours

__Mentors__: Chris Holder ([@chrisholder](https://github.com/chrisholder)), 
Matthew Middlehurst ([@MatthewMiddlehurst](https://github.com/MatthewMiddlehurst)) 
and Tony Bagnall ([@TonyBagnall](https://github.com/TonyBagnall))

### Description

Clustering algorithms making use of distance measures are popular approaches for time 
series clustering. While well-known measures such as Euclidean Distance (ED) are used 
for feature vector clustering, algorithms can be adapted for time series data by using 
elastic distances such as Dynamic Time Warping (DTW) to compare two series. The `aeon` 
implementation of various distance measures and clustering algorithms were recently 
used to evaluate the effectiveness of different elastic distances for clustering [1]. 

While the `aeon` `distances` module is already extensive, there are still clusterers 
that could be implemented. `aeon` currently has common algorithms such as KMeans and
KMedoids, but is missing algorithms such as Density Peaks [2], DBSCAN [3] and 
Hierarchical clustering approaches. The project will involve implementing and evaluating 
some of these, and ensuring they are properly integrated to use the wide variety of 
functions in the `distances` module.

### Required Skills

- Python 3
- Git and GitHub
- Basic understanding of machine learning, specifically clustering algorithms and 
distance measures

Optional but useful skills:
- Writing code using `numba`
- For understanding the alternative implementations: Java

### Expected Outcome(s)

- A Python implementation of one or more algorithms using the `aeon` time series 
classification API.
- An evaluation of the mentees implementation against alternative
implementations of the algorithm, showing that the implementation is as accurate 
and efficient enough that it is feasible to run experiments with.

### References

1. Holder, C., Middlehurst, M. and Bagnall, A., 2024. A review and evaluation of 
elastic distance functions for time series clustering. Knowledge and Information 
Systems, 66(2), pp.765-809.
2. Rodriguez, A. and Laio, A., 2014. Clustering by fast search and find of density 
peaks. science, 344(6191), pp.1492-1496.
3. Ester, M., Kriegel, H.P., Sander, J. and Xu, X., 1996, August. A density-based 
algorithm for discovering clusters in large spatial databases with noise. In kdd 
(Vol. 96, No. 34, pp. 226-231).

## Project #2: Forecasting - Implementing and evaluating machine learning forecasters

__Complexity__: High

__Duration__ 350 hours

__Mentors__: Tony Bagnall ([@TonyBagnall](https://github.com/TonyBagnall))
and Matthew Middlehurst ([@MatthewMiddlehurst](https://github.com/MatthewMiddlehurst)) 

### Description

todo

### Required Skills

- todo

### Expected Outcome(s)

- todo

### References

1. todo

## Project #3: Forecasting - Deep learning for forecasting

__Complexity__: High

__Duration__ 350 hours

__Mentors__: Ali Ismail-Fawaz ([@hadifawaz1999](https://github.com/hadifawaz1999)),
Tony Bagnall ([@TonyBagnall](https://github.com/TonyBagnall))
and Matthew Middlehurst ([@MatthewMiddlehurst](https://github.com/MatthewMiddlehurst)) 

### Description

todo

### Required Skills

- todo

### Expected Outcome(s)

- todo

### References

1. todo

## Project #4: Documentation - Improving the `aeon` documentations interactivity and testing

__Complexity__: Medium

__Duration__ 90 or 175 hours

__Mentors__: Matthew Middlehurst ([@MatthewMiddlehurst](https://github.com/MatthewMiddlehurst)),
Tony Bagnall ([@TonyBagnall](https://github.com/TonyBagnall))
and Antoine Guillaume ([@baraline](https://github.com/baraline))

### Description

todo

### Required Skills

- todo

### Expected Outcome(s)

- todo

## Project #5: Maintenance - Modernising the `aeon` linting and type checking workflow

__Complexity__: Medium

__Duration__ 90 or 175 hours

__Mentors__: Matthew Middlehurst ([@MatthewMiddlehurst](https://github.com/MatthewMiddlehurst)),
Tony Bagnall ([@TonyBagnall](https://github.com/TonyBagnall))
and Antoine Guillaume ([@baraline](https://github.com/baraline))

### Description

todo

### Required Skills

- todo

### Expected Outcome(s)

- todo