> Written with [StackEdit](https://stackedit.io/).

## Popular Data Management Operation using Pandas

### Table of contents

- [How to count the number of missing values in each row in Pandas dataframe?](#heading)
- [Replace `NaN` values with average of columns](#heading-2)

```
# Table of Contents
1. [Example](#example)
2. [Example2](#example2)
3. [Third Example](#third-example)

## Example
## Example2
## Third Example
```



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

### Replace NaN values with average of columns

```python
# Import modules
import pandas as pd
import numpy as np
```
```python
# Create a dataframe
raw_data = {'first_name': ['Jason', 'Molly', np.nan, np.nan, np.nan], 
        'nationality': ['USA', 'USA', 'France', 'UK', 'UK'], 
        'age': [42, 52, 36, 24, np.nan],
        'tenure': [np.nan, 3, np.nan, 15, 8]}
df = pd.DataFrame(raw_data, columns = ['first_name', 'nationality', 'age', 'tenure'])
print(df)
```
      first_name nationality   age  tenure
    0      Jason         USA  42.0     NaN
    1      Molly         USA  52.0     3.0
    2        NaN      France  36.0     NaN
    3        NaN          UK  24.0    15.0
    4        NaN          UK   NaN     8.0
    
The mean value for each and every numberic variable (column) is:

```python
df.mean()
```
    age       38.500000
    tenure     8.666667
    dtype: float64
    
Now we can impute all those missing observations using the mean value per column:

```python
df = df.fillna(df.mean())
print(df.head())
```
      first_name nationality   age     tenure
    0      Jason         USA  42.0   8.666667
    1      Molly         USA  52.0   3.000000
    2        NaN      France  36.0   8.666667
    3        NaN          UK  24.0  15.000000
    4        NaN          UK  38.5   8.000000
    
References:

- [pandas DataFrame: replace nan values with average of columns](https://stackoverflow.com/questions/18689823/pandas-dataframe-replace-nan-values-with-average-of-columns)
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA2ODEyMzY1OSwtODY3MDY2OTMyLC0yOD
g3ODY2ODIsLTc4NzU4MDA4MSwxMTkyOTkyMTg3LC00ODAyMDQw
MTEsLTEyODM0MDk4NjUsLTEyNTQ4OTE1MDRdfQ==
-->