> Written with [StackEdit](https://stackedit.io/).

# Introduction to Python Text Basics

- Understand how to open a normal `.txt` and `.pdf` files with basic Python libraries.
- Learn some basic regular expressions.

## Working with text files with Python - Part One

### Write a `.txt` file using Jupyter and magic cells

####  The File Reading/Writing Process

Once you are comfortable working with folders and relative paths, you’ll be able to specify the location of files to read and write. The functions covered in the next few sections will apply to plaintext files.  _Plaintext files_  contain only basic text characters and do not include font, size, or color information. Text files with the  _.txt_  extension or Python script files with the  _.py_  extension are examples of plaintext files. These can be opened with Windows’s Notepad or OS X’s TextEdit application. Your programs can easily read the contents of plaintext files and treat them as an ordinary string value.

_Binary files_  are all other file types, such as word processing documents, PDFs, images, spreadsheets, and executable programs. If you open a binary file in Notepad or TextEdit, it will look like scrambled nonsense, like in  [Figure 8-5](https://automatetheboringstuff.com/chapter8/#calibre_link-86 "Figure 8-5. The Windows calc.exe program opened in Notepad").

![](https://automatetheboringstuff.com/images/000046.jpg)

Since every different type of binary file must be handled in its own way, this book will not go into reading and writing raw binary files directly. Fortunately, many modules make working with binary files easier—you will explore one of them, the  `shelve`  module, later in this chapter.

There are three steps to reading or writing files in Python.

1.  Call the  `open()`  function to return a  `File`  object.
    
2.  Call the  `read()`  or  `write()`  method on the  `File`  object.
    
3.  Close the file by calling the  `close()`  method on the  `File`  object.

[Reference](https://automatetheboringstuff.com/chapter8/)

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
content = myfile.read()
```
Print the content for example:
```python
content
```
the content is going to be this save string of the file:
```
'Hello, this is a quick test file.\nThis is the second line of the file.\n'
```
Content is going to be this save string of the file and since it has its backslash `\n` if ever what actually want to print the content:
```python
print(content)
```
output:
```
Hello, this is a quick test file.
This is the second line of the file.
```
Finally close always the file:
```python
myfile.close()
```
In summary, to read a file:
```python
myfile = open('test.txt')
content = myfile.read()
print(content)
myfile.close()
```
You can change the cursor to index position 0 which essentially resets the cursor:
```python
myfile.seek(0)
```
it would be nice if we could iterate through each line in the text file. Notice that each line is essentially segmented by this `\n`. Luckily Python actually has a `readline()` method in addition to the read method which will actually read in each line as a separate item in a python list:
```python
mylines = myfile.readlines()
mylines
```
output:
```
['Hello, this is a quick test file.\n',
 'This is the second line of the file.\n']
```
`mylines` object which is a list of every string are essentially every line as a string and then it could iterate through it:
```python
for line in mylines:
    print(line.split()[0])
```
output:
```
Hello,
This
```
>So `read()` is to grab everything as one giant string `readlines()` is the grab every line as a separate string for a list.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyOTkwMTMyMDMsMTAzMjMxNTc4NSwtNT
g4NzM1NTQ1LC0yMDQxNzEzNTYwXX0=
-->