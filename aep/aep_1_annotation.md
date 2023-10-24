# AEP Annotation Module

Contributors: TonyBagnall, 

https://github.com/aeon-toolkit/aeon/issues/592


## Overview

The annotation module contains algorithms for everything that could be classed as annotating a series. This is a non standard taxonomy. I think I would split segmentation, change point detection and anomaly detection into separate modules. I believe it would improve exposure and be more logical. You can call them both annotation, but then you can call classification/regression/forecasting prediction if you want, doesnt make it a good idea. 

This AEP is simply to propose two new modules, segmentation and annotation, in the first instance just reorganising, a simple refactor

We should then consider base class design and what goes there as a separate issue. Currently we can return sparse or dense representations of the annotation. My opinion would be that anomaly detection would return sparse and segmentation dense, although not that concerned. 

## Problem Statement and Use Cases

Segmentation is not the same as anomaly detection. Segmentation always labels each time point, whereas anomaly detection returns regions of interest or nothing. Also segmentation is more like a fit/transform transformer (transforms series into discrete labels) whereas anomaly detection is closer to fit/predict estimator.

[Include an example of how the AEP contents would be used]

## Implementation

[Describe the steps required for the implementation of the AEP contents]

## Examples code/structure (if applicable)



summary of annotation currently:

ClaspSegmentation: Segmentation (BaseSeriesAnnotator)
GGS: Segmentation (no base class)
EAAgglo: "is a non-parametric clustering approach for multivariate timeseries" Should then be in clustering, but this class extends BaseTransformer, which seems a bit odd. Name not exactly informatibe
HMM: "Implements a simple HMM fitted with Viterbi algorithm." (BaseSeriesAnnotator). Seems like a full implementation
IGTS: Segmentation (no base class)
InformationGainSegmentation: Segmentation (SegmentationMixin)
STRAY: robust anomaly detection in data streams with concept drift. (BaseTransformer)

then we have in sub packages
PyODAnnotator. "Transformer that applies outlier detector from pyOD." (BaseSeriesAnnotator)

in hmm_learn package which wraps https://github.com/hmmlearn/hmmlearn
BaseHMMLearn (BaseSeriesAnnotator): Base class for all HMM wrappers, handles required overlap between packages.
GaussianHMM: "Hidden Markov Model with Gaussian emissions."
GMMHMM: "Hidden Markov Model with Gaussian mixture emissions"
PoissonHMM: Hidden Markov Model with Poisson emissions

there is also a base and a plotting subpackage.

phase 1: 
segmentation: IGTS, GGS, Clasp
anomaly_detection: STRAY

then work the rest out as we go.

## Considerations and Alternatives

the annotation module is a mess, we should do something.

## Discussion

see 
https://github.com/aeon-toolkit/aeon/pull/782
https://github.com/aeon-toolkit/aeon/issues/803
https://github.com/aeon-toolkit/aeon/issues/802
https://github.com/aeon-toolkit/aeon/issues/794


