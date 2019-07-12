


> Written with [StackEdit](https://stackedit.io/).

# Overfitting Notes

## Small Data problems

Problems of small-data are numerous, but mainly revolve around high variance:

-   **Over-fitting**  becomes much harder to avoid
-   You don’t only over-fit to your training data, but sometimes you over-fit to your validation set as well.
-   **Outliers**  become much more dangerous.
-   Noise in general becomes a real issue, be it in your target variable or in some of the features.

## Solutions for small data

**Stick to simple models**

More precisely: stick to a limited set of hypotheses. One way to look at predictive modeling is as a search problem. From an initial set of possible models, which is the most appropriate model to fit our data? In a way, each data point we use for fitting down-votes all models that make it unlikely, or up-vote models that agree with it. When you have heaps of data, you can afford to explore huge sets of models/hypotheses effectively and end up with one that is suitable. When you don’t have so many data points to begin with, you need to start from a fairly small set of possible hypotheses (e.g. the set of all linear models with 3 non-zero weights, the set of decision trees with depth <= 4, the set of histograms with 10 equally-spaced bins). This means that you rule out complex hypotheses like those that deal with non-linearity or feature interactions. This also means that you can’t afford to fit models with too many degrees of freedom (too many weights or parameters). Whenever appropriate, use strong assumptions (e.g. no negative weights, no interaction between features, specific distributions, etc.) to restrict the space of possible hypotheses.

**Pool data when possible**

Are you building a personalized spam filter? Try building it on top of a universal model trained for all users. Are you modeling GDP for a specific country? Try fitting your models on GDP for all countries for which you can get data, maybe using importance sampling to emphasize the country you’re interested in. Are you trying to predict the eruptions of a specific volcano? … you get the idea.

**Limit Experimentation**

Don’t over-use your validation set. If you try too many different techniques, and use a hold-out set to compare between them, be aware of the statistical power of the results you are getting, and be aware that the performance you are getting on this set is not a good estimator for out of sample performance.

**Do clean up your data**

With small data sets, noise and outliers are especially troublesome. Cleaning up your data could be crucial here to get sensible models. Alternatively you can restrict your modeling to techniques especially designed to be robust to outliers. (e.g.  [Quantile Regression](https://en.wikipedia.org/wiki/Quantile_regression))

**Do perform feature selection**

I am not a big fan of explicit feature selection. I typically go for regularization and model averaging (next two points) to avoid over-fitting. But if the data is truly limiting, sometimes explicit feature selection is essential. Wherever possible, use domain expertise to do feature selection or elimination, as brute force approaches (e.g. all subsets or greedy forward selection) are as likely to cause over-fitting as including all features.

**Do use Regularization**

Regularization is an almost-magical solution that constraints model fitting and reduces the effective degrees of freedom without reducing the actual number of parameters in the model.  **L1 regularization**  produces models with fewer non-zero parameters, effectively performing implicit feature selection, which could be desirable for explainability of performance in production, while  **L2 regularization**  produces models with more conservative (closer to zero) parameters and is effectively similar to having strong zero-centered priors for the parameters (in the Bayesian world). L2 is usually better for prediction accuracy than L1.

![](https://miro.medium.com/max/554/1*CwnSVcr9rZa3pllDrRP71Q.png)

**Do use Model Averaging**

Model averaging has similar effects to regularization is that it reduces variance and enhances generalization, but it is a generic technique that can be used with any type of models or even with heterogeneous sets of models. The downside here is that you end up with huge collections of models, which could be slow to evaluate or awkward to deploy to a production system. Two very reasonable forms of model averaging are Bagging and Bayesian model averaging.

![](https://miro.medium.com/max/630/1*LQYmYT1t4QqGGnho-zVe0g.png)
Each of the red curves is a model fitted on a few data points

![](https://miro.medium.com/max/630/1*-RadM0WAtEHd0HIAxQAawQ.png)
But averaging all these high variance models gets us a smooth output that is remarkably close to the original distribution [Pattern Recognition and Machine Learning](http://research.microsoft.com/en-us/um/people/cmbishop/prml/webfigs.htm)

**Try Bayesian Modeling and Model Averaging**

Again, not a favorite technique of mine, but Bayesian inference may be well suited for dealing with smaller data sets, especially if you can use domain expertise to construct sensible priors.

**Prefer Confidence Intervals to Point Estimates**

It is usually a good idea to get an estimate of confidence in your prediction in addition to producing the prediction itself. For regression analysis this usually takes the form of predicting a range of values that is calibrated to cover the true value 95% of the time or in the case of classification it could be just a matter of producing class probabilities. This becomes more crucial with small data sets as it becomes more likely that certain regions in your feature space are less represented than others. Model averaging as referred to in the previous two points allows us to do that pretty easily in a generic way for regression, classification and density estimation. It is also useful to do that when evaluating your models. Producing confidence intervals on the metrics you are using to compare model performance is likely to save you from jumping to many wrong conclusions.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY0NjM4MjksMTgzOTc5NjAyNCwxNTY1Nj
gwNjM0LC0xODI0MDE2MDQ1XX0=
-->