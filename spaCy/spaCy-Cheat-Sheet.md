> Written with [StackEdit](https://stackedit.io/).

#### Import the English language class
```python
# Import the English language class
from spacy.lang.en import English
```
#### Create the `nlp` object
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

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTgxMzM0NTM0OCwxMzExNTEzNzMsNjc1Nj
YxNDQyXX0=
-->