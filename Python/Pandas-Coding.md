> Written with [StackEdit](https://stackedit.io/).

## Popular Data Management Operation using Pandas

### Table of contents
- [Import modules]()
- [Pandas version]()
- [Return the `dtypes` in the `DataFrame`]()
- [Force `dtypes` in pandas `read_csv`]()
- [Combine two columns of text in `dataframe` in pandas]()
- [How to count the number of missing values in each row in Pandas dataframe?](https://github.com/markeyser/Data-Science-Cookbook/blob/master/Pandas/Pandas-Coding.md#how-to-count-the-number-of-missing-values-in-each-row-in-pandas-dataframe)
- [Replace `NaN` values with average of columns](https://github.com/markeyser/Data-Science-Cookbook/blob/master/Pandas/Pandas-Coding.md#replace-nan-values-with-average-of-columns)
- [Replace `NaN` values with average of rows](https://github.com/markeyser/Data-Science-Cookbook/blob/master/Pandas/Pandas-Coding.md#replace-nan-values-with-average-of-rows)
- [Read and Write a `CSV` file]()
- [Merge and Join DataFrames]()

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

### Checking and changing working directory

```python
# checking and changing working directory
import os
cwd = os.getcwd()
cwd
# Changing working directory to current project's directory
os.chdir('C:\\Users\\t93kqi0\\Documents\\Projects\\TriggerAnalysis\\python_code')
cwd = os.getcwd()
cwd
```

### Import modules
```python
# Import modules
import pandas as pd
import numpy as np
import warnings
warnings.filterwarnings('ignore')
```
### Pandas override default 60 lines display

```python
# Pandas by default display 60 rows. You can override this:
pd.set_option('display.max_rows', 120)
```

refern

### Pandas version
```python
# pandas version
pd.__version__
```
Output
```
'0.23.4'
```
### Return the `dtypes` in the `DataFrame`

```python
dataframe.dtypes
```
output:
```bash
LAUS_Code                          object
Stete_FIPS_Code                    object
Country_FIPS_Code                  object
County_Name_State_Abbreviation     object
Year                               object
Labor_Force                         int64
Employed                            int64
Unemployed                          int64
Unemployment_Rate_Percentage      float64
```

### Force `dtypes` in pandas `read_csv`
 
```python
# Force to import the following variables as string instead as number
dtypes = {'Stete_FIPS_Code': 'str', 'Year': 'float'}
unemployment = pd.read_csv("../data/unemployment.csv", dtype=dtypes )
```

### Combine two columns of text in `dataframe` in pandas
The new variable `FIPS_CD` concatenates the content of the variables  `Stete_FIPS_Code` and  `Country_FIPS_Code`:
```python
df["FIPS_CD"] = df["Stete_FIPS_Code"] + df["Country_FIPS_Code"]
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

### Read and Write a `CSV` file 

To read use:

```python
aux01 = pd.read_csv("../data/Retention_History_GO_2007_2018_v02.csv") 
```
To write use:
```python
ret_cc.to_csv('../output_data/ret_cc.csv', index=False)
```
-   `index`: whether to write row (index) names (default True)

Output:
```
YEAR,GOCODE,ZONE,GO,GROUP,RETENTION,ID,TRIGGER
2007,V48,NE,ALBANY,CC,0.6920000000000001,0,TRG_00500
2007,V56,NE,BOSTON,CC,0.9470000000000001,1,TRG_00500
2007,V79,NE,BROOKLYN,CC,0.9470000000000001,2,TRG_00500
2007,V79,NE,BROOKLYN,CC,0.9470000000000001,3,TRG_00500
```

[Reference](http://pandas.pydata.org/pandas-docs/stable/user_guide/io.html#io-read-csv-table)

### Merge and Join DataFrames

![](https://shanelynnwebsite-mid9n9g1q9y8tt.netdna-ssl.com/wp-content/uploads/2017/03/pandas-merge-join-different-variable-names-copy-e1488722312527.png)
[source](https://shanelynnwebsite-mid9n9g1q9y8tt.netdna-ssl.com/wp-content/uploads/2017/03/pandas-merge-join-different-variable-names-copy-e1488722312527.png)

```python
result = pd.merge(result,
				  devices[['manufacturer'. 'model']],
				  left_on = 'device',
				  right_on = 'model',
				  how = 'left')
```
It is important to note that the join key variables must be part of the selected variables. For example:
```python
result = pd.merge(ret_cc, aapr[['YEAR', 'GOCODE', 'AAPR']],
                  left_on  = ['GOCODE', 'YEAR'],
				  right_on = ['GOCODE', 'YEAR'],
				  how = 'left')
```
`YEAR` and `GOCODE` must be part of `aapr[['YEAR', 'GOCODE', 'AAPR']]` even when I only want to select `AAPR` from the `aapr` dataset. 

Another way to perform a left join:

```python
matching = rolling12month_target.merge(acxiom_subset, how='left', 
                                                      left_on = 'marketer_id', 
                                                      right_on = 'SRC_HHLD_ID')
```


### Join multiple files using Lambda expression
Let's say we want to join multiple files. We could use a lambda expression. 
```python
# Import reduce from functools:
from functools import reduce
# Read all tables from a csv file:
gender_2007 = pd.read_csv("../output_data/gender_2007.csv", usecols = ['GOCODE', 'gender_F_PER_2007'])
gender_2008 = pd.read_csv("../output_data/gender_2008.csv", usecols = ['GOCODE', 'gender_F_PER_2008'])
gender_2009 = pd.read_csv("../output_data/gender_2009.csv", usecols = ['GOCODE', 'gender_F_PER_2009'])
gender_2010 = pd.read_csv("../output_data/gender_2010.csv", usecols = ['GOCODE', 'gender_F_PER_2010'])
gender_2011 = pd.read_csv("../output_data/gender_2011.csv", usecols = ['GOCODE', 'gender_F_PER_2011'])
gender_2012 = pd.read_csv("../output_data/gender_2012.csv", usecols = ['GOCODE', 'gender_F_PER_2012'])
gender_2013 = pd.read_csv("../output_data/gender_2013.csv", usecols = ['GOCODE', 'gender_F_PER_2013'])
gender_2014 = pd.read_csv("../output_data/gender_2014.csv", usecols = ['GOCODE', 'gender_F_PER_2014'])
gender_2015 = pd.read_csv("../output_data/gender_2015.csv", usecols = ['GOCODE', 'gender_F_PER_2015'])
gender_2016 = pd.read_csv("../output_data/gender_2016.csv", usecols = ['GOCODE', 'gender_F_PER_2016'])
gender_2017 = pd.read_csv("../output_data/gender_2017.csv", usecols = ['GOCODE', 'gender_F_PER_2017'])
gender_2018 = pd.read_csv("../output_data/gender_2018.csv", usecols = ['GOCODE', 'gender_F_PER_2018'])
# Create a list of all dataframe names
dfs = [gender_2007, gender_2008, gender_2009, gender_2010, gender_2011, gender_2012, gender_2013, gender_2014, gender_2015, gender_2016, gender_2017, gender_2018]
# Let's performe an outer join to get all different GO offices
df_final = reduce(lambda left,right: pd.merge(left,right, on='GOCODE', how='outer'), dfs)
```


###  Strip Leading and Trailing Space of a column
```python
# Strip Leading and Trailing Space of the GO_CD before join
unemployment['GO_CD'] = unemployment['GO_CD'].str.strip()
```
### Drop one or more columns
```python
# GO_CD and YEAR are not necesary
result6 = result5.drop(columns = ['GO_CD','YEAR'])
```
### Rename some variables
```python
result9 = result8.rename(index=str, columns={"Rural_Urban": "RURAL_URBAN"})
```
### Using the `interpolate` method to impute those few missing obs.
This method is going to use the `interpolate` method to impute missing values in each and every continuous variable.
```python
result10 = result9.interpolate()
```
### Read an Excel file using Pandas

To read an Excel spreadsheet using Pandas:

```python
import pandas as pd
from pandas import ExcelWriter
from pandas import ExcelFile

agents07 = pd.read_excel("../data/2007_2018_Contracted_Agents_by_Year.xlsx", sheet_name='2007')
```
[Reference](https://pythonspot.com/read-excel-with-pandas/)

How to retrieve specific columns from and specific sheet:

```python
# Read Excel file first sheet
file_loc = "../data/2007_2018_Contracted_Agents_by_Year.xlsx"

agents07 = pd.read_excel( file_loc , index_col=None, sheet_name='2007', usecols = "A, C, F, G" )
```
We can assign the position of the column in excel  using `usecols` option. 

[Reference](https://stackoverflow.com/questions/33655127/how-to-read-certain-columns-from-excel-using-pandas-python)

### Check Python Working Directory and Change WD
To check and change current Python working directory:
```python
import os

# Checking current working directory
cwd = os.getcwd()
cwd

# Changing current working directory to the following one
os.chdir('C:\\Users\\t93kqi0\\Documents\\Projects\\TriggerAnalysis\\python_code')

# Checking current working directory
cwd = os.getcwd()
cwd
```
### Import CSV - Ignore the second header
Using the option `header` we can choose the from what line we want to start reading the file. In this case we have two headers. I just want to keep the first one. Therefore, I can use the option `skiprows=[1]` in combination with `header = 0` to keep just the first header.  
 
```python
# Uisnt skiprows=[1] we can skip the second header that is not useful at all
# reference: https://bit.ly/2PeNXhE
ACS_17 = pd.read_csv("../data/ACS_17_1YR_S0201_with_ann.csv", header = 0, skiprows=[1])
```
Reference: [Ignore second header line](https://stackoverflow.com/questions/36066575/pandas-read-csv-ignore-second-header-line)

### Creating new pandas `DataFrames` in a loop / function

In this example we have 4 Excel spreadsheets with 12 sheets each. We need to read each sheet within each Excel spreadsheet, create a new variable for each of the 12 years and, concatenate each of those 12 tables. The final output are 4 new pandas DataFrames. 

```python
# Import libraries
import pandas as pd
from pandas import ExcelWriter
from pandas import ExcelFile
import numpy as np

years_all = ['2007', '2008', '2009', '2010', '2011', '2012', '2013', '2014',
             '2015', '2016', '2017', '2018']

def licExt(group, abc):
    abc = pd.DataFrame() # to clear abc after every group iteration (4)
    year = years_all
    appended_data = [] # to create a list of 12 DataFrames
    for years in year:
        w = pd.DataFrame() 
        file_name = "../data/2007-2018-license-by-GO-Proactive-"
        w = pd.read_excel(file_name + group + '.xlsx', sheet_name=years)
        # Let's create a variable for the year named YEAR
        w['YEAR'] = years
        # Let's append all above dataframes in the list appended_data
        appended_data.append(w)

    abc = pd.concat(appended_data, ignore_index=True)
    return abc

license_cc = licExt('CC', license_cc)
license_1p = licExt('1P', license_1p)
license_2p = licExt('2P', license_2p)
license_3p = licExt('3P', license_3p)
```
### Saving multiple pandas `DataFrames`
This is a similar example as the above one. 
```python
# Let's save the DataFrame into a .csv file
def licSave(group, abc):
    abc.to_csv('../output_data/license_' + group + '.csv', index=False)

licSave('cc', license_cc)
licSave('1p', license_1p)
licSave('2p', license_2p)
licSave('3p', license_3p)
```
### Add an empty column 'NaN' to a `dataFrame`:
Let's add a new column, `FYC_2007` with null values `NaN`:
```python
import pandas as pd
import numpy as np

aux01["FYC_2007"] = np.nan
```
### Sort pandas `dataFrame` by column 

In ascending order:
```python
# sort Brand - ascending order
df.sort_values(by=['Brand'], inplace=True)
```
In descending order:
```python
# sort Brand - descending order
df.sort_values(by=['Brand'], inplace=True, ascending=False)
```
Sort by multiple columns:
```python
df.sort_values(by=['Year','Price'], inplace=True)
```
### Use pandas to lag your time series data in order to examine causal relationships
How to create a lag in your pandas `dataFrame`:
```python
# Sort the data by ID and YEAR first
total_avg_fyc.sort_values(by=['ID', 'YEAR'], inplace=True)
# Let's to create the PRIOR_CAPITAL variable using the shift function to create a lag
total_avg_fyc['PRIOR_CAPITAL'] = total_avg_fyc['CAPITAL'].shift(1)
```
You can create two-years lag, etc.
[Reference](https://medium.com/@NatalieOlivo/use-pandas-to-lag-your-timeseries-data-in-order-to-examine-causal-relationships-f8186451b3a9)

### Reading a fixed width text file
Let's say we have the following data file:


References:

- [pandas.read_fwf](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_fwf.html)
- [pandas.read_fwf examples](https://www.programcreek.com/python/example/101362/pandas.read_fwf)
- [python code style for long lists](https://softwareengineering.stackexchange.com/questions/286318/python-code-style-for-long-lists)
- [working with huge lists in python](https://stackoverflow.com/questions/15283893/working-with-huge-lists-in-python)


### Add column with constant value to pandas dataframe

For in-place modification, perform direct assignment. This assignment is broadcasted by pandas for each row.

```python
df = pd.DataFrame('x', index=range(4), columns=list('ABC'))
df
```

```
   A  B  C
0  x  x  x
1  x  x  x
2  x  x  x
3  x  x  x
```
```python
df['new'] = 'y'
# Same as,
# df.loc[:, 'new'] = 'y'
df
```
```
   A  B  C new
0  x  x  x   y
1  x  x  x   y
2  x  x  x   y
3  x  x  x   y
```
If you need a copy instead, use [`DataFrame.assign`](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.assign.html):

```python
df.assign(new='y')
```
```
   A  B  C new
0  x  x  x   y
1  x  x  x   y
2  x  x  x   y
3  x  x  x   y
```
And, if you need to assign multiple such columns with the same value, this is as simple as,

```python
c = ['new1', 'new2', ...]
df.assign(**dict.fromkeys(c, 'y'))
```
```
   A  B  C new1 new2
0  x  x  x    y    y
1  x  x  x    y    y
2  x  x  x    y    y
3  x  x  x    y    y
```
Finally, if you need to assign multiple columns with different values, you can use `assign` with a dictionary.

```python
c = {'new1': 'w', 'new2': 'y', 'new3': 'z'}
df.assign(**c)
```

```
   A  B  C new1 new2 new3
0  x  x  x    w    y    z
1  x  x  x    w    y    z
2  x  x  x    w    y    z
3  x  x  x    w    y    z
```
Reference: [add-column-with-constant-value-to-pandas-dataframe](https://stackoverflow.com/questions/24039023/add-column-with-constant-value-to-pandas-dataframe)

###  How to check if a column/s exists in Pandas?

```python
import pandas as pd
 
df = pd.DataFrame([[10, 20, 30, 40], [7, 14, 21, 28], [55, 15, 8, 12]],
                  columns=['Apple', 'Orange', 'Banana', 'Pear'],
                  index=['Basket1', 'Basket2', 'Basket3'])
 
if 'Apple' in df.columns:
    print("Yes")
else:
    print("No")
 
 
if set(['Apple','Orange']).issubset(df.columns):
    print("Yes")
else:
    print("No")
```

Another approach:

```python
# Another approach, we can use a for loop like this

test = []

for column in vars:
    if column in Acxiom.columns:
        test.append('Yes')
    else:
        test.append('NO')

print(test)
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzY3NjY0NjEyLDI1NzU3NTI2LDgwMDIzMD
g5NiwxNzQ2Nzc4MzI2LDQ2ODEyMjM0OCwtMjExODIxMDMwMywt
MTE3NTQzMjQ2LC02NTMzNjIwMTYsLTE4ODM1NzI0OTEsMTE5NT
Y5MTUzNSwtNTYwMjc3MzcsLTEyNTY4MTE4MTksLTk4MDYxMDc2
Miw1NzM4Mjg1OTgsMTAxMTg5NjUwNCwxNDcwNjM0Mzc0LC0xMz
Q0MDQzMTMzLC0xNjYwODM5NjA1LC0xMzUzMzM1MTI4LDY2MTIz
NjM0XX0=
-->