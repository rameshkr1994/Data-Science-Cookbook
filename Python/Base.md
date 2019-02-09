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

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3NTkxNDAzMjhdfQ==
-->