


> Written with [StackEdit](https://stackedit.io/).


# [How to calculate mean values grouped on another column in Pandas](https://stackoverflow.com/questions/30482071/how-to-calculate-mean-values-grouped-on-another-column-in-pandas)

You could  `groupby`  on  `StationID`  and then take  `mean()`  on  `BiasTemp`. To output  `Dataframe`, use  `as_index=False`

```python
In [4]: df.groupby('StationID', as_index=False)['BiasTemp'].mean()
Out[4]:
  StationID  BiasTemp
0        BB       5.0
1     KEOPS       2.5
2    SS0279      15.0
```

Without  `as_index=False`, it returns a  `Series`  instead

```python
In [5]: df.groupby('StationID')['BiasTemp'].mean()
Out[5]:
StationID
BB            5.0
KEOPS         2.5
SS0279       15.0
Name: BiasTemp, dtype: float64
```

Read more about  `groupby`  in this pydata  [tutorial](http://pandas.pydata.org/pandas-docs/stable/groupby.html).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NjgwNjg2NF19
-->