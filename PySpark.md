### Spark DataFrame Basics
In order to actually work with Spark data frames we first need to start a Spark session to do that.
```python
from pyspark.sql import SparkSession
```
To actually start the Spark session let's create a variable that by convention we call `spark`. Give the `appName` whatever the name you want, in this case  `Basics`
```python
spark = SparkSession.builder.appName('Basics').getOrCreate()
```




<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE2MTk0ODMyOCw0NDEyNDYxNDcsMTk3NT
Q2MDQyMiw0NjE0ODk2ODRdfQ==
-->