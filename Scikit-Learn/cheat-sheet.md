


> Written with [StackEdit](https://stackedit.io/).

# Scikit-Learn cheat-sheet


### Dimensional Reduction: Feature Agglomeration 
Our dataset contains 58 features. I created 5 clusters (of features) .

First we need to standardize the features beforehand (for example using `sklearn`'s scaler). Otherwise you are rather grouping the scales of the quantities than clustering similar behavior.
```python
from sklearn import cluster

agglo = cluster.FeatureAgglomeration(n_clusters=5)
agglo.fit(X_train)
```
Output:
```
FeatureAgglomeration(affinity='euclidean', compute_full_tree='auto',
           connectivity=None, linkage='ward', memory=None, n_clusters=5,
           pooling_func=<function mean at 0x0000000004E3FB70>)

```
```python
df_reduced = agglo.transform(X_train)

agglo.labels_
```
Output:
```
array([2, 4, 2, 0, 2, 4, 4, 0, 2, 2, 0, 2, 4, 4, 2, 4, 1, 2, 2, 4, 4, 1,
       3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3,
       3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3, 3], dtype=int64)

```
 After fitting the cluster, `agglo.labels_` contains a list that tells in which cluster in the reduced dataset each feature in the original dataset belongs. So now, I can chose the most predictable variable from each of those 5 clusters and see if they models improves.

#### References

- [Feature agglomeration: How to retrieve the features that make up the clusters?](https://stackoverflow.com/questions/47909588/feature-agglomeration-how-to-retrieve-the-features-that-make-up-the-clusters)
- [How to use Python's feature agglomeration for dimensionality reduction?](https://stackoverflow.com/questions/45625218/how-to-use-pythons-feature-agglomeration-for-dimensionality-reduction)
- [Feature agglomeration: Is it testing interactions?](https://datascience.stackexchange.com/questions/25907/feature-agglomeration-is-it-testing-interactions)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ3MTY3NTYwOCwtMTgxOTg1NDY1NiwtMT
U3NDgxNTg1MywxOTM5NTQzNTMyLDE1NjQ4OTM4NjJdfQ==
-->