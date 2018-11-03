### Spark DataFrame Basics
In order to actually work with Spark data frames we first need to start a Spark session to do that.
```python
from pyspark.sql import SparkSession
```
To actually start the Spark session let's create a variable that by convention we call `spark`. Give the `appName` whatever the name you want, in this case  `Basics`
```python
spark = SparkSession.builder.appName('Basics').getOrCreate()
```
Now, most likely if you just open up the notebook and you are running this command for the first time 




<!--stackedit_data:
eyJoaXN0b3J5IjpbODE4Nzc5NTk1LDQ0MTI0NjE0NywxOTc1ND
YwNDIyLDQ2MTQ4OTY4NF19
-->