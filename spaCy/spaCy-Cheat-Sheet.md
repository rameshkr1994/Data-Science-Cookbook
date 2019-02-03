> Written with [StackEdit](https://stackedit.io/).

#### Import the English language class
```python
# Import the English language class
from spacy.lang.en import English
```
#### Create the `Nlp` object
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
To get a token at a specific posiiton, you can index into the `doc`:
```python
# Index into the Doc to get a single Token
token = doc[1]
```
### Visualizing Part of Speech

```python
from spacy import displacy
displacy.serve(doc, style='dep')
```
Output:
127.0.0.1:5000
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0Mzg3MjExNTUsLTExMjM0OTQzMDAsOT
k0ODE4MDE2LDkyNTE0MDk5MiwxMzExNTEzNzMsNjc1NjYxNDQy
XX0=
-->