


> Written with [StackEdit](https://stackedit.io/).


### [How to calculate mean values grouped on another column in Pandas](https://stackoverflow.com/questions/30482071/how-to-calculate-mean-values-grouped-on-another-column-in-pandas)

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

### Replace all spaces in column names with underscores

```python
df.columns = df.columns.str.strip().str.replace(' ', '_')
```

### [How to split data into 3 sets (train, validation and test)?](https://stackoverflow.com/questions/38250710/how-to-split-data-into-3-sets-train-validation-and-test)

The following function was written to handle seeding of randomized set creation. You should not rely on set splitting that doesn't randomize the sets.

```python
import numpy as np
import pandas as pd

def train_validate_test_split(df, train_percent=.6, validate_percent=.2, seed=None):
    np.random.seed(seed)
    perm = np.random.permutation(df.index)
    m = len(df.index)
    train_end = int(train_percent * m)
    validate_end = int(validate_percent * m) + train_end
    train = df.ix[perm[:train_end]]
    validate = df.ix[perm[train_end:validate_end]]
    test = df.ix[perm[validate_end:]]
    return train, validate, test
```

Demonstration

```python
np.random.seed([3,1415])
df = pd.DataFrame(np.random.rand(10, 5), columns=list('ABCDE'))
df

train, validate, test = train_validate_test_split(df)

train

validate

test
```

### [Get list from pandas dataframe column](https://stackoverflow.com/questions/22341271/get-list-from-pandas-dataframe-column)

Pandas DataFrame columns are Pandas Series when you pull them out, which you can then call  `x.tolist()`  on to turn them into a Python list. Alternatively you cast it with  `list(x)`.

```python
import pandas as pd

d = {'one' : pd.Series([1., 2., 3.],     index=['a', 'b', 'c']),
    'two' : pd.Series([1., 2., 3., 4.], index=['a', 'b', 'c', 'd'])}

df = pd.DataFrame(d)

print("Starting with this dataframe\n", df)

print("The first column is a", type(df['one']), "\nconsisting of\n", df['one'])

dfToList = df['one'].tolist()

dfList = list(df['one'])

dfValues = df['one'].values

print("dfToList is", dfToList, "and it's a", type(dfToList))
print("dfList is  ", dfList,   "and it's a", type(dfList))
print("dfValues is", dfValues, "and it's a", type(dfValues))
```

The last lines return:

```python
dfToList is [1.0, 2.0, 3.0, nan] and it's a <class 'list'>
dfList is   [1.0, 2.0, 3.0, nan] and it's a <class 'list'>
dfValues is [ 1.  2.  3. nan] and it's a <class 'numpy.ndarray'>
```

[This question](https://stackoverflow.com/questions/14822680/convert-python-dataframe-to-list)  might be helpful. And the  [Pandas docs](http://pandas.pydata.org/pandas-docs/stable/dsintro.html)  are actually quite good once you get your head around their style.

So in your case you could:
```python
my_list = df["cluster"].tolist()
```
and then go from there.

### Append at the beginning of the list

```python
a = 5
li = [1, 2, 3]
[a] + li  # Don't use 'list' as variable name.
```
output 
```
[5, 1, 2, 3]
```

### Append at the end of the list
```python
a = 5
li = [1, 2, 3]
li.append(a)  # Don't use 'list' as variable name.
```
output 
```
[1, 2, 3, 5]
```

### Export a correlation matrix to a .CSV file

```python
def corr_matrix(file_name):
    df = pd.read_csv('master_train_test/train_' + file_name + '.csv')
    corr = df.corr()
    corr.to_csv('model_output/corr_' + file_name + '.csv')

corr_matrix('K')
corr_matrix('KC')
corr_matrix('KCP')
```

### [Pythonic way to print list items](https://stackoverflow.com/questions/15769246/pythonic-way-to-print-list-items)

How to print the whole content of a super long list:

Assuming you are using Python 3.x:

```Python
print(*myList, sep='\n')
```

### Fill `NaN` values in a columns with the value of another column

```python
# Replace NaN values in Variable Definition by Feature values

matching3['Variable_Definition'] = matching3['Variable_Definition'].fillna(matching3['Feature'])
```

### Replace  underscore by space in pandas dataframe

```python
matching3['Variable_Definition'] = matching3['Variable_Definition'].replace(regex=['_'], value=' ')
```
[more](http://www.datasciencemadesimple.com/replace-a-substring-of-a-column-in-pandas-python/) 

### [Set order of columns in pandas dataframe](https://stackoverflow.com/questions/41968732/set-order-of-columns-in-pandas-dataframe)

Just select the order yourself by typing in the column names. Note the double brackets:

```python
frame = frame[['column I want first', 'column I want second'...etc.]]
```

### [how would you make a comma separated string from a list of strings](https://stackoverflow.com/questions/44778/how-would-you-make-a-comma-separated-string-from-a-list-of-strings)

```python
myList = ['a','b','c','d']
myString = ",".join(myList )
```

This won't work if the list contains numbers.

As  [Ricardo Reyes](https://stackoverflow.com/users/3399/ricardo-reyes)  suggested, if it contains non-string types (such as integers, floats, bools, None) then do:

```python
myString = ','.join(map(str, myList)) 
```

### Add a header to a pandas series

Using `names  = ['marketer_id']` we can add a header to a pandas series 

```python
train_targetMaster = pd.read_csv('target/data_output/train_targetMaster.csv', names = ['marketer_id'])
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDcxMTQ0MDEwLC04MTEzNTA3LDY0NTU4Mj
MwNSwtMzg3NDQyNzAzLC0yNDI4NjA5OTYsLTY4MjY4OTk4Nywt
MTM3MTQ1NTEwLDE3MzQ2MDcxMjAsNzgyNTE1MjIwLDEwMTY3Mz
cwMDcsLTIxMTYyOTUyNzcsLTQxMzQwNTkzNl19
-->