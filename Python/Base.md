> Written with [StackEdit](https://stackedit.io/).

### The Current Working Directory

```python
import os
os.getcwd()
os.chdir('/Users/marcosaguilerakeyser/Projects/advanced-nlp-with-spacy')
os.getcwd()
```
[reference](http://automatetheboringstuff.com/chapter8/)

### Absolute vs. Relative Paths

There are two ways to specify a file path.

-   An  _absolute path_, which always begins with the root folder
    
-   A  _relative path_, which is relative to the program’s current working directory
    

There are also the  _dot_  (`.`) and  _dot-dot_  (`..`) folders. These are not real folders but special names that can be used in a path. A single period (“dot”) for a folder name is shorthand for “this directory.” Two periods (“dot-dot”) means “the parent folder.”'

[reference](http://automatetheboringstuff.com/chapter8/)

### Finding the version of the python

```python
import sys
print(sys.version)
print(sys.version_info)
```
Output:

```
3.7.1 (default, Dec 10 2018, 22:54:23) [MSC v.1915 64 bit (AMD64)]

sys.version_info(major=3, minor=7, micro=1, releaselevel='final', serial=0)

```

```python
import sklearn
print(sklearn.__version__)
```
[reference](https://medium.com/@rakshithvasudev/finding-the-version-of-the-python-package-is-very-easy-1db1a3271d88)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY2NDQ4OTAwNSwtMjU0NTQ4NDA3LC0xNz
U5MTQwMzI4XX0=
-->