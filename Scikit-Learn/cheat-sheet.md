


> Written with [StackEdit](https://stackedit.io/).

# Scikit-Learn cheat-sheet

### How to set the global random_state in Scikit Learn

Such information should be in the first paragraph of Scikit Learn manual, but it is hidden somewhere in the FAQ, so let’s write about it here.

Scikit Learn does not have its own global random state but uses the numpy random state instead. If you want to have reproducible results in Jupyter Notebook (you should want that ;) ), set the seed at the beginning of your notebook:

```python
np.random.seed(31415)
```
[Reference](https://www.mikulskibartosz.name/how-to-set-the-global-random_state-in-scikit-learn/)

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

### How to Create Pandas Dataframe from Multiple Lists?

The output of `scikit-learn` consists into lists, so to make reports we need to put all those lists into a pandas dataframe and then save as csv. So, creating pandas dataframes from multiple lists is essential:

Let us say we have two lists, one of them is of string type and the other is of type int. We want to make a dataframe with these lists as columns.

```python
months = [ 'Jan', 'Apr', 'Mar', 'June']

days = [ 31, 30, 31, 30]
```

Refernces:

- [How to create pandas dataframe from multiple lists](https://cmdlinetips.com/2018/01/how-to-create-pandas-dataframe-from-multiple-lists/)
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg1NDA5NjIzNCw0NjEyMTc3NjIsLTQ3MT
Y3NTYwOCwtMTgxOTg1NDY1NiwtMTU3NDgxNTg1MywxOTM5NTQz
NTMyLDE1NjQ4OTM4NjJdfQ==
-->