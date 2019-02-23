> Written with [StackEdit](https://stackedit.io/).

# Interpretable Machine Learning Notes

*Notes about the book [Interpretable Machine Learning](https://christophm.github.io/interpretable-ml-book/)*

## From the preface and introduction

- Machine learning has great potential for improving products, processes and research. But **computers usually do not explain their predictions** which is a barrier to the adoption of machine learning.

- Interpretable models:
	- Decision trees
	- Linear regression
- General model-agnostic methods for **interpreting black box models** like: 
	- Partial Dependence Plots
	- Accumulated local effects
	- Explaining individual predictions with Shapley values and LIME

All model-agnostic methods can be further differentiated based on whether they explain global model behavior across all data instances or individual predictions.

Methods explain the overall behavior of the model:

- Partial Dependence Plots
- Accumulated Local effects
- Feature Interaction
- Feature Importance
- Global Surrogate Models
- Prototypes and Criticisms

Methods explains individual predictions:

- Local Surrogate Models
- Shapley Value Explanations
- Counterfactual Explanations
- Adversarial Examples

Some methods can be used to explain both aspects of global model behavior and individual predictions:

- Individual Conditional Expectation
- Influential Instances

All above methods are devoted to supervised machine learning model.

The book focuses on machine learning models for tabular data (also called relational or structured data) and less on computer vision and natural language processing tasks.

### From 1.2 What is Machine Learning

- A major disadvantage of using machine learning is that insights about the data and the task the machine solves is hidden in increasingly complex models.
- 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3NTY4NTc4NTAsLTE0MTg4MDk5NjIsLT
EwNDYzOTI3MjIsOTEyNDg5MTEsODMwODAxMTgzLC0xNzMzODA2
MjQ1XX0=
-->