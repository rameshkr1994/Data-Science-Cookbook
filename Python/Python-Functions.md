
> Written with [StackEdit](https://stackedit.io/).

# Python Functions Tutorial

### References

- [Python Functions Tutorial](https://bit.ly/2DDlBsF)

Functions are an essential part of the Python programming language: you might have already encountered and used some of the many fantastic functions that are built-in in the Python language or that come with its library ecosystem. However, as a Data Scientist, you’ll constantly need to write your own functions to solve problems that your data poses to you.

That’s why this post will introduce you to functions in Python. You’ll cover the following topics:

## Functions in Python

You use functions in programming to bundle a set of instructions that you want to use repeatedly or that, because of their complexity, are better self-contained in a sub-program and called when needed. That means that a function is a piece of code written to carry out a specified task. To carry out that specific task, the function might or might not need multiple inputs. When the task is carried out, the function can or can not return one or more values.

There are three types of functions in Python:
- Built-in functions, such as  `help()`  to ask for help,  `min()`  to get the minimum value,  `print()`to print an object to the terminal,… You can find an overview with more of these functions  [here](https://docs.python.org/3/library/functions.html).
-   User-Defined Functions (UDFs), which are functions that users create to help them out; And
-   Anonymous functions, which are also called lambda functions because they are not declared with the standard  `def`  keyword.

### Functions vs Methods

A method refers to a function which is part of a class. You access it with an instance or object of the class. A function doesn’t have this restriction: it just refers to a standalone function. This means that all methods are functions, but not all functions are methods.

Consider this example, where you first define a function `plus()` and then a `Summation` class with a `sum()` method:

```python
# Define a function `plus()`
def plus(a,b):
  return a + b
  
# Create a `Summation` class
class Summation(object):
  def sum(self, a, b):
    self.contents = a + b
    return self.contents 
```
If you now want to call the `sum()` method that is part of the `Summation` class, you first need to define an instance or object of that class. So, let’s define such an object:

```python
# Instantiate `Summation` class to call `sum()`
sumInstance = Summation()
sumInstance.sum(1,2)
```
Output:
```
3
```
Remember that this instantiation not necessary for when you want to call the function `plus()`! You would be able to execute `plus(1,2)`:

```python
plus(1,2)
```
Output:
```
3
```


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTgyNTE1MTY0NywtMTkxODQ5MTM5NSwtMT
czNDIzMTIwNl19
-->