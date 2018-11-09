### Start a Spark session
In order to actually work with Spark data frames we first need to start a Spark session to do that.
```python
%pyspark
from pyspark.sql import SparkSession
```
To actually start the Spark session let's create a variable that by convention we call `spark`. Give the `appName` whatever the name you want, in this case  `Basics`
```python
%pyspark
spark = SparkSession.builder.appName('Basics').getOrCreate()
```
Now, most likely if you just open up the notebook and you are running this command for the first time it is going to take maybe a minute or two.
### `PySpark` version
```python
%pyspark
sc.version
```
Output
```python
%pyspark
'2.2.1'
```
### Create a `DataFrame`

```python
%pyspark
inputDF =spark.createDataFrame([
    (0, "This is an apple. An apple is a fruit, not a vegetable"),
    (1, "Fruits are tasty"),
    (2, "Vegatables are nasty")],
    ["id","document"])
```
### Show `DataFrame` Content
In order to show the data, use the `show()` method

Use `show(truncate=False)` to show the `DataFrame` content without column truncation:
```python
%pyspark
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
###  Show `DataFrame` schema
Use the `printSchema()` method
```python
%pyspark
df.printSchema()
```
Output:
```
root 
|-- id: long (nullable = true) 
|-- document: string (nullable = true)
```
### Read a `JSON` file:
Use the `.read` method to read different file types
```python
%pyspark
df = spark.read.json('/user/t93kqi0/people.json')
```
Now we have a data frame called `df`
### Read a `CSV` file
Use the `.read` methods to read different file types. Use `header='true'` if the data contains a header. Use `inferSchema = True` to infer data types:
```python
%pyspark
AgentRoster = spark.read.csv('/user/t93kqi0/AgentRoasterAddrs.csv', header='true', inferSchema = True)
```
Now we have a data frame called `AgentRoster`
### Export `DataFrame` in PySpark to CSV
For Apache Spark 2+, in order to save `DataFrame` into single csv file use following command:
```python
%pyspark
AgentAdrsPre.repartition(1).write.csv("/user/t93kqi0/AgentAdrsPre.csv", sep='|')
```
Here `1` indicate that I need one partition of csv only. You can change it according to your requirements. 

### Show `DataFrame` column names
Use the `.column`  attribute meaning you don't need to actually have to close parentheses there.
```python
%pyspark
inputDF.columns
```
Output:
```
['id', 'document']
```
It returns a Python list of all the column names
### Statistical summary of a `DataFrame`
Use `.describe` method to get a statistical summary of the DataFrame
```python
%pyspark
df.describe().show()
```
If you call `describe()` by itself you get back a DataFrame
### Select columns
```python
%pyspark
AgentAdrsPre =  AgentRoaster.select('AgentID', 'GOCode','GO','PreferredAddress1', 'PreferredAddress2', 
                                    'PreferredAddress3', 'PreferredCity', 'PreferredState', 'PreferredZip')
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0MTI5MzA3MjIsMTAxODIwODI0OCwtOT
EyMjAwODVdfQ==
-->