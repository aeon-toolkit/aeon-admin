# Deprecate Annotation Module

Contributors: [@TonyBagnall](https://github.com/TonyBagnall), [@MatthewMiddlehurst](https://github.com/MatthewMiddlehurst)

## Overview

This AEP concerns the deprecation of the annotation module, splitting its contents into 
two new modules, segmentation and anomaly detection.

## Problem Statement and Use Cases

The annotation module contains algorithms for everything that could be classed as 
annotating a series. This is a non-standard taxonomy, and is generally confusing to 
people searching for individual tasks. I think we should split segmentation, 
change point detection and anomaly detection into separate modules. I believe it would 
improve exposure and be more logical. You can call them both annotation, but then you 
can call classification/regression/forecasting prediction if you want, doesn't make it 
a good idea. 

This AEP is simply to propose two new modules, segmentation and anomaly detection. 
Segmentation is not the same as anomaly detection. Segmentation always labels each 
time point, whereas anomaly detection returns regions of interest or nothing. 
Also segmentation is more like a fit/transform transformer (transforms series into 
discrete labels) whereas anomaly detection is closer to fit/predict estimator.

In the first instance just reorganising, a simple refactor of algorithms to these
packages. We should then consider base class design and what goes there as a separate 
issue deserving their own proposals. Currently we can return sparse or dense 
representations of the annotation. My opinion would be that anomaly detection would 
return sparse and segmentation dense, although not that concerned. 

This would eventually culminate in the full deprecation of the annotation module.

Issues: [#592](https://github.com/aeon-toolkit/aeon/issues/592) [#722](https://github.com/aeon-toolkit/aeon/issues/722)

## Implementation

Summary of annotation currently:

- ClaspSegmentation: Segmentation (BaseSeriesAnnotator)
- GGS: Segmentation (no base class)
- EAAgglo: "is a non-parametric clustering approach for multivariate timeseries" Should then be in clustering, but this class extends BaseTransformer, which seems a bit odd. Name not exactly informative
- HMM: "Implements a simple HMM fitted with Viterbi algorithm." (BaseSeriesAnnotator). Seems like a full implementation
- IGTS: Segmentation (no base class)
- InformationGainSegmentation: Segmentation (SegmentationMixin)

These algorithms move to segmentation

- STRAY: robust anomaly detection in data streams with concept drift. (BaseTransformer)

The STRAY algorithms moves to anomaly_detection

then we have in sub packages:

- PyODAnnotator. "Transformer that applies outlier detector from pyOD." (BaseSeriesAnnotator)
- BaseHMMLearn (BaseSeriesAnnotator): Base class for all HMM wrappers, handles required overlap between packages.
- GaussianHMM: "Hidden Markov Model with Gaussian emissions."
- GMMHMM: "Hidden Markov Model with Gaussian mixture emissions"
- PoissonHMM: Hidden Markov Model with Poisson emissions

These are either simple wrappers or do not fit into the new categories. I would remove
them for now, unless others are in favor of keeping them.

## Considerations and Alternatives

The alternative is to leave the annotation module as it is and build on the current
structure, but as discussed above, I would not recommend this.

## Discussion

See:
https://github.com/aeon-toolkit/aeon/pull/782
https://github.com/aeon-toolkit/aeon/pull/946
https://github.com/aeon-toolkit/aeon/pull/1002
https://github.com/aeon-toolkit/aeon/pull/1441


