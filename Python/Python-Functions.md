
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
Out[1]: 3
```
Remember that this instantiation not necessary for when you want to call the function `plus()`! You would be able to execute `plus(1,2)`:

```python
plus(1,2)
```
Output:
```
Out[1]: 3
```
### Parameters vs Arguments

Parameters are the names used when defining a function or a method, and into which arguments will be mapped. In other words, arguments are the things which are supplied to any function or method call, while the function or method code refers to the arguments by their parameter names.

Consider the following example and look back to the above chunk: you pass two  _arguments_  to the  `sum()`  method of the  `Summation`  class, even though you previously defined three  _parameters_, namely,  `self`,  `a`  and  `b`.

What happened to  `self`?

The first argument of every class method is always a reference to the current instance of the class, which in this case is  `Summation`. By convention, this argument is called  `self`.

This all means that you don’t pass the reference to  `self`  in this case because  `self`  is the parameter name for an implicitly passed argument that refers to the instance through which a method is being invoked. It gets inserted implicitly into the argument list.

## How To Define A Function: User-Defined Functions (UDFs)

The four steps to defining a function in Python are the following:

1.  Use the keyword  `def`  to declare the function and follow this up with the function name.
2.  Add parameters to the function: they should be within the parentheses of the function. End your line with a colon.
3.  Add statements that the functions should execute.
4.  End your function with a return statement if the function should output something. Without the return statement, your function will return an object  `None`.

```python
def hello():
  print("Hello World") 
  return 

hello()
```
Output:
```
Out[1]: Hello World
```
Of course, your functions will get more complex as you go along: you can add for loops, flow control, … and more to it to make it more finegrained:

```python
def hello():
  name = str(input("Enter your name: "))
  if name:
    print ("Hello " + str(name))
  else:
    print("Hello World") 
  return 
  
hello()
```
In the above function, you ask the user to give a name. If no name is given, the function will print out “Hello World”. Otherwise, the user will get a personalized “Hello” response.

**Remember**  also that you can define one or more function parameters for your UDF. You’ll learn more about this when you tackle the Function Arguments section. Additionally, you can or can not return one or multiple values as a result of your function.

### The  `return`  Statement

Note that as you’re printing something in your UDF  `hello()`, you don’t really need to return it. There won’t be any difference between the function above and this one:

```py
def hello_noreturn():
  print("Hello World") 
```
However, if you want to continue to work with the result of your function and try out some operations on it, you will need to use the `return` statement to actually return a value, such as a String, an integer, …. Consider the following scenario, where `hello()` returns a String `"hello"`, while the function `hello_noreturn()` returns `None`:
```py
def hello():
  print("Hello World") 
  return("hello")

def hello_noreturn():
  print("Hello World")
  
# Multiply the output of `hello()` with 2 
hello() * 2

# (Try to) multiply the output of `hello_noreturn()` with 2 
hello_noreturn() * 2
```
Output
```
Hello World
Out[1]: 'hellohello'

Traceback (most recent call last):
  File "<stdin>", line 12, in <module>
    hello_noreturn() * 2
TypeError: unsupported operand type(s) for *: 'NoneType' and 'int'
```
The second function gives you an error because you can’t perform any operations with a  `None`. You’ll get a  `TypeError`  that says that you can’t do the multiplication operation for  `NoneType`  (the  `None`  that is the result of  `hello_noreturn()`) and  `int`  (`2`).

**Tip**  functions immediately exit when they come across a  `return`  statement, even if it means that they won’t return any value:
```py
def run():
  for x in range(10):
     if x == 2:
       return
  print("Run!")
  
run()
```
Another thing that is worth mentioning when you’re working with the  `return`  statement is the fact that you can use it to return multiple values. To do this, you make use of tuples.

**Remember**  that this data structure is very similar to that of a list: it can contain multiple values. However, tuples are immutable, which means that you can’t modify any amounts that are stored in it! You construct it with the help of double parentheses  `()`. You can unpack tuples into multiple variables with the help of the comma and the assignment operator.

Check out the following example to understand how your function can return multiple values:
```py
# Define `plus()`
def plus(a,b):
  sum = a + b
  return (sum, a)

# Call `plus()` and unpack variables 
sum, a = plus(3,4)

# Print `sum()`
print(sum)
```
Output:
```
7
```
**Note** that the `return` statement `return sum, a` would have the same result as `return (sum, a)`: the former actually packs `sum` and `a` into a tuple under the hood!

### How To Call A Function

In the previous sections, you have seen a lot of examples already of how you can call a function. Calling a function means that you execute the function that you have defined - either directly from the Python prompt or through another function (as you will see in the section “Nested Functions”).

Call your newly defined function  `hello()`  by simply executing  `hello()`, just like in the chunk below:
```py
hello()
```
Output:
```
Hello World
```
### How To Add Docstrings To A Python Function

Another essential aspect of writing functions in Python: docstrings. Docstrings describe what your function does, such as the computations it performs or its return values. These descriptions serve as documentation for your function so that anyone who reads your function’s docstring understands what your function does, without having to trace through all the code in the function definition.

Function docstrings are placed in the immediate line after the function header and are placed in between triple quotation marks. An appropriate Docstring for your  `hello()`  function is ‘Prints “Hello World”’.

```py
def hello():
"""Prints "Hello World".

Returns:
    None
"""
  print("Hello World") 
  return 
```
**Note** that docstrings can be more prolonged than the one that is given here as an example. If you’d like to study docstrings in more detail, you best check out some Github repositories of Python libraries such as [scikit-learn](https://github.com/scikit-learn/scikit-learn/tree/master/sklearn) or [pandas](https://github.com/pandas-dev/pandas/tree/master/pandas), where you’ll find plenty of examples!

### Function Arguments in Python

Earlier, you learned about the difference between parameters and arguments. In short, arguments are the things which are given to any function or method call, while the function or method code refers to the arguments by their parameter names. There are four types of arguments that Python UDFs can take:

-   Default arguments
-   Required arguments
-   Keyword arguments
-   Variable number of arguments

#### Default Arguments

Default arguments are those that take a default value if no argument value is passed during the function call. You can assign this default value by with the assignment operator  `=`, just like in the following example:

```py
# Define `plus()` function
def plus(a,b = 2):
  return a + b
  
# Call `plus()` with only `a` parameter
plus(a=1)

# Call `plus()` with `a` and `b` parameters
plus(a=1, b=3)
```
#### Required Arguments

As the name kind of gives away, the required arguments of a UDF are those that have to be in there. These arguments need to be passed during the function call and in precisely the right order, just like in the following example:

```py
# Define `plus()` with required arguments
def plus(a,b):
  return a + b
  ```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MDYyNjU4MTgsLTE2NTkxODUwOTQsLT
E0MDc3OTU3MzUsNTU4OTg3MjY4LC03MDcxMTgwNDYsLTI1NjEz
NTg3MywtMTA1MzM4Nzc2NSwtMTkxODQ5MTM5NSwtMTczNDIzMT
IwNl19
-->