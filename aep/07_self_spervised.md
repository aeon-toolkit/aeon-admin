# AEP SSL

## Overview

Introducing self supervised learning for time series data, down stream task can be susbsequently used posterior to training an SSL model, so its
not dependent on classification/regression/forecasting etc. See references below for examples

## Problem Statement and Use Cases

Self-Supervised Learning  (SSL) aims to learn a laten representaiton of input data in an unsupervised mechanism, being independent of the label,
making it less at risk of overfitting the training data

### Use Cases
- semi supervision/linear probing where not enough labeled samples exist
- latent space analysis in medical fields
- can be used then for transfer learnign (see aep 06)

## Implementation

1. Networks design (use any backbone)
2. Define sub module fors techniques (contrastive, distance based, prediction based etc.)
3. Each SSL model will have its own mechanism with its own loss, independent of the backbone network used

## Example Code/Structure

```python
# Load and evaluate a SSL technique using aeon

from aeon.datasets import load_classification
from aeon.self_supervised.distance_based import Series2Vec

# labels not used for the phase of SSL, can be loaded if needed posterior to SSL training and predicting
xtrain, _ = load_classification("ECG200", split="train")
xtest, _ = load_classification("ECG200", split="test")

ssl_model = Series2Vec()
ssl_model.fit(xtrain)

latent_train = ssl_model.predict(xtrain) # produce latent features of train samples
latent_test = ssl_model.predict(xtrain) # produce latent features of test samples
```

## Considerations and Alternatives

N/A

## Discussion

N/A

## References

[1] [TRILITE](https://hal.science/hal-04143083/document)
[2] [series2vec](https://www.researchgate.net/profile/Navid-Mohammadi-Foumani/publication/376683892_Series2Vec_Similarity-based_Self-supervised_Representation_Learning_for_Time_Series_Classification/links/6583a4c70bb2c7472bfbd4d2/Series2Vec-Similarity-based-Self-supervised-Representation-Learning-for-Time-Series-Classification.pdf)
