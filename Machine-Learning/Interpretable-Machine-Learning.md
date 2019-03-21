> Written with [StackEdit](https://stackedit.io/).

You c

# Interpretable Machine Learning Notes

*Notes about the book [Interpretable Machine Learning](https://christophm.github.io/interpretable-ml-book/)*. I also have a pdf copy of the book on EverNote.

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
- You need millions of numbers to describe a deep neural network, and there is no way to understand the model in its entirety. 
- Other models, such as the random forest, consist of hundreds of decision trees that “vote” for predictions. To understand how the decision was made, you would have to look into the votes and structures of each of the hundreds of trees.
- That just does not work no matter how clever you are or how good your working memory is. 
- The best performing models are often blends of several models (also called ensembles) that cannot be interpreted, even if each single model could be interpreted. 
- If you focus only on performance, you will automatically get more and more opaque models. Just take a look at [interviews with winners on the kaggle.com machine learning competition platform](http://blog.kaggle.com/): The winning models were mostly ensembles of models or very complex models such as boosted trees or deep neural networks.
### From intro to chapter 2 Interpretability

There is no mathematical definition of interpretability. A (non-mathematical) definition I like by Miller (2017)[3](https://christophm.github.io/interpretable-ml-book/interpretability.html#fn3) is: **Interpretability is the degree to which a human can understand the cause of a decision.**Another one is: **Interpretability is the degree to which a human can consistently predict the model’s result**  [4](https://christophm.github.io/interpretable-ml-book/interpretability.html#fn4). The higher the interpretability of a machine learning model, the easier it is for someone to comprehend why certain decisions or predictions have been made. A model is better interpretable than another model if its decisions are easier for a human to comprehend than decisions from the other model. 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NzE0NjUwMTNdfQ==
-->