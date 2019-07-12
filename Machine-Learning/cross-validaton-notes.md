


> Written with [StackEdit](https://stackedit.io/).

> General advice for big dataset usually k = 3 or k = 5 is a preferred option while in small datasets it is recommended to use Leave one out.

Reference: [Cross validation](https://towardsdatascience.com/cross-validation-70289113a072)

> Larger K means less bias towards overestimating the true expected error (as training folds will be closer to the total dataset) but higher variance and higher running time (as you are getting closer to the limit case: Leave-One-Out CV).

Reference: [how to calculate the fold number k fold in cross validation](https://datascience.stackexchange.com/questions/28158/how-to-calculate-the-fold-number-k-fold-in-cross-validation)

The reason why we divide the data into training and validation sets was to use the validation set to estimate how well is the model trained on the training data and how well it would perform on the unseen data. Logical conclusion would be that more partition (larger size of K) the better it is but keep in mind that more splits would reduce the size of validation set. In other words, you won’t have sufficient samples in validation set to confidently evaluate a model.

![](https://qph.fs.quoracdn.net/main-qimg-29c6f21ce298acfa228f37448f844ab8)

Therefore, the choice of number of folds must allow the size of each validation partition to be large enough to provide a fair estimate of the model’s performance on it and at the same time K shouldn’t be be too small, say 2, such that we don’t have enough trained models to evaluate.

**In general, you can keep around 15%–20% data in validation set.**

[For-K-fold-cross-validation-what-k-should-be-selected](https://www.quora.com/For-K-fold-cross-validation-what-k-should-be-selected)

>The choice of k is usually 5 or 10, but there is no formal rule. As k gets larger, the difference in size between the training set and the resampling subsets gets smaller. As this difference decreases, the bias of the technique becomes smaller

[k-fold-cross-validation](https://machinelearningmastery.com/k-fold-cross-validation/)
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTA0ODkwNjA2NywxMjA0MzIyOTE0LC03Mz
I5ODU5NTJdfQ==
-->