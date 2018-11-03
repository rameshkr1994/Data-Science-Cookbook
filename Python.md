> Written with [StackEdit](https://stackedit.io/).

Assign a new column to df called 'age' with a list of ages
```python
df2 = df.assign(age_1 = [31, 32, 19], age_2 = [1,2,3], age_3 = [4,5,6], age_4 = [6,7,8])

age_2 = [1,2,3]
age_3 = [4,5,6]
age_4 = [6,7,8]

df2
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
eyJoaXN0b3J5IjpbLTEyODMwNzI3OTgsLTg1Nzg2MTIzN119
-->