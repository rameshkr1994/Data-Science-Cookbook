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



127.0.0.1:5000
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExMjM0OTQzMDAsOTk0ODE4MDE2LDkyNT
E0MDk5MiwxMzExNTEzNzMsNjc1NjYxNDQyXX0=
-->