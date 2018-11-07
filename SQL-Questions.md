> Written with [StackEdit](https://stackedit.io/).
## SQL Questions 

`1.`	Is a `NULL` value same as zero or a blank space? If not, then what is the difference?
<br><br/>
`2.`	What is the purpose of the condition operators `BETWEEN` and `IN`?
<br><br/>
`3.`	How do you search for a value in a database table when you don’t have the exact value to search for?
<br><br/>
`4.`	What is the default ordering of data using the `ORDER BY` clause? How could it be changed?
<br><br/>
`5.`	If a table contains duplicate rows, does a query result display the duplicate values by default? How can you eliminate duplicate rows from a query result?
<br><br/>
`6.`	What is the difference between cross joins and natural joins?
<br><br/>
`7.`	What is the purpose of the group functions in SQL? Give some examples of group functions.
<br><br/>
`8.`	Say True or False. Give explanation if False: 
<br><br/>
<i>By default, the group functions consider only distinct values in the set.</i>
<br><br/>
`9.`	Say True or False. Give explanation if False: 
<br><br/>
<i>The `DISTINCT` keyword allows a function to consider only non-duplicate values.</i>
<br><br/>
`10.` Say True or False. Give explanation if False:
<br><br/>
<i>COUNT(*) returns the number of columns in a table.</i>
<br><br/>
`11.`	What’s wrong in the following query?
```SQL
SELECT subject_code, COUNT(name)  
FROM students;
```
`12.`	What is the meaning of the following query?
```SQL
SELECT *
FROM station_data
WHERE length(report_code) != 6;
```
`13.`	What is the meaning of the following query?
```SQL
SELECT *
FROM station_data
WHERE report_code LIKE 'A%';
```
`14.`	What is the meaning of the following query?
```SQL
SELECT report_code, coalesce(precipitation, 0) AS rainfall
FROM station_data;
```
`15.`	What is the meaning of the following query?
```SQL
SELECT year, SUM(precipitation) as tornado_precipitation
FROM station_data
WHERE tornado = 1
GROUP BY year;
```
`16.`	What the meaning of the following query?
```SQL
SELECT DISTINCT station_number, year
FROM station_data;
```
`17.`	What is the meaning of the following query?

```SQL
SELECT report_code, year, month, day, wind_speed,

CASE
       WHEN wind_speed >= 40 THEN ‘HIGH’
       WHEN wind_speed >= 30 THEN ‘MODERATE’
       ELSE `LOW`
END as wind_severity

FROM station_data;
```

`18.` What is the meaning of the following query?

```SQL
SELECT year,
 
SUM (precipitation) AS total_precipitation,

FROM station_data
GROUP BY year
HAVING total_precipitation > 30;
```

`19.` What is the meaning of the following query?


```SQL
SELECT year, month, day,
 
SUM (CASE WHEN tornado = 1 THEN precipitation ELSE 0 END) AS tornado_precipitation,

SUM (CASE WHEN tornado = 0 THEN precipitation ELSE 0 END) AS non_tornado_precipitation

FROM station_data
GROUP BY year, month;
```


`20.` Consider the CUSTOMERS table having the following records −

| ID | NAME     | AGE | ADDRESS   | SALARY   |
|----|----------|-----|-----------|----------|
|  1 | Ramesh   |  35 | Ahmedabad |  2000.00 |
|  2 | Khilan   |  25 | Delhi     |  1500.00 |
|  3 | kaushik  |  23 | Kota      |  2000.00 |
|  4 | Chaitali |  25 | Mumbai    |  6500.00 |
|  5 | Hardik   |  27 | Bhopal    |  8500.00 |
|  6 | Komal    |  22 | MP        |  4500.00 |
|  7 | Muffy    |  24 | Indore    | 10000.00 |

What's the output of the following query:

```SQL
SQL> SELECT * 
   FROM CUSTOMERS 
   WHERE ID IN (SELECT ID 
         FROM CUSTOMERS 
         WHERE SALARY > 4500) ;
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTczMTQ0MTE1OV19
-->