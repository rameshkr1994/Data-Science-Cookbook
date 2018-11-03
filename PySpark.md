### Spark DataFrame Basics
In order to actually work with Spark data frames we first need to start a Spark session to do that.
```python
from pyspark.sql import SparkSession
```
To actualpark session let's create a variable that by convention we call `spark`
```python
spark = SparkSession.builder.appName('Basics').getOrCreate()
```



<!--stackedit_data:
eyJoaXN0b3J5IjpbODkxMzQzMjgwLDE5NzU0NjA0MjIsNDYxND
g5Njg0XX0=
-->