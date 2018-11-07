## SAS Questions & Answers

`1.`	What is the difference between `DO WHILE` and `DO UNTIL`?

**Answer:** The `DO WHILE` expression is evaluated at the top of the DO loop. If the expression is false the first time it is evaluated, then the DO loop never executes. Whereas `DO UNTIL` executes at least once.
<br><br/>
`2.`	How many data types are there in SAS?

**Answer:** Character and Numeric.
<br><br/>
`3.`	Purpose of double trailing `@@` in `INPUT` Statement?

**Answer:** The double trailing sign (`@@`) tells SAS rather than advancing to a new record, hold the current input record for the execution of the next `INPUT` statement.
<br><br/>
`4.`	How to include or exclude specific variables in a data set?

**Answer:** Using `DROP`, `KEEP` statements and `DATA` and `SET` options.
<br><br/>
`5.`	What are the default statistics that `PROC MEANS` produces?

**Answer:** It produces the default statistics of `MIN`, `MAX`, `MEAN` and `STD DEV`.
<br><br/>
`6.`	What is Program Data Vector (PDV)?

**Answer:** PDV is a logical area in the memory.PDV is created followed by the creation of input buffer. SAS builds dataset in the PDV area of memory. 
<br><br/>
`7.`	What is `DATA _NULL_`?

**Answer:** It can also be used to write output without creating a dataset. 
<br><br/>
`8.`	How to remove unique and duplicate values? 

**Answer:** 

By using `PROC SORT` with `NODUPKEY` and `NODUP` options.
<br><br/>
`9.`	How to sort in descending order?

**Answer:** Use `DESCENDING` keyword in `PROC SORT` code.
<br><br/>
`10.` How to convert a numeric variable to a character variable?

**Answer:** By creating a differently-named variable using the `PUT` function.

`11.`	What is the difference between `SET` and `MERGE`?

**Answer:**

`SET` concatenates the data sets where as `MERGE` matches the observations of the data sets.

`12.`	What is the difference between `+` operator and `SUM` function?

**Answer:** `SUM` function returns the sum of non-missing arguments whereas `+` operator returns a missing value if any of the arguments are missing.


`13.`	What `SUBSTR` function does?

**Answer:** The `SUBSTR` function is used to extract substring from a character variable.


`14.`	What is the difference between `SAS PROC`s and the `SAS DATA STEP`s?

**Answer:** Procs are sub-routines with a specific purpose in mind and the data step is designed to read in and manipulate data.

`15.`	If a variable contains letters or special characters, can it be numeric data type?

**Answer:** No, it must be character data type.

`16.`	What can be the size of largest dataset in SAS?

**Answer:** The number of observations is limited only by computer’s capacity to handle and store them.

`17.`	What is the difference between `CLASS` statement and `BY` statement in `PROC MEANS`?

**Answer:** `BY` processing requires that your data already be sorted or indexed in the order of the `BY` variables.

`18.` How to specify variables to be processed by the `FREQ` procedure?

**Answer:** By using `TABLES` statement.

`19.` What’s wrong in the following code?

```SAS
DATA demographics;
    INFILE `C:\books\learning\mydata.csv` dsd;
    INPUT Gender $ Age Height Weight;
RUN;
```

**Answer:** It doesn’t have a `GROUP BY` clause. The `subject_code` should be in the `GROUP BY` clause.

`20.` What the meaning of the following code?

**Answer:** 

```SAS
LIBNAME Mozart `c:\books\learning`;

DATA mozart.test_scores;
    LENGHT ID $ 3 Name $ 15;
    INPUT ID $ Score1-Score3 Name $;
DATALINES;
1 90 95 98
2 78 77 75
3 88 91 92
;
```

**Answer:** It creates the SAS dataset `test_scores` in the `mozart` permanent library by reading the data lines bellow the `DATALINES` keyword. The INPUT option creates the `ID` and `Name` variables as character variables and the `Score1`, `Score2` and `Score3` as numeric variables. The length of the `ID` variable is 3 and the length for the `Name` variable is 15.

`21.` What the meaning of the following code?

```SAS
PROC PRINT DATA = readin (FIRSTOBS=5 OBS=10);
RUN;
```

**Answer:** The `FIRSTOBS=` and `OBS=` data set options would tell SAS to print observations 5 through 10 from the data set `READIN`.

`22.` What the meaning of the following code?

```SAS
DATA readin;
DO i=1 TO 100;
    tep=0 + rannor(1)*1;
    OUTPUT;
END;
RUN;

PROC MEANS DATA=readin MEAN STDDEV;
    VAR temp;
RUN;
```

**Answer:** It creates a dataset with observations = 100, mean 0 and standard deviation 1.

`23.` What the meaning of the following code?

```SAS
PROC FREQ DATA = auto;
    TABLES a*b;
RUN;
```

**Answer:** It generates cross tabulation.

`24.` What the meaning of the following code?

```SAS
PROC EXPORT DATA=sashelp.class;
   OUTFILE= `c:\myfiles\class\mydata.csv`
   DBMS=DLM;
   DELIMITER=’&’
RUN;
```

**Answer:** It exports as CSV file using ampersand as delimiter.

`25.` What the meaning of the following code?

```SAS
DATA test_03;
    MERGE test_01(in=a) test02(in=b);
    BY owner_id cnt_id;
    IF a
RUN;
```

**Answer:** It is a `LEFT JOIN` using a SAS data step. It returns all records from the left table (`test_01`), and the matched records from the right table (`test_02`). 

`26.` What the meaning of the following code?

```SAS
PROC RANK DATA=test2 OUT=ranky TIES=low DESCENDING GROUPS=10;
     VAR score;
     RANKS r_score;
RUN;
```

**Answer:** It generaates 10 deciles for the variable `score`. The variable that contains the deciles (0, 1, 2, ...,9) is `r_score`.  

`27.` What the meaning of the following code?

```SAS
DATA nums;
    SET learn.chars (RENAME=
                    (Height = Char_Height
                     Weight = Char_Weight
                     Date   = Char_Date));
    Height = INPUT(Char_Height,8.);
    Weight = INPUT(Char_Weight,8.);
    Date   = INPUT(Char_Date,mmddyy10.);
    DROP Char_Height Char_Weight Char_Date;
RUN;
```

**Answer:** Character-to-numeric conversion using the technique called "swap and drop". 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5NzExMTM1NzldfQ==
-->