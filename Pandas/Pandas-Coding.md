> Written with [StackEdit](https://stackedit.io/).


#### [How to count the number of missing values in each row in Pandas dataframe?](https://datascience.stackexchange.com/questions/12645/how-to-count-the-number-of-missing-values-in-each-row-in-pandas-dataframe)



Import modules
```python
# Import modules
import pandas as pd
import numpy as np
```
Create a DataFrame
```python
# Create a dataframe
raw_data = {'first_name': ['Jason', 'Molly', np.nan, np.nan, np.nan], 
        'nationality': ['USA', 'USA', np.nan, 'UK', np.nan], 
        'age': [42, 52, 36, 24, np.nan]}
df = pd.DataFrame(raw_data, columns = ['first_name', 'nationality', 'age'])
df
```
Output:
```markdown
| obs | first_name | nationality | age  |
|-----|------------|-------------|------|
| 0   | Jason      | USA         | 42.0 |
| 1   | Molly      | USA         | 52.0 |
| 2   | NaN        | NaN         | 36.0 |
| 3   | NaN        | UK          | 24.0 |
| 4   | NaN        | NaN         | NaN  |
```



```python

```


```python

```

### How to count the number of missing values in each row in Pandas dataframe?


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
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>first_name</th>
      <th>nationality</th>
      <th>age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Jason</td>
      <td>USA</td>
      <td>42.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Molly</td>
      <td>USA</td>
      <td>52.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>36.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NaN</td>
      <td>UK</td>
      <td>24.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



Using `.isnull` and `.sum` opperations we can create a new variable called `full_count` counting the number of missing values per row:


```python
df['full_count']  = df.isnull().sum(axis=1)
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>first_name</th>
      <th>nationality</th>
      <th>age</th>
      <th>full_count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Jason</td>
      <td>USA</td>
      <td>42.0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Molly</td>
      <td>USA</td>
      <td>52.0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>36.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NaN</td>
      <td>UK</td>
      <td>24.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>



Now you can take a look to those few rows with missing values using:


```python
df[df['full_count'] > 0]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>first_name</th>
      <th>nationality</th>
      <th>age</th>
      <th>full_count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>36.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NaN</td>
      <td>UK</td>
      <td>24.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>



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
eyJoaXN0b3J5IjpbLTE0Mjg5MzQ5NTIsLTQ4MDIwNDAxMSwtMT
I4MzQwOTg2NSwtMTI1NDg5MTUwNF19
-->