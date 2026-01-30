# AEP UDA

## Overview

Introducing a benchmark module for evaluating Unsupervised Domain Adaptation (UDA) techniques for time series classification using various backbones with different techniques for doing domain adaptation.

## Problem Statement and Use Cases

UDA for time series data is underexplored despite its importance in fields like medicine, manufacturing, and earth observation. This AEP addresses this gap by providing access to UDA methods, helping improve models for unlabeled target data.

### Use Cases
- Medical diagnostics
- Predictive maintenance in manufacturing
- Environmental monitoring
- Human activity recognition

## Implementation

1. Compile a dataset with source and target seperation.
2. Design a standardized evaluation framework.
3. Integrate neural network backbones like Inception.
4. Evaluate UDA techniques using the framework.

## Example Code/Structure

```python
# Load and evaluate a UDA technique on the benchmark dataset

import benchmark_framework

dataset = benchmark_framework.load_dataset(x_source,y_source,x_target,y_target)
uda_model = benchmark_framework.UDA_Model(backbone='Inception')
results = uda_model.evaluate(dataset)
print(results)
```

## Considerations and Alternatives

- Ensure compatibility with existing UDA tools.
- Explore alternative neural network backbones and evaluation metrics.

## Discussion

N/A

## References

- [Deep Unsupervised Domain Adaptation for Time Series Classification: a Benchmark](https://arxiv.org/abs/2312.09857)