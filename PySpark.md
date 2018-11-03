### Spark DataFrame Basics
In order to actually work with Spark data frames we first need to start a Spark session to do that.
```python
from pyspark.sql import SparkSession
```
To actually start the Spark session let's create a variable that by convention we call `spark`
```python
spark = SparkSession.builder.appName('Basics').getOrCreate()
```




<!--stackedit_data:
eyJoaXN0b3J5IjpbODY5MzcwNjczLDQ0MTI0NjE0NywxOTc1ND
YwNDIyLDQ2MTQ4OTY4NF19
-->