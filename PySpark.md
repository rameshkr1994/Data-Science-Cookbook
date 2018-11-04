# Spark Notes using DataFrame syntax (2.0 and higher)

### References:
- [ Complete Guide on DataFrame Operations in PySpark](https://www.analyticsvidhya.com/blog/2016/10/spark-dataframe-and-operations/)
- [Spark and Python for Big data with PySpark](https://www.udemy.com/spark-and-python-for-big-data-with-pyspark/)
- [ Pandas Comparison with SAS](http://pandas-docs.github.io/pandas-docs-travis/comparison_with_sas.html)
 - [Python for SAS Users: The pandas Data Analysis Library](https://blog.dominodatalab.com/pandas-for-sas-users-part-1/)
  - [PythonForSASUsers](http://nbviewer.jupyter.org/github/RandyBetancourt/PythonForSASUsers/tree/master)
### Start a Spark session
In order to actually work with Spark data frames we first need to start a Spark session to do that.
```python
from pyspark.sql import SparkSession
```
To actually start the Spark session let's create a variable that by convention we call `spark`. Give the `appName` whatever the name you want, in this case  `Basics`
```python
spark = SparkSession.builder.appName('Basics').getOrCreate()
```
Now, most likely if you just open up the notebook and you are running this command for the first time it is going to take maybe a minute or two.
### PySpark version
```python
sc.version
```
Output
```python
'2.2.1'
```
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
### Statistical summary of the DataFrame
Use `.describe` method to get a statistical summary of the DataFrame
```python
df.describe().show()
```
If you call `describe()` by itself you get back a DataFrame
### Create a DataFrame

```python
inputDF =spark.createDataFrame([
    (0, "This is an apple. An apple is a fruit, not a vegetable"),
    (1, "Fruits are tasty"),
    (2, "Vegatables are nasty")],
    ["id","document"])
```
Use `show(truncate=False)` to show the `DataFrame` content
```python
inputDF.show(truncate = False)
```
Output:
```
+---+------------------------------------------------------+
|id |document                                              |
+---+------------------------------------------------------+
|0  |This is an apple. An apple is a fruit, not a vegetable|
|1  |Fruits are tasty                                      |
|2  |Vegatables are nasty                                  |
+---+------------------------------------------------------+
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc4Mjg5MjA4Miw0MTY2NDIwODUsNzQxMT
EyMTg4LC0xMjgxMDc2MDExLC03NDIzNTkwMzYsMTI3OTczMjU1
NiwyMTEwOTkzNzQwLDQ0MTI0NjE0NywxOTc1NDYwNDIyLDQ2MT
Q4OTY4NF19
-->