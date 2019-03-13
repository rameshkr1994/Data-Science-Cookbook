
> Written with [StackEdit](https://stackedit.io/).

## Render and align images on Jupyter Lab

To render an image inside a Markdown dell use:

```
![](../imgs/logistic-function-01.png)
```

To align an image inside a Markdown cell use:

```
<center><img src='../imgs/logistic-function-01.png'></center>
```
or 

```
<center><img width="300" height="300" src='../imgs/logistic-function-01.png'></center>
```

To align an images inside a code cell:

```python
%%html
<img src="../imgs/logistic-function-01.png" width="240" height="240" align="center"/>
```

or 

```python
from IPython.display import Image
Image(filename="../imgs/logistic-function-01.png", width=400, height=400)
```
## Create spaces
Use:
```
<br>
```

## Create a Table of Contents in Jupyter
This is the Markdown code you need to write to get a TOC:
```
### Table of Contents

- [Import Data](#Import-Data)
- [Join AAPR Variable](#Join-AAPR-Variable)
- [Join AVG_FYC Variable](#Join-AVG_FYC-Variable)
- [Join CULTMARK Variable](#Join-CULTMARK-Variable)
- [Join TIER_GROUP Variable](#Join-TIER_GROUP-Variable)
- [Join UNEMPLOY Variable](#Join-UNEMPLOY-Variable)
- [Join RURAL_URBAN variable](#Join-RURAL_URBAN-variable)
- [Missing values treatment](#Missing-values-treatment)
- [Export final data set](#Export-final-data-set) 
```
The text inside brackets [...] is what you want to show up in the TOC. The text inside (...) is the title of the corresponding paragraph in Jupyter notebook. You need to add always `#` at the beginning and use and `-` to separate the words.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwNTM1ODc1MSw5OTEwNDM5MDMsMTA4Nz
Y5NjQ2OSwtMTk0ODU2MTY3NCwtMTIyNzQ5MjY2OV19
-->