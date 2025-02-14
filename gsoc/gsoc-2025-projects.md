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

The `aeon` documentation is a key resource for users of the toolkit. It provides
information on how to install the toolkit, how to use the toolkit, and how to
contribute to the toolkit. The `aeon` documentation is built using `sphinx` and hosted 
on `readthedocs`. 

While there are always improvements that can be made to the general documentation itself
(e.g., improving the clarity of the text, adding more examples, etc.) for both webpages
and estimator docstrings, this project focuses on implementing functions to 
automatically link relevant API pages together and ensure new pull requests are
accompanied by the appropriate documentation. Some examples of improvements that could
be made include:

- Linking to examples to in API pages where the function/class is used similar to 
`scikit-learn` (e.g., [here](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html#gallery-examples))
- Improving the [estimator overview page](https://www.aeon-toolkit.org/en/stable/estimator_overview.html)
by further integrating the tags system or adding search and filtering functionality
- Implementing workflows to ensure that new public functionality includes a valid
docstring (i.e. has a description, parameters, returns, etc. sections where relevant)

There is a lot of potential for additional functionality, so feel free to suggest
improvements or new features outside the examples provided.

### Required Skills

- Python 3
- Git and GitHub
- Understanding of how `sphinx` is used to build documentation

Optional but useful skills:
- Understanding of GitHub Actions and writing workflows

### Expected Outcome(s)

- At least one new feature or improvement to the `aeon` documentation webpage
(outside of general text improvements)

And/Or (depending on project duration scope)

- Improvement to the `aeon` testing suite to ensure that new PRs
are accompanied by the appropriate documentation

## Project #5: Maintenance - Modernising the `aeon` linting and type checking workflows

__Complexity__: Medium

__Duration__ 90 or 175 hours

__Mentors__: Matthew Middlehurst ([@MatthewMiddlehurst](https://github.com/MatthewMiddlehurst)),
Tony Bagnall ([@TonyBagnall](https://github.com/TonyBagnall))
and Antoine Guillaume ([@baraline](https://github.com/baraline))

### Description

This project involves updating the `aeon` linting and type checking workflows to
use modern tools and ensure that the codebase is up to date with the latest
Python standards. 

The `aeon` toolkit uses `pre-commit` to run code quality checks on all code changes
and ensure that they meet the project's standards. This includes a number of checks and
formatting tools, such as `black`, `flake8`, and `isort` (see [here](https://github.com/aeon-toolkit/aeon/blob/main/.pre-commit-config.yaml)).
Over time new tools have been released such as `ruff` and tools we previously used such
as `pydocstyle` have been deprecated. The first part of this project will involve
modernising the `pre-commit` configuration to use the latest tools.

`aeon` contributors have been encouraged to add type hints to the codebase, but this
is a gradual process and there are still many parts of the codebase that are not fully
typed. A big issue we face in this is the current lack of automated testing to ensure
that implemented type hints are accurate. This second part project will involve 
implementing robust testing utilities to help contributors and reviewers ensure that
new type hints are correct.

Other ideas to improve the code quality testing in `aeon` pull requests or deliver
feedback from tests to contributors are welcome.

### Required Skills

- Python 3
- Git and GitHub
- Understanding of GitHub Actions and writing workflows

### Expected Outcome(s)

- Updated workflows for checking code quality in `aeon` pull requests
- Automated testing and utilities to help contributors implement accurate type hints
for `aeon` code.
