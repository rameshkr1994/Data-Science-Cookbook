> Written with [StackEdit](https://stackedit.io/).
# Atom Notes

### How to use `hydrogen` Atom package with Anaconda

In order to use Atom (`hydrogen`) with Anaconda you need first to install Anaconda. Do not add the PATH environmental variables during the installation. Once installed, add the environmental variable:

Computer > click on right bottom of the mouse > Properties > Advanced System sttings > Environmental Variables

You need to change the `User variables for T93KQI0` and also the `System Variables`. But the first ones are the ones are really important.

The environmental variables for Anaconda are:

`C:\Users\t93kqi0\AppData\Local\Continuum\anaconda3\Scripts;`
`C:\Users\t93kqi0\AppData\Local\Continuum\anaconda3;`

The variables are for Atom to find Python. 

Install Atom and add the environment variable too:

`C:\Users\t93kqi0\AppData\Local\atom;`

The environment variable of for the console to be able to open Atom from the console. But we don't need this last one in reality.

Then you need to go [here](https://nteract.gitbooks.io/hydrogen/docs/Installation.html) to install the kernels you need. In this case, because we are using Anaconda, we want to use the IPython kernel. To install it go [here](https://nteract.io/kernels?_sm_nck=1) . Because we are using Anaconda and not regular Python we need to use this section:

Using conda

```

conda create -n my_conda python=3  # Or python=2 for Python 2
source activate my_conda           # On Windows, remove the word 'source'
conda install ipykernel            # install Python kernel (ipykernel) into the conda environment
python -m ipykernel install        # install python kernel into nteract's available kernel list
```

But, the above code assumes that you are going to create an Anaconda virtual environment every time you create a project with Atom for example. I am no interested on creating different environments, so instead of running the above code we can run the following using the Anaconda console as administrator:

```
conda install ipykernel            # install Python kernel (ipykernel) into the conda environment
python -m ipykernel install        # install python kernel into nteract's available kernel list
```
Either way, if you decide to create different environments or you not at the end of the process you need to run the following to update the IPython's kernel spec, run: 

`python -m ipykernel install --user`

[reference]([https://github.com/nteract/hydrogen/issues/1241](https://github.com/nteract/hydrogen/issues/1241))

Now close the Anaconda console. Then, open Atom. Excute now any code that uses some of the libraries installed on Anaconda, for example:

```python
import pandas as pd
import numpy as np

2 + 2

print("Hello world!")
```
And should work. Atom and hydrogen now are using Anaconda kernel to run the above lines of code.

### How to use Anaconda environment with Atom (this is not right!!! delete it!) See the above note

First install Anaconda. During the Anaconda installation click on the option "Add Anaconda to my PATH environment variable:

![](https://cdn-images-1.medium.com/max/640/1*7a9zVyGP3iMXu9aB4e_Vhw.png)

Now install Atom. Atom will open, close it. Then install the Atom package  `platformio-ide-terminal`. To do that, open windows CMD console as administrator. Then write:
```
$ apm install platform-ide-terminal
```
Now open Atom. But, to make Atom works with Anaconda, you need to open Atom through the Anaconda propm using:

```
$ atom --new-instance
```

If you have an Anaconda virtual environment, In your Anaconda terminal, activate your Conda environment and then run `atom --new-instance`.

Now create a `test.py` file like that using Atom:
```python
print("Hello Word!")
```
Now open a terminal inside Atom using `platformio-ide-terminal`. The Windows CMD terminal will open. To run the `test.py` using the Windows terminal just write:

```
$ ipython
``` 
The output is:
```
Hello Word!
```
So far so good, but we want to run interactively Python code inside Atom.  To do that, just install Atom `Hydrogen` package using the Windows CMD console as administrator:
```
$ apm install hydrogen
```
Close and reopen using the Anaconda prop:
```
$ atom --new-instance
```
Now run that line of code using CTRL+ENTER and you get something like that:

```python
print("Hello Word!") Hello Word!
```
Now `hydrogen` package works!

### Reference

- [Using anaconda environment in Atom](https://stackoverflow.com/questions/43207427/using-anaconda-environment-in-atom)
- [Hydrogen installation guide]([https://nteract.gitbooks.io/hydrogen/docs/Installation.html](https://nteract.gitbooks.io/hydrogen/docs/Installation.html))

### Change terminal in Atom-editor's Platformio-Ide-Terminal on Windows

Open the Settings of the `platformio-ide-terminal` package:

![xzdf](https://github.com/markeyser/Data-Science-Cookbook/blob/master/imgs/Platformio-Ide-Terminal-01.png?raw=true)
Replace the default shell by git bash:
![xzdf](https://github.com/markeyser/Data-Science-Cookbook/blob/master/imgs/Platformio-Ide-Terminal-02.png?raw=true)
Replace with:

```
C:\Program Files\Git\bin\bash.exe
```

Now open the terminal:
![xzdf](https://github.com/markeyser/Data-Science-Cookbook/blob/master/imgs/Platformio-Ide-Terminal-03.png?raw=true)
The terminal now is using Git Bash instead Windows Console.

Reference:

- [Change terminal in Atom-editor's Platformio-Ide-Terminal on Windows](https://stackoverflow.com/questions/42277302/change-terminal-in-atom-editors-platformio-ide-terminal-on-windows)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0MzI2MzM5OTMsLTM3MjAyOTM5MCwtMT
kxMTcyNTc0LDkyOTgxNDQ5MSwxNTk5NjQ3ODYxXX0=
-->