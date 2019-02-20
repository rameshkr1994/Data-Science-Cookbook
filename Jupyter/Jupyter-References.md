


> Written with [StackEdit](https://stackedit.io/).
## Jupyter References

- [Working efficiently with JupyterLab Notebooks](https://florianwilhelm.info/2018/11/working_efficiently_with_jupyter_lab/ "Permalink to Working efficiently with JupyterLab Notebooks")
- [Cell magics](https://ipython.readthedocs.io/en/stable/interactive/magics.html)

### How to print Jupyter Notebooks in PDF
If you find the following error when you try to print to PDF a jupyter notebook on Jupyter Lab:

```
# 500 : Internal Server Error

The error was:
nbconvert failed: xelatex not found on PATH, 
if you have not installed xelatex you may need to 
do so. 
Find further instructions at https://nbconvert.readthedocs.io/en/latest/install.html#installing-tex.
```
You need to follow the steps here:

https://nbconvert.readthedocs.io/en/latest/install.html#installing-tex.`

Notes:

- `nbconvert` comes with the default Anaconda installation
- `Pandoc` I think also comes with the default Anaconda installation. If not install it. I installed it from here: https://pandoc.org/installing.html
- Intall TeX: In this case, for Windows you need to install MikTex from here https://miktex.org/ and then you need to add the path to the directory containing
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc4NjM0ODkyNSw4Nzk2Njg5MzksMjA0Mj
E4MTQ0LDYzNjI0MTg0MSwxNTM3ODIxNzk5LC0xOTYzMTEwNSwy
MDMyMTQ5NjI3LC0xNDUyMDgwMDYwXX0=
-->