> Written with [StackEdit](https://stackedit.io/).
## From SAS to PySpark
Notes about how to transcribe SAS code into PySpark code.

### How to write a SAS macro using Pyspark

```sas
data df;
    input id year sales;
    datalines;
    1 2015 100
    3 2016 200
    5 2017 300 
    ;
run;

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
eyJoaXN0b3J5IjpbMTcxMTk0MTU2NywxNjc4NDgwMjcwLDkzNz
MwOTk3M119
-->