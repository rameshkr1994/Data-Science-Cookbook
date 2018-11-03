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
Now we have a data frame called `df`
### Show a DataFrame
In order to show the data, use the `show()` method
```python
df.show()
```
###  Show DataFrame schema
Use the `printSchema()` method
```python
df.printSchema()
```
### Show DataFrame column names
Use the `.column`  attribute meaning you don't need to actually have to close parentheses there.
```python
df.columns
```
It returns a Python list of all the column names




<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM3NzIwNDE1OCwyMTEwOTkzNzQwLDQ0MT
I0NjE0NywxOTc1NDYwNDIyLDQ2MTQ4OTY4NF19
-->