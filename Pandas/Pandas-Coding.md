> Written with [StackEdit](https://stackedit.io/).

### How to count the number of missing values in each row in Pandas dataframe?

Import modules:

```python
# Import modules
import pandas as pd
import numpy as np
```


```python
# Create a dataframe
raw_data = {'first_name': ['Jason', 'Molly', np.nan, np.nan, np.nan], 
        'nationality': ['USA', 'USA', np.nan, 'UK', np.nan], 
        'age': [42, 52, 36, 24, np.nan]}
df = pd.DataFrame(raw_data, columns = ['first_name', 'nationality', 'age'])
print(df)
```

      first_name nationality   age
    0      Jason         USA  42.0
    1      Molly         USA  52.0
    2        NaN         NaN  36.0
    3        NaN          UK  24.0
    4        NaN         NaN   NaN
    

Using `.isnull` and `.sum` opperations we can create a new variable called `full_count` counting the number of missing values per row:


```python
df['full_count']  = df.isnull().sum(axis=1)
print(df)
```

      first_name nationality   age  full_count
    0      Jason         USA  42.0           0
    1      Molly         USA  52.0           0
    2        NaN         NaN  36.0           2
    3        NaN          UK  24.0           1
    4        NaN         NaN   NaN           3
    

Now you can take a look to those few rows with missing values using:


```python
df[df['full_count'] > 0]
print(df)
```

      first_name nationality   age  full_count
    0      Jason         USA  42.0           0
    1      Molly         USA  52.0           0
    2        NaN         NaN  36.0           2
    3        NaN          UK  24.0           1
    4        NaN         NaN   NaN           3
    

When using pandas, try to avoid performing operations in a loop, including `apply`, `map`, `applymap` etc. That's slow!

If you want to count the missing values in each column, try:

```python
df.isnull().sum() or df.isnull().sum(axis=0)
```
On the other hand, you can count in each row (which is your question) by:
```python
df.isnull().sum(axis=1)
```
It's roughly 10 times faster than Jan van der Vegt's solution(BTW he counts valid values, rather than missing values):
```python
In [18]: %timeit -n 1000 df.apply(lambda x: x.count(), axis=1)
1000 loops, best of 3: 3.31 ms per loop

In [19]: %timeit -n 1000 df.isnull().sum(axis=1)
1000 loops, best of 3: 329 µs per loop
```

References:

- [How to count the number of missing values in each row in Pandas dataframe?](https://datascience.stackexchange.com/questions/12645/how-to-count-the-number-of-missing-values-in-each-row-in-pandas-dataframe)


```python

```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ0Nzg5MTM5NCwxMTkyOTkyMTg3LC00OD
AyMDQwMTEsLTEyODM0MDk4NjUsLTEyNTQ4OTE1MDRdfQ==
-->