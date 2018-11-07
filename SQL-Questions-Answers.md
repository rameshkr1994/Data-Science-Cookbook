## SQL Questions 

`1.`	Is a `NULL` value same as zero or a blank space? If not, then what is the difference?

**Answer:** A `NULL` value is not same as zero or a blank space. A `NULL` value is a value which is ‘unavailable, unassigned, unknown or not applicable’. Whereas, zero is a number and blank space is a character.
<br><br/>
`2.`	What is the purpose of the condition operators `BETWEEN` and `IN`?

**Answer:** The `BETWEEN` operator displays rows based on a range of values. The `IN` condition operator checks for values contained in a specific set of values.
<br><br/>
`3.`	How do you search for a value in a database table when you don’t have the exact value to search for?

**Answer:** In such cases, the LIKE condition operator is used to select rows that match a character pattern. This is also called ‘wildcard’ search.
<br><br/>
`4.`	What is the default ordering of data using the `ORDER BY` clause? How could it be changed?

**Answer:** The default sorting order is ascending. It can be changed using the `DESC` keyword, after the column name in the `ORDER BY` clause.
<br><br/>
`5.`	If a table contains duplicate rows, does a query result display the duplicate values by default? How can you eliminate duplicate rows from a query result?

**Answer:** A query result displays all rows including the duplicate rows. To eliminate duplicate rows in the result, the DISTINCT keyword is used in the SELECT clause.
<br><br/>
`6.`	What is the difference between cross joins and natural joins?

**Answer:** The cross join produces the cross product or Cartesian product of two tables. The natural join is based on all the columns having same name and data types in both the tables. 
<br><br/>
`7.`	What is the purpose of the group functions in SQL? Give some examples of group functions.

**Answer:** Group functions in SQL work on sets of rows and returns one result per group. Examples of group functions are `AVG`, `COUNT`, `MAX`, `MIN`, `STDDEV`, `SUM`, `VARIANCE`. 
<br><br/>
`8.`	Say True or False. Give explanation if False: 
<br><br/>
<i>By default, the group functions consider only distinct values in the set.</i>

**Answer:** 

By default, group functions consider all values including the duplicate values.
<br><br/>
`9.`	Say True or False. Give explanation if False: 
<br><br/>
<i>The `DISTINCT` keyword allows a function to consider only non-duplicate values.</i>

**Answer:**

True
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

**Answer:**

It doesn’t have a `GROUP BY` clause. The `subject_code` should be in the `GROUP BY` clause.

`12.`	What is the meaning of the following query?
```SQL
SELECT *
FROM station_data
WHERE length(report_code) != 6;
```

**Answer:**

The `length()` function will count the number of characters for a given value. So, if we were assigned quality control and needed to ensure every `report_code` was six characters in length, we would want to make sure no records come back when running this query.

`13.`	What is the meaning of the following query?
```SQL
SELECT *
FROM station_data
WHERE report_code LIKE 'A%';
```

**Answer:**

Another common operation is to use wildcards with a `LIKE` expression, where `%` is any number of characters and `_` is any single character. Any other character is interpreted literally. So, if you wanted to find all report codes that start with the letter “A,” you would run this statement to find “A” followed by any characters.

`14.`	What is the meaning of the following query?
```SQL
SELECT report_code, coalesce(precipitation, 0) AS rainfall
FROM station_data;
```

**Answer:**

Like any function, a `coalesce()` can be used in the `SELECT` statement too, and not just the `WHERE`. This is helpful if you want to pretty up a report and not have null values displayed, but rather have some placeholder—for example, 0, “N/A” or “None”—which is more meaningful to most people.


`15.`	What is the meaning of the following query?
```SQL
SELECT year, SUM(precipitation) AS tornado_precipitation
FROM station_data
WHERE tornado = 1
GROUP BY year;
```
**Answer:**

It may not be apparent yet, but you can achieve some very specific aggregations by leveraging the `WHERE`. If you wanted the total precipitation by year only when a tornado was present, you would just have to filter on tornado being true. This will only include tornado-related precipitation in the totals.

`16.`	What the meaning of the following query?
```SQL
SELECT DISTINCT station_number, year
FROM station_data;
```

**Answer:**

If we want a distinct list of station numbers without any duplicates, we can use the `DISTINCT` keyword. You can also get distinct results for more than one column. If you need the distinct `station_number` and `year` sets, just include both of those columns in the `SELECT` statement.


`17.`	What is the meaning of the following query?

```SQL
SELECT report_code, year, month, day, wind_speed,

CASE
       WHEN wind_speed >= 40 THEN 'HIGH'
       WHEN wind_speed >= 30 THEN 'MODERATE'
       ELSE 'LOW'
END as wind_severity

FROM station_data;
```

**Answer:**

It is an equivalent way to create a variable using an `if-then` statement. It creates the variable `wind_severity` based on the values of the variable `wind_speed`. 

`18.` What is the meaning of the following query?

```SQL
SELECT year,
 
SUM (precipitation) AS total_precipitation

FROM station_data
GROUP BY year
HAVING total_precipitation > 30;
```
**Answer:**

If we wanted to filter on the `SUM()` value, we would need the filter to take place after it is calculated. This is where `HAVING` can be applied.

`19.` What is the meaning of the following query?


```SQL
SELECT year, month, day,
 
SUM (CASE WHEN tornado = 1 THEN precipitation ELSE 0 END) AS tornado_precipitation,

SUM (CASE WHEN tornado = 0 THEN precipitation ELSE 0 END) AS non_tornado_precipitation

FROM station_data
GROUP BY year, month;
```
**Answer:**

Say you wanted to aggregate `precipitation` into two sums, `tornado_precipitation` and `non_tornado_precipitation`, and `GROUP BY` year and month. The logic is primarily dependent on two fields: `precipitation` and `tornado`. But how exactly do you code this? If you give it some thought, you will realize you cannot do this with a `WHERE` statement unless you do two separate queries (one for tornado being true and the other false). But it is possible to do this in a single query using a `CASE` statement. You can move the tornado conditions from the `WHERE` to a `CASE`, and make the value 0 if the condition is false. Then you can `SUM` those `CASE` statements. 

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

**Answer:**

This would produce the following result:


| ID | NAME     | AGE | ADDRESS | SALARY   |
|----|----------|-----|---------|----------|
|  4 | Chaitali |  25 | Mumbai  |  6500.00 |
|  5 | Hardik   |  27 | Bhopal  |  8500.00 |
|  7 | Muffy    |  24 | Indore  | 10000.00 |

[Source](https://www.tutorialspoint.com/sql/sql-sub-queries.htm)

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg2MDA5NjYyM119
-->