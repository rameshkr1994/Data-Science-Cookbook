


> Written with [StackEdit](https://stackedit.io/).

# Scikit-Learn cheat-sheet




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

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg4MjcyNzg5NSwxNTY0ODkzODYyXX0=
-->