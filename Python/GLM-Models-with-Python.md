
> Written with [StackEdit](https://stackedit.io/).

# GLM models in Python

## Different option to implement GLM models using Python
The following Python libraries provide GLM implementation using Python:
- scikit-learn
- h2o
- StatsModels
- TensorFlow
- PyTorch
- PySpark

### GLM with scikit-learn

- As at today you can only find there logistic and gaussian distributions implemented. 
- But really soon we are going to have the whole GLM family (Gamma, Poisson, Tweedie, etc.)

References:

- [Auto  examples linear model plot tweedie regression insurance claims](https://63035-843222-gh.circle-artifacts.com/0/doc/auto_examples/linear_model/plot_tweedie_regression_insurance_claims.html#sphx-glr-download-auto-examples-linear-model-plot-tweedie-regression-insurance-claims-py)
- [https://github.com/scikit-learn/scikit-learn/pull/9405](https://github.com/scikit-learn/scikit-learn/pull/9405)
- [https://github.com/scikit-learn/scikit-learn/issues/5975](https://github.com/scikit-learn/scikit-learn/issues/5975)

### GLM with h2o

- They already have implemented for Python and R the whole GLM framework including cross-validation, etc. 
- The problem is that h2o cannot be installed in a corporate laptop due to the company firewall.
- Another issue is that you are forced to do the data management using h2o tools. It seems you cannot use pandas or matplotlib for example.
- Another issue is that at least u

References:

- 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI1OTM1NDMwMF19
-->