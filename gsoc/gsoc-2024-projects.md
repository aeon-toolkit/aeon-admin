# GSoC 2024 Project Ideas

`aeon` is an open-source Python toolkit for time series machine learning algorithms, 
evaluation, and other time series related utilities. It based on the `scikit-learn` 
interface and is developed by a community of researchers and practitioners from a range 
of backgrounds. The GitHub repository for `aeon` is [here](https://github.com/aeon-toolkit/aeon/), 
which contains links to our project documentation and communication channels.

As an affiliated project, `aeon` is putting forward [Google Summer of Code (GSoC) 2024](https://summerofcode.withgoogle.com/)
project ideas under the [NumFOCUS](https://numfocus.org/) umbrella. We recommend that
prospective applicants look at the `aeon` [contributor guide](https://www.aeon-toolkit.org/en/stable/contributing.html#)
and [good first issues](https://github.com/aeon-toolkit/aeon/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22). 
Feel free to post and ask questions on our dedicated [GSoC 2024 discussion](https://github.com/aeon-toolkit/aeon/discussions/1121)
or on our community [Slack](https://join.slack.com/t/aeon-toolkit/shared_invite/zt-22vwvut29-HDpCu~7VBUozyfL_8j3dLA).

The projects presented here are our top picks for GSoC 2024. See our general [projects
page](https://www.aeon-toolkit.org/en/stable/mentoring.html) for more project ideas.
We are open for discussion if you are interested in another project, but we recommend
that you contact us early to discuss your ideas.

## Project #1: Implement Proximity Forest for Time Series Classification

This project involves implementing the Proximity Forest algorithm and benchmarking it 
against the original Java implementation. Depending on the speed of progress, there is 
scope for further work and experimentation with the algorithm.

__Complexity__: High

__Duration__ 350 hours

__Mentors__: Matthew Middlehurst ([@MatthewMiddlehurst](https://github.com/MatthewMiddlehurst)) 
and Tony Bagnall ([@TonyBagnall](https://github.com/TonyBagnall))

### Description

Distance-based classifiers such as k-Nearest Neighbours are popular approaches to time 
series classification. They primarily use elastic distance measures such as Dynamic Time 
Warping (DTW) to compare two series. The Proximity Forest algorithm [1] is a 
distance-based classifier for time series. The classifier creates a forest of decision
trees, where the tree splits are based on the distance between time series using 
various distance measures. A recent review of time series classification algorithms [2] 
found that Proximity Forest was the most accurate distance-based algorithm of those 
compared.

`aeon` previously had an implementation of the Proximity Forest algorithm, but it was 
not as accurate as the original implementation (the one used in the study) and was 
unstable on benchmark datasets. The goal of this project is to significantly overhaul 
the previous implementation or completely re-implement Proximity Forest in `aeon` to 
match the accuracy of the original algorithm. This will involve comparing against the 
authors' Java implementation of the algorithm as well as alternate Python versions. 
The mentors will provide results for both for alternative methods. 

Recently, the group which published the algorithm has proposed a new version of the 
Proximity Forest algorithm, Proximity Forest 2.0 [3]. This algorithm is more accurate 
than the original Proximity Forest algorithm, and does not currently have an 
implementation in `aeon` or elsewhere in Python. If time allows, the project could also 
involve implementing and evaluating the Proximity Forest 2.0 algorithm.

### Required Skills

- Python 3
- Git and GitHub
- Basic understanding of machine learning, specifically distance measures and 
decision trees for classification

Optional but useful skills:
- Writing code using `numba`
- For understanding the original implementations: Java and C++

### Expected Outcome(s)

- A Python implementation of the Proximity Forest using the `aeon` time series 
classification API.
- An evaluation of the mentees implementation against the original and other
implementations of the algorithm, showing that the implementation is as accurate as the
original and efficient enough that it is feasible to run experiments with.

### References

1. Lucas, B., Shifaz, A., Pelletier, C., O’Neill, L., Zaidi, N., Goethals,
B., Petitjean, F. and Webb, G.I., 2019. Proximity forest: an effective and scalable
distance-based classifier for time series. Data Mining and Knowledge Discovery, 33(3),
pp.607-635.
2. Middlehurst, M., Schäfer, P. and Bagnall, A., 2023. Bake off redux: a review and
experimental evaluation of recent time series classification algorithms. arXiv preprint
arXiv:2304.13029.
3. Herrmann, M., Tan, C.W., Salehi, M. and Webb, G.I., 2023. Proximity Forest 2.0: A
new effective and scalable similarity-based classifier for time series. arXiv
preprint arXiv:2304.05800.

## Project #2: ?

(SUMMARY HERE)

__Complexity__: (LOW/MEDIUM/HIGH)

__Duration__ (175/350) hours

__Mentors__: (MENTOR NAMES HERE)

### Description



### Required Skills



### Expected Outcome(s)


