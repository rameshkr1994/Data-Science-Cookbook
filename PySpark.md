### Spark DataFrame Basics
In order to actually work with Spark data frames we first need to start a Spark session to do that.
```python
from pyspark.sql import SparkSession
```
To actually start the Spark session let's create a variable that by convention we call `spark`. Give the `appName` whatever the name you want, in this case  `Basics`
```python
spark = SparkSession.builder.appName('Basics').getOrCreate()
```
Now, most likely if you just open up the notebook and you are running this command for the first time it is going to take maybe a minute or two.
### Read a data set
Use the `.read` method to read different file types
```python
df = spark.read.json('people.json')
```




<!--stackedit_data:
eyJoaXN0b3J5IjpbMjExMDk5Mzc0MCw0NDEyNDYxNDcsMTk3NT
Q2MDQyMiw0NjE0ODk2ODRdfQ==
-->