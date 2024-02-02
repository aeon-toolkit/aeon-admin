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

## Project #2: Improving the computational complexity of the Shapelet Transform 

The goal of this project is to propose a new implementation for the Shapelet Transform [1]
algorithm based on the computational optimization offered by Similarity Search algorithms,
and benchmark it against the current aeon implementation. Depending on the speed of progress,
the implementation could also be adapted to the case of the Dilated Shapelet Transform [5].

__Complexity__: High

__Duration__ 350 hours

__Mentors__: Antoine Guillaume ([@baraline](https://github.com/baraline)) and
Ali Ismail-Fawaz ([@hadifawaz1999](https://github.com/hadifawaz1999))

### Description

A shapelet is defined as a time series subsequence representing a pattern of interest
that we wish to search for in time series data. Shapelet-based algorithms can be used
for a wide range of time series tasks. In this project, we will focus on its core
application, which is to create an embedding of the input time series.

Our goal in this project will be to optimize the code related to the shapelet
transform method, which takes as input a set of shapelets and a time series dataset,
and give as output a tabular dataset containing the features characterizing the
presence (or absence) of each shapelet in the input time series (more information
in [1] and [2]).

Similarity search is another field of time series, which has proposed greatly optimized
algorithms (see [3] and [4]) for the task of finding the best matches of a subsequence
inside another time series. As this task is extremely similar to what is done in the
shapelet transform, we want to adapt these algorithms to the context of shapelets,
in order to achieve significant speed-ups.

### Required Skills

- Python 3
- Git and GitHub
- Array manipulation with numpy
- Basic understanding of machine learning, specifically distance measures

Optional but useful skills:
- Writing code using `numba`

### Expected Outcome(s)

- A Python implementation of the Shapelet Transform using the computational 
optimization from Similarity Search algorithms.
- An evaluation of the mentees implementation against the original, showing that
the implementation produces the same output space given the same input.
- A benchmark of the mentees implementation against the original, showing the 
performance gains.

### References

1. Hills, J., Lines, J., Baranauskas, E., Mapp, J. and Bagnall, A., 2014.
Classification of time series by shapelet transformation. Data mining and knowledge
discovery, 28, pp.851-881.
2. Bostrom, A. and Bagnall, A., 2017. Binary shapelet transform for multiclass time
series classification. Transactions on Large-Scale Data-and Knowledge-Centered Systems
XXXII: Special Issue on Big Data Analytics and Knowledge Discovery, pp.24-46.
3. Yeh, C.C.M., Zhu, Y., Ulanova, L., Begum, N., Ding, Y., Dau, H.A., Silva, D.F.,
Mueen, A. and Keogh, E., 2016, December. Matrix profile I: all pairs similarity joins
for time series: a unifying view that includes motifs, discords and shapelets. In 2016
IEEE 16th international conference on data mining (ICDM) (pp. 1317-1322). Ieee.
4. Zhu, Y., Zimmerman, Z., Senobari, N.S., Yeh, C.C.M., Funning, G., Mueen, A., Brisk,
P. and Keogh, E., 2016, December. Matrix profile ii: Exploiting a novel algorithm and
gpus to break the one hundred million barrier for time series motifs and joins. In 2016
IEEE 16th international conference on data mining (ICDM) (pp. 739-748). IEEE.
5. Guillaume, A., Vrain, C. and Elloumi, W., 2022, June. Random dilated shapelet
transform: A new approach for time series shapelets. In International Conference on
Pattern Recognition and Artificial Intelligence (pp. 653-664). Cham: Springer
International Publishing.


## Project #3: Machine learning from EEG with aeon-neuro

The goal of this project is to help develop the `aeon` sister toolkit, `aeon-neuro` 
to provide structured tools for improved machine learning from EEG data.

__Complexity__: High

__Duration__ 350 hours

__Mentors__: Tony Bagnall ([@TonyBagnall](https://github.com/TonyBagnall)) and Aiden 
Rushbrooke ([@AidenRushbrooke](https://github.com/AidenRushbrooke))

### Description

EEG (Electroencephalogram) data are high dimensional time series that are used in
medical, psychology and brain computer interface research. For example, EEG are
used to detect epilepsy and to control decvices such as mice. There is a huge body
of work on analysing and learning from EEG, but there is a wide disparity of
tools, practices and systems used. This project will help members of the `aeon`
team who are currently researching techniques for EEG classification [1] and
developing an aeon sister toolkit, `aeon-neuro` (link [here](https://github.com/aeon-toolkit/aeon-neuro)). 
We will work together to improve the structure and documentation for `aeon-neuro`, help 
integrate the toolkit with existing EEG toolkits such as NM [2], provide interfaces to 
standard data formats such as BIDS [3] and help develop and assess a range of EEG 
classification algorithms.

### Required Skills

- Python 3
- Git and GitHub
- Array manipulation with numpy
- Basic understanding of machine learning, specifically classification algorithms

### Expected Outcome(s)

- Improved documentation and structure for the `aeon-neuro` toolkit.
- Better integration with existing EEG toolkits and data formats.
- Increased functionality for feature extraction and classification of EEG data.

### References

1. Rushbrooke, A., Tsigarides, J., Sami, S. and Bagnall, A., 2023, June. Time Series 
Classification of Electroencephalography Data. In International Work-Conference on 
Artificial Neural Networks (pp. 601-613). Cham: Springer Nature Switzerland.
2. MNE Toolkit, https://mne.tools/stable/index.html
3. The Brain Imaging Data Structure (BIDS) standard, https://bids.neuroimaging.io/

## Project #4: Machine Learning for Time Series Forecasting

The goal of this project is to help develop the `aeon` forecasting package to make 
it easier to use regression algorithms and improve the functionality.

__Complexity__: High

__Duration__ 350 hours

__Mentors__: Tony Bagnall ([@TonyBagnall](https://github.com/TonyBagnall)) and 
Matthew Middlehurst ([@MatthewMiddlehurst](https://github.com/MatthewMiddlehurst)) 

### Description

This project will investigate algorithms for forecasting based on traditional machine
learning (tree based) and time series machine learning (transformation based). Note
this project will not involve deep learning based forecasting. It will involve
helping develop the `aeon` framework to work more transparently with ML algorithms,
evaluating regression algorithms already in `aeon`[1] for forecasting problems [2] and
implementing at least one algorithm from the literature not already in `aeon`, such as
SETAR-Tree [3].

### Required Skills

- Python 3
- Git and GitHub
- Basic understanding of forecasting.
- Basic understanding of machine learning, specifically decision trees.

### Expected Outcome(s)

- Contributions to the `aeon` forecasting module. 
- Implementation of a machine learning forecasting algortihms. 
- Help write up results for a technical report/academic paper (depending on outcomes).

### References

1. Guijo-Rubio, D., Middlehurst, M., Arcencio, G., Silva, D.F. and Bagnall, A., 2023. 
Unsupervised feature based algorithms for time series extrinsic regression. 
arXiv preprint arXiv:2305.01429.
2. https://forecasters.org/resources/time-series-data/
3. Godahewa, R., Webb, G.I., Schmidt, D. and Bergmeir, C., 2023. SETAR-Tree: a novel 
and accurate tree algorithm for global time series forecasting. Machine Learning, 
pp.1-37.

