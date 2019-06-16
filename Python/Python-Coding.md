


> Written with [StackEdit](https://stackedit.io/).


In Python, create a new object is often better than modify an existing one:

```python
item_list = ['item', 5, 'foo', 3.14, True]
item_list = [e for e in item_list if e not in ('item', 5)]
```

Which is equivalent to:

```python
item_list = ['item', 5, 'foo', 3.14, True]
new_list = []
for e in item_list:
    if e not in ('item', 5):
        new_list.append(e)
item_list = new_list
```
In case of a big list of filtered out values (here,  `('item', 5)`  is a small set of element), use a  `set`  can lead to performance improvement, as the  `in`  operation is in O(1) :

```python
item_list = [e for e in item_list if e not in {'item', 5}]
```

Note that, as explained in comments and suggested  [here](https://gist.github.com/Aluriak/01c3d100cb44ef048c00854c6f439642), the following could save even more time, avoiding the set to be built at each loop:

```python
unwanted = {'item', 5}
item_list = [e for e in item_list if e not in unwanted]
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjQ2NTg0MDMzXX0=
-->