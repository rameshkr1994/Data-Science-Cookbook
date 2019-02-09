> Written with [StackEdit](https://stackedit.io/).

# Introduction to Python Text Basics

- Understand how to open a normal `.txt` and `.pdf` files with basic Python libraries.
- Learn some basic regular expressions.

## Working with text files with Python - Part One

### Write a `.txt` file using Jupyter and magic cells

```python
%%writefile test.txt
Hello, this is a quick test file.
This is the second line of the file.
```

### Read a file

First you need to open the file:
```python
myfile = open('test.txt')
```
Then read the file:
```python
myfile.read()
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU4ODc2NDk5MSwtMjA0MTcxMzU2MF19
-->