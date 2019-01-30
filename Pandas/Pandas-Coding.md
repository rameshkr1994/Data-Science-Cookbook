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
 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY3MzQyOTYyNCwtMTI4MzQwOTg2NSwtMT
I1NDg5MTUwNF19
-->