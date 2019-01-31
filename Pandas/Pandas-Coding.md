> Written with [StackEdit](https://stackedit.io/).

## Popular Data Management Operation using Pandas

### Table of contents

- [How to count the number of missing values in each row in Pandas dataframe?](https://github.com/markeyser/Data-Science-Cookbook/blob/master/Pandas/Pandas-Coding.md#how-to-count-the-number-of-missing-values-in-each-row-in-pandas-dataframe)
- [Replace `NaN` values with average of columns](https://github.com/markeyser/Data-Science-Cookbook/blob/master/Pandas/Pandas-Coding.md#replace-nan-values-with-average-of-columns)

```
# Table of Contents
1. [Example](#example)
2. [Example2](#example2)
3. [Third Example](#third-example)

## Example
## Example2
## Third Example
```

- [Tutorial: Manually create a Markdown table of contents for your GitHub README](https://www.setcorrect.com/portfolio/work11/)

### Import modules
```python
# Import modules
import pandas as pd
import numpy as np
```
### Pandas version
```python
# pandas version
pd.__version__
```
Output
```
'0.23.4'
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

### Replace `NaN` values with average of columns

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

### Replace `NaN` values with average of rows

### Replace `NaN` values with average of rows


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
        'tenure': [np.nan, 3, np.nan, 15, 8],
        'salary': [32, 56 , 78, 99, 45]}
df = pd.DataFrame(raw_data, columns = ['first_name', 'nationality', 'age', 'tenure', 'salary'])
print(df)
```
Output:
```
      first_name nationality   age  tenure  salary
    0      Jason         USA  42.0     NaN      32
    1      Molly         USA  52.0     3.0      56
    2        NaN      France  36.0     NaN      78
    3        NaN          UK  24.0    15.0      99
    4        NaN          UK   NaN     8.0      45
```    

The mean value for each and every numeric row is:
```python
test = df.mean(axis=1)
test
```
Output
```
    0    37.0
    1    37.0
    2    57.0
    3    46.0
    4    26.5
    dtype: float64
```
The `axis` argument to `fillna` is not implementet. Therefore, the following approach doesn't work:
```python
df = df.fillna(df.mean(axis=1), axis=1)
df
```
Output:
```
    ---------------------------------------------------------------------------

    NotImplementedError                       Traceback (most recent call last)

    <ipython-input-48-13bc2191f7ff> in <module>
    ----> 1 df = df.fillna(df.mean(axis=1), axis=1)
          2 df
    

    ~\AppData\Local\Continuum\anaconda3\lib\site-packages\pandas\core\frame.py in fillna(self, value, method, axis, inplace, limit, downcast, **kwargs)
       3788                      self).fillna(value=value, method=method, axis=axis,
       3789                                   inplace=inplace, limit=limit,
    -> 3790                                   downcast=downcast, **kwargs)
       3791 
       3792     @Appender(_shared_docs['replace'] % _shared_doc_kwargs)
    

    ~\AppData\Local\Continuum\anaconda3\lib\site-packages\pandas\core\generic.py in fillna(self, value, method, axis, inplace, limit, downcast)
       5410             elif isinstance(value, (dict, ABCSeries)):
       5411                 if axis == 1:
    -> 5412                     raise NotImplementedError('Currently only can fill '
       5413                                               'with dict/Series column '
       5414                                               'by column')
    

    NotImplementedError: Currently only can fill with dict/Series column by column
```
An alternative is to `fillna` then transpose and then transpose:
```python
print(df.T.fillna(df.mean(axis=1)).T)
```
Output:
```
      first_name nationality   age tenure salary
    0      Jason         USA    42     37     32
    1      Molly         USA    52      3     56
    2         57      France    36     57     78
    3         46          UK    24     15     99
    4       26.5          UK  26.5      8     45
 ```   

[Reference](https://stackoverflow.com/questions/33058590/pandas-dataframe-replacing-nan-with-row-average)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIxNDY5MDE0NCw3NDM2NTg2NTAsNzU0Mj
MxNDAzLDI2NTc1OTE4MywtMTk0NzIxODExOSwtMTk4MTU0Nzc0
MywtODY3MDY2OTMyLC0yODg3ODY2ODIsLTc4NzU4MDA4MSwxMT
kyOTkyMTg3LC00ODAyMDQwMTEsLTEyODM0MDk4NjUsLTEyNTQ4
OTE1MDRdfQ==
-->