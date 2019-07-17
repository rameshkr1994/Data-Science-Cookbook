 - List item

> Written with [StackEdit](https://stackedit.io/).

# Interpretable Machine Learning Example: Fraud Detection Scorecard using LIME

This [webpage](https://shiring.shinyapps.io/fraud_example_dashboard/#section-test-case-result) shows and example of a Dashboard for Fraud Detection using LIME to explain how each factor contributes to the final score. Below there is an image of that dashboard:

![](https://github.com/markeyser/Data-Science-Cookbook/blob/master/imgs/Fraud-Detection-Dashboard-LIME.png?raw=true)

A couple of references related to the above dashboard:

- [Data Science for Fraud Detection](https://blog.codecentric.de/en/2017/09/data-science-fraud-detection/ "Data Science for Fraud Detection")
- [Explaining complex machine learning models with LIME](https://shiring.github.io/machine_learning/2017/04/23/lime)

![](https://github.com/markeyser/Data-Science-Cookbook/blob/master/imgs/Fraud-Detection-Dashboard-Bin.png?raw=true)

The authors uses [OneR](https://cran.r-project.org/web/packages/OneR/OneR.pdf) R library to bin continuous variables:

![](https://github.com/markeyser/Data-Science-Cookbook/blob/master/imgs/Fraud-Detection-Dashboard-ML-OneR.png?raw=true)

The ML model:

![](https://github.com/markeyser/Data-Science-Cookbook/blob/master/imgs/Fraud-Detection-Dashboard-LIME-ML.png?raw=true)

The example is based on an example data set about monetary transactions in e-commerce (source: [Kaggle](https://www.kaggle.com/ntnu-testimon/paysim1)).









<!--stackedit_data:
eyJoaXN0b3J5IjpbNDA1NjQ2Mjk3XX0=
-->