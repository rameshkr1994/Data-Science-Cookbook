


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

Intall TeX: In this case, for Windows you need to install MikTex from here https://miktex.org/ and then you need to add the path to the executable files to your Environmental Variables:
```
C:/Users/t93kqi0/AppData/Local/Programs/MiKTeX 2.9/miktex/bin/x64;
C:/Users/t93kqi0/AppData/Local/Pandoc;
```
The easiest way to find the above paths is just going to the Environmental Variables window
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjcxMDU3MjAyLDg3OTY2ODkzOSwyMDQyMT
gxNDQsNjM2MjQxODQxLDE1Mzc4MjE3OTksLTE5NjMxMTA1LDIw
MzIxNDk2MjcsLTE0NTIwODAwNjBdfQ==
-->