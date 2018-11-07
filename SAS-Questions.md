## SAS Questions

`1.`	What is the difference between `DO WHILE` and `DO UNTIL`?
<br><br/>
`2.`	How many data types are there in SAS?
<br><br/>
`3.`	Purpose of double trailing `@@` in `INPUT` Statement?
<br><br/>
`4.`	How to include or exclude specific variables in a data set?
<br><br/>
`5.`	What are the default statistics that `PROC MEANS` produces?
<br><br/>
`6.`	What is Program Data Vector (PDV)?
<br><br/>
`7.`	What is `DATA _NULL_`?
<br><br/>
`8.`	How to remove unique and duplicate values? 
<br><br/>
`9.`	How to sort in descending order?
<br><br/>
`10.` How to convert a numeric variable to a character variable?
<br><br/>
`11.`	What is the difference between `SET` and `MERGE`?
<br><br/>
`12.`	What is the difference between `+` operator and `SUM` function?
<br><br/>
`13.`	What `SUBSTR` function does?
<br><br/>
`14.`	What is the difference between `SAS PROC`s and the `SAS DATA STEP`s?
<br><br/>
`15.`	If a variable contains letters or special characters, can it be numeric data type?
<br><br/>
`16.`	What can be the size of largest dataset in SAS?
<br><br/>
`17.`	What is the difference between `CLASS` statement and `BY` statement in `PROC MEANS`?
<br><br/>
`18.` How to specify variables to be processed by the `FREQ` procedure?
<br><br/>
`19.` What’s wrong in the following code?

```SAS
DATA demographics;
    INFILE `C:\books\learning\mydata.csv` dsd;
    INPUT Gender $ Age Height Weight;
RUN;
```
`20.` What the meaning of the following code?

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
`21.` What the meaning of the following code?

```SAS
PROC PRINT DATA = readin (FIRSTOBS=5 OBS=10);
RUN;
```
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
`23.` What the meaning of the following code?

```SAS
PROC FREQ DATA = auto;
    TABLES a*b;
RUN;
```
`24.` What the meaning of the following code?

```SAS
PROC EXPORT DATA=sashelp.class;
   OUTFILE= `c:\myfiles\class\mydata.csv`
   DBMS=DLM;
   DELIMITER=’&’
RUN;
```
`25.` What the meaning of the following code?

```SAS
DATA test_03;
    MERGE test_01(in=a) test02(in=b);
    BY owner_id cnt_id;
    IF a
RUN;
```
`26.` What the meaning of the following code?

```SAS
PROC RANK DATA=test2 OUT=ranky TIES=low DESCENDING GROUPS=10;
     VAR score;
     RANKS r_score;
RUN;
```
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
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzAzNTgzODI3XX0=
-->