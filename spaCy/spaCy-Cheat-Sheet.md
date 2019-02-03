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
Load the small English modell:
```python
import spacy
# Load the small English model
nlp = spacy.load('en_core_web_sm')
```
### Predict Part-of-speech Tags
First, we load the small English model and receive and `nlp` object. 
```python
import spacy
# Load the small English model
nlp = spacy.load('en_core_web_sm')
# Process a text
doc = nlp("Shee ate the pizza")
# Iterate over the tokens
for token in doc:
    
    # Print the text and the predicted part-of-speech tag
    print(token.text, token.pos_)
```
output:
```
Shee PROPN
ate VERB
the DET
pizza NOUN
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
eyJoaXN0b3J5IjpbLTE2NjA3MjYzMTIsMTEyMTI5NDgxNywxOD
QzMjc0Mjk3LC0xNDYxODI1MTY1LC0xNDM4NzIxMTU1LC0xMTIz
NDk0MzAwLDk5NDgxODAxNiw5MjUxNDA5OTIsMTMxMTUxMzczLD
Y3NTY2MTQ0Ml19
-->