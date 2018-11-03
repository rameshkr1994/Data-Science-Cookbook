### Spark DataFrame Basics
In order to actually work with Spark data frames we first need to start a Spark session to do that.
```python
from pyspark.sql import SparkSession
```
To start actually the Spark session let's create a variable that by convention we call `spark`
```python
spark = SparkSession.builder.appName('Basics').getOrCreate()
```



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5OTc4MTYxMjksMTk3NTQ2MDQyMiw0Nj
E0ODk2ODRdfQ==
-->