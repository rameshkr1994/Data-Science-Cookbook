### Spark DataFrame Basics
Start a Spark session:
```python
from pyspark.sql import SparkSession
```
To start actually the Spark session let's create a variable that by convention we call `spark`
```python
spark = SparkSession.builder.appName('Basics').getOrCreate()
```



<!--stackedit_data:
eyJoaXN0b3J5IjpbMTk3NTQ2MDQyMiw0NjE0ODk2ODRdfQ==
-->