> Written with [StackEdit](https://stackedit.io/).

# Seaborn

Basic guide on Chris Albon site [here](https://chrisalbon.com/python/data_wrangling/pandas_with_seaborn/) 

## Typical `seaborn` setup

```python
# Import libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
%matplotlib inline
```

## To switch to seaborn defaults, simply call the [`set()`](https://seaborn.pydata.org/generated/seaborn.set.html#seaborn.set "seaborn.set") function.

```python
sns.set()
```
[reference](https://seaborn.pydata.org/tutorial/aesthetics.html)

## lineplot
Line plot with title:
```python
SanDiego = sns.lineplot(x="YEAR", y="RETENTION", data=abt_cc_s67).set_title("CC Retention by Year for S67 - San Diego GO (SC)")
```
To save the plot:
```python
SanDiego.figure.savefig("../imgs/SanDiegoGO01.png")
``
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1Nzk5MDc0MzJdfQ==
-->