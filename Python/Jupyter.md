


> Written with [StackEdit](https://stackedit.io/).
# Jupyter Notebook

### Cheat Sheet

From `.py` to `.ipynb`:
```bash
$ p2j train.py
```
From `.ipython` to `.html` or any other format.:
```bash
$ jupyter nbconvert --to FORMAT notebook.ipynb
```
It is possible to execute `.ipynb` and create the .`html` file without open Jupyter Lab using the  `--execute` option:

```
$ jupyter nbconvert --e notebook.ipynb
```


### How to convert a `.py` script  into a Jupyter Notebook file `.ipynb`

You can use the following Python package: 

[p2j 1.2.1](https://pypi.org/project/p2j/)

Usage:

`$ p2j train.py`

Example of a python script ready for conversion:

- `#####` will be `###`
- Use always and space just below `#####` 

```python
"""
**PROJECT NAME** : Agent-Screening
**CODE NAME**: Target.py
**AUTHOR**: Marcos Keyser
**AIM**: Create all target for Phase II models. Target 1 and Target 2.
**INPUT DATA**:

`target/data/rolling12month_target.csv` -- Rolling 12 months target target 1
`target/data/Manpower2018.csv` -- End of the Year 2018 target target 1
`target/data/age_council.csv` -- Council data to build target 2

**OUTPUT DATA**: target master table with 4 different target definiton

`target/data_output/target_master.csv`
"""

##### Import modules

# checking and changing working directory

import os
cwd = os.getcwd()
cwd

# Changing working directory to current project's directory
os.chdir('C:\\Users\\t93kqi0\\Documents\\Projects\\Agent-Screening')
cwd = os.getcwd()
cwd

# Import modules
import pandas as pd
import numpy as np
# for plotting
import matplotlib.pyplot as plt
# for read Excel files
from pandas import ExcelWriter
from pandas import ExcelFile
# for warnings
import warnings
warnings.filterwarnings('ignore')
# Pandas by default display 60 rows. You can override this:
pd.set_option('display.max_rows', 1000)
#pd.set_option('display.max_rows', 500)
pd.set_option('display.max_columns', 80)
pd.set_option('display.width', 1500)

##### Let's go ahead and load the dataset

targetRoll = pd.read_csv('target/data/rolling12month_target.csv')
targetEoy = pd.read_csv('target/data/Manpower2018.csv')
council = pd.read_csv('target/data/age_council.csv')

print(targetRoll.shape)
print(targetEoy.shape)
print(council.shape)

##### targetRoll

# We are going to use targetRoll (Rolling 12 months) `marketer_id for` the whole analysis: 1378

targetRoll.head()

# Let's select the variables we need to build target 1 and target 2 for rolling
# 12 months verson of the target

targetRoll = targetRoll[['marketer_id', 'proactive']]

# Let's now join target 1 variables:
targetRoll.head()

##### targetEoy

# Let's select the variables we need to build target 1 and target 2 for end of
# 2018 verson of the target

targetEoy = targetEoy[['MKTRNUM', 'PROACTIVE IND']]

# Rename the target variables as `PROACTIVE_IND`
targetEoy = targetEoy.rename(index=str, columns={"PROACTIVE IND": "PROACTIVE_IND"})
targetEoy.head()

# transform tartet into a numberic varible 1 - 0:
targetEoy['PROACTIVE_IND'] = np.where(targetEoy['PROACTIVE_IND'] == "Y", 1, 0)

targetEoy.head()

##### Joining targetRoll & targetRoll

# Now we can join target1 information to target2

targetAll = targetRoll.merge(targetEoy, how='left', left_on = 'marketer_id',
                        right_on = 'MKTRNUM')

targetAll.shape

# As expected we get 1378 observations for targetAll

targetAll.head()

targetAll['proactive'].isnull().sum()

targetAll['PROACTIVE_IND'].isnull().sum()

# There are 30 NaN values on `PROACTIVE_IND` varible (targetEoy).
# List of missing marketer_id for `PROACTIVE_IND`:

targetEoyMiss = targetAll[targetAll['PROACTIVE_IND'].isnull()]

targetEoyMiss

##### council data prep

# Let's join now council data to create the different target variables (4):

targetAll.head()

council.head()

council.shape

# Let's remove Unnamed: 0 varible
council.drop(council.columns[council.columns.str.contains('unnamed', case=False)],
          axis=1, inplace=True)

council.head()

# We need to select only those rows with cncl_year_dt = 2018. There are
# duplicated records for each and every marketer_id otherwise.
# If we take only == 2018 there are 125 missing observations for council.
# Therefore, I am going to take the last year information instead. At least
# for the moment.

council.head(100)

# Remove duplicates by column marketer_id, keeping the row with the highest value in column cncl_year_dt
# Referencer: https://stackoverflow.com/questions/12497402/python-pandas-remove-duplicates-by-columns-a-keeping-the-row-with-the-highest

councilHighest = council.sort_values('cncl_year_dt', ascending=False).drop_duplicates('marketer_id').sort_index()

councilHighest

councilSel = council[council['cncl_year_dt'] == 2018]

councilSel.shape

councilSel.head()

# Let's check if there are stil duplicates for the mariable `marketer_id`
councilDup = councilSel[councilSel.duplicated('marketer_id')]

councilDup.head()

# There are no more duplicated. Now we can join with the target.

# Let's select the variables we need to build up Target 2
councilSel = councilSel[['marketer_id','cncl_year_dt', 'cncl_cd']]

councilSel.shape

# Let's use `councilHighest` instead for the moment:

councilHighest  = councilHighest[['marketer_id','cncl_year_dt', 'cncl_cd']]

councilHighestDup = councilHighest[councilHighest.duplicated('marketer_id')]

councilHighestDup

# There a no duplicates as expected

##### Joining council & targetAll

targetAll.shape

#  Joining targetAll (1378 obs.) to council data

targetAllCoun = targetAll.merge(councilHighest, how='left', left_on = 'marketer_id',
                        right_on = 'marketer_id')

targetAllCoun.shape

targetAllCoun.head()

# Let's check there are no missing values on `cncl_year_dt` ( in `cnl_cd` there are
# missing values by variable definition.

targetAllCoun['cncl_year_dt'].isnull().sum()

# There are 125 NaN values on `PROACTIVE_IND` varible (`cncl_year_dt`).
# With this new approach we we 85 missing obs instead 125.
# List of missing `marketer_id` for `cncl_year_dt`:

targetAllCouMiss = targetAllCoun[targetAllCoun['cncl_year_dt'].isnull()]

targetAllCouMiss

##### Target calculation

targetAllCoun.head()

targetAllCoun.shape

targetAllCoun.dtypes

# Rename proactive variables as `target1Rolling`
targetAux01 = targetAllCoun.rename(index=str, columns={"proactive": "target1Rolling"})

# Rename `PROACTIVE_IND` variables as `target1Eoy`
targetAux02 = targetAux01.rename(index=str, columns={"PROACTIVE_IND": "target1Eoy"})

targetAux02.head()

# To calculate target2 variables (Eof and Rolling) we need to do first:
# We need to replace the NaN value in the cncl_cd variable by blanck, otherwise
# Python get confused. NaN values in Python are only for numeric types.
targetAux02['cncl_cd'] =  targetAux02.cncl_cd.fillna('')

targetAux02.head()

# Target 2 Rolling 12 months creation:

def target2Def(df):
    if df['target1Rolling'] == 0:
        return 'Low'
    elif (df['target1Rolling'] == 1 and df['cncl_cd'] == 'QC') or (df['target1Rolling'] == 1 and df['cncl_cd'] == ""):
        return 'Medium'
    else:
        return 'High'

targetAux02['target2Rolling'] = targetAux02.apply(target2Def, axis=1)

targetAux02.shape

targetAux02.head()

# Target 2 End of the year 2018 (Eoy) creation:

def target2EoyDef(df):
    if df['target1Eoy'] == 0:
        return 'Low'
    elif (df['target1Eoy'] == 1 and df['cncl_cd'] == 'QC') or (df['target1Eoy'] == 1 and df['cncl_cd'] == ""):
        return 'Medium'
    else:
        return 'High'

targetAux02['target2Eoy'] = targetAux02.apply(target2EoyDef, axis=1)

targetAux02.shape

targetAux02.head()

##### Save master DataFrame

# Let's save the target master DataFrame as CSV file
targetAux02.to_csv('target/data_output/target_master.csv', index=False)

``` 

### Convert `.ipynb` into `.html` or other formats a command line tool

Using:

[nbconvert](https://nbconvert.readthedocs.io/en/latest/usage.html)

```bash
$ jupyter nbconvert --to FORMAT notebook.ipynb
```

Maybe you need to install first:

```
$ pip install jupyter-contrib-nbextensions
```
and then:
```
$ pip install nbconvert
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwMjI3MTkzMzksLTIwOTA5NjA5MTEsLT
EzOTI3MTIyNzUsLTEyODc3NDg2MDMsMTk2MDM3NTI5Nyw4NzU3
ODc5NTRdfQ==
-->