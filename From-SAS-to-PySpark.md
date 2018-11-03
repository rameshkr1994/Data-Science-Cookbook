> Written with [StackEdit](https://stackedit.io/).
## From SAS to PySpark
Notes about how to transcribe SAS code into PySpark code.

### How to create a SAS data set using SAS
Using the `datalines` option it is possible create a SAS data set using code:
```sas
data df;
    input id year sales;
    datalines;
    0 2015 100
    3 2016 200
    5 2017 300 
    ;
run;
```
### How to create a PySpark DataFrame using PySpark



### How to write a SAS macro using Pyspark
The following SAS macro creates three SAS data sets:
```sas
%macro sales (year=);
data df_&year;
	set df;
	if year = &year then output;
run;
%mend sales;

%sales(year=2015);
%sales(year=2016);
%sales(year=2017);
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
eyJoaXN0b3J5IjpbLTI0NjA5NDE3MCwxNjc4NDgwMjcwLDkzNz
MwOTk3M119
-->