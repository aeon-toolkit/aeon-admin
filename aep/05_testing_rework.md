# AEP Template

Contributors: MatthewMiddlehurst

## Overview

The current general testing framework is confusing and complicated. This AEP aims to
suggest a simplification for the general testing of estimators, based around the
`scikit-learn1` `check_estimator` method of testing.

## Problem Statement and Use Cases

Currently `aeon` uses a number of custom `pytest` fixtures and "scenario" classes to
test estimators. This is generally confusing, both to maintain and to understand the 
exact contents of a test being run. This AEP suggests a simplification of the testing
framework to use the `check_estimator` [1] and `parametrize_with_checks` [2] functions 
as a basis for general unit testing, similar to what is done in `scikit-learn`. This 
would include the removal of the `pytest` fixtures and scenario classes, and a rework 
of the current `check_estimator` method which is heavily reliant on the `pytest` 
fixtures.

This involves reworking the current tests to be run through the mentioned functions,
rather than being individual pytest `functions`. All tests would be run through a single 
function, i.e.

```python
@parametrize_with_checks(ALL_ESTIMATORS)
def test_parametrize_with_checks_classes(estimator, check):
    """Test all checks on all aeon estimators."""
    check(estimator)
```

Which would run every test function on every estimator.

This change will allow us to more easily edit the contents of these tests if necessary 
and integrate our new experimental modules into the testing framework. The testing
contents will also be more centralised, rather than split into double digit files
throughout all modules of the package.

## Implementation

1. Create proof of concept for the new testing framework and functions 
   ([#1479](https://github.com/aeon-toolkit/aeon/pull/1479)).
2. Port over all existing tests to the new framework, i.e. the current classification 
   test fixtue and the various `test_all_x` files.
3. Remove all old testing fixtures and scenario classes, swapping them for the new 
   framework or isolate to legacy frameworks.
4. Consider changing the tests available or adding and removing from the suite
   to better meet the new requirements of the package.
5. Update the documentation to reflect the new testing framework.

## Examples code/structure (if applicable)

See [#1479](https://github.com/aeon-toolkit/aeon/pull/1479)

## Considerations and Alternatives

The testing module is currently marked as experimental, so while there may be some
differences compared to previous testing for users if they use this functionality,
no deprecation is required according to the current document.

I am currently not including `BaseTransformer` and `BaseForecaster` in this update,
as they are likely to be removed or heavily overhauled in the future. This would require
keeping the old testing framework and isolating the tests for these frameworks.

## Discussion

N/A

## References

- [1] https://scikit-learn.org/stable/modules/generated/sklearn.utils.estimator_checks.check_estimator.html
- [2] https://scikit-learn.org/stable/modules/generated/sklearn.utils.estimator_checks.parametrize_with_checks.html
