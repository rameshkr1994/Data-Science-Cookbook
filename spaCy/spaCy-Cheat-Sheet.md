> Written with [StackEdit](https://stackedit.io/).

### Import the English language class
```python
# Import the English language class
from spacy.lang.en import English
```
### Create the `Nlp` object
```python
# Create the nlp object
nlp = English()
```
### Create a `Doc` object
```python
# Created by processing a string of text with the nlp object
doc = nlp("Hello world!")
```
iterate over `Doc` tokens:
```python
# Itereate over tokens in a Doc
for token in doc:
    print(token.text)
```
output:
```
Hello
world
!
```
To get a token at a specific position, you can index into the `doc`:
```python
# Index into the Doc to get a single Token
token = doc[1]
```
### Load Model Packages (Statistical Models)
```python
import spacy
# Load the small English model
nlp = spacy.load('en_core_web_sm')
```
### Visualizing Part of Speech / Dependency / NER
On Jupyter Notebook / Lab use `render`:
```python
from spacy import displacy
displacy.render(doc,style='dep', jupyter=True)
```
To display on a browser use `serve`:
```python
from spacy import displacy
displacy.serve(doc, style='dep')
```
Output:
5000

And put `127.0.0.1:5000` on your browser.
Use this option if you are working on a text editor and not on Jupyter. You need to stop the Python 3 Kernel to stop serving on the browser (???).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAyNDA0Njc4MiwxMTIxMjk0ODE3LDE4ND
MyNzQyOTcsLTE0NjE4MjUxNjUsLTE0Mzg3MjExNTUsLTExMjM0
OTQzMDAsOTk0ODE4MDE2LDkyNTE0MDk5MiwxMzExNTEzNzMsNj
c1NjYxNDQyXX0=
-->