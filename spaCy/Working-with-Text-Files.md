> Written with [StackEdit](https://stackedit.io/).

# Working with Text Files with Python
> This notes comes from the Udemy course: NLP Natural Language Processing with Python from Jose Portilla. Section 2: Python Text Basics

## Working with Text Files with Python

### Basic print formatting (f-string literal)
On Python 3.6 and higher includes what it knowns as formatting string literals or f-string literals for short.
```python
person = "Jose"
print(f"my name is {person}")
```
output:
```
my name is Jose
```
If you have a Python object such as a dictionary, 
```python
d = {'a':123,'b':456}
```
you can do some operations within the string litteral
```python
print(f"my number is {d['a']}") 
```
output:
```
my numer is 123
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzQ1NDcxMzc2XX0=
-->