


> Written with [StackEdit](https://stackedit.io/).

# Atom with R and Python

The best practice is creating a new conda virtual environment for each and new project. In this environment you need to install thow types of components:

- **First**: all you need to use Atom with that specific new virtual environment. Here you have two types of components
	- The kernels through the conda console as administrator
	- The Atom packages you need through the Windows CMD console as admin.
- **Second**: all Python packages and R packages you will need during the project. You install all these packages through the conda console as administrator.

> Note: using virtual environment is the only one realistic way to downgrade Anaconda Python 3.7 version (the latest one) to the NYL Python 3.6.5 version we are currently using at NYL. Trying to change Python version system wide doesn’t work like the second option [here](https://interviewbubble.com/how-to-downgrade-python-3-7-to-3-6-in-anaconda/). So, the only one realistic way to downgrade Python from 7.3 to 3.6.5 is via creation of a conda virtual environment like [here](https://stackoverflow.com/questions/53972362/how-to-downgrade-python-from-3-7-to-3-5-in-anaconda).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjExNzA4Mjk3NF19
-->