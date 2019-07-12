


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


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYwMTczMTUzLDE1NjU2ODA2MzQsLTE4Mj
QwMTYwNDVdfQ==
-->