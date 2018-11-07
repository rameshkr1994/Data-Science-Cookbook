## Python Questions

`1.`	Explain Python’s `zip()` function? What’s the output of the following code?

```PYTHON
list1 = ['A','B','C’]
list2 = [10,20,30]
zip(list1, list2)
```
`2.`	Explain Python Lists. What’s the output of the following code?

```python
L = [2, 3, 5, 7]
L.append(11)
```
`3.`	What’s the output of the following code?

```python
L = [2, 3, 5, 7, 11]
L[:3]
```
`4.`	Explain Python Dictionaries? What’s the output of the following code?
```python
numbers = {'one':1, 'two':2, 'three':3}
numbers['two']
```
`5.`	What’s the output of the following code?
```python
for n in range(20):
    if n % 2 == 0:
        continue
    print(n, end=' ')
```
`6.`	What’s the output of the following code?
```python
def fibonacci(N, a=0, b=1):
    L = []
    while len(L) < N:
        a, b = b, a + b
        L.append(a)
    return L

fibonacci(5)
```
`7.`	What’s the output of the following code?
```python
N = 10 ** 12
for i in range(N):
    if i >= 10: break
    print(i, end=', ')
```
`8.`	What’s the output of the following code?
```python
[(i, j) for i in range(2) for j in range(3)]
```
`9.`	What’s the output of the following code?
```python
email = re.compile('\w+@\w+\.[a-z]{3}')
text = "To email Guido, try guido@python.org \
or the older address guido@google.com."
email.findall(text)
```
`10.`	What’s the output of the following code?
```python
regex = re.compile(r'\w\s\w')
regex.findall('the fox is 9 years old')
```
`11.`	What’s the output of the following code?
```python
import numpy as np
x = np.arange(1, 10)
x

M = x.reshape((3, 3))
M

M.T
```
`12.`	What’s the output of the following code?
```python
from numpy import array
from numpy.linalg import norm
# define vector
a = array([1, 2, 3])
print(a)
# calculate norm
l1 = norm(a, 1)
print(l1)
```
`13.`	What’s the output of the following code?
```python
from numpy import array
# define two-dimensional array
A = array([[1, 2, 3],
           [1, 2, 3]])
# define one-dimensional array
b = array([1, 2, 3])
C = A + b
print(C)
```
`14.`	What’s the output of the following code?
```python
# Load libraries
import numpy as np
import pandas as pd
from sklearn.preprocessing import LabelBinarizer

# Create NumPy array
x = np.array([['Texas'], 
              ['California'], 
              ['Texas'], 
              ['Delaware'], 
              ['Texas']])
              
# Create LabelBinzarizer object
one_hot = LabelBinarizer()

# One-hot encode data
one_hot.fit_transform(x)
```
`15.`	What’s the output of the following code?
```python
C = [10, 1, .1, .001]

for c in C:
    clf = LogisticRegression(penalty='l1', C=c)
    clf.fit(X_train, y_train)
    print('C:', c)
    print('Coefficient of each feature:', clf.coef_)
    print('Training accuracy:', clf.score(X_train, y_train))
    print('Test accuracy:', clf.score(X_test, y_test))
    print('')
```
`16.`	What’s the output of the following code?
```python
df['elderly'] = np.where(df['age']>=50, 'yes', 'no')
```
`17.`	What’s the output of the following code?
```python
import pandas as pd
data = {'name': ['Jason', 'Molly', 'Tina', 'Jake', 'Amy'], 
        'year': [2012, 2012, 2013, 2014, 2014], 
        'reports': [4, 24, 31, 2, 3]}
df = pd.DataFrame(data, index = ['Cochice', 'Pima', 'Santa Cruz', 'Maricopa', 'Yuma'])

df.drop(['Cochice', 'Pima'])
df.drop('reports', axis=1)
```
`18.`	Comment the following code:
```python
# dense to sparse
from numpy import array
from scipy.sparse import csr_matrix
# create dense matrix
A = array([[1, 0, 0, 1, 0, 0], [0, 0, 2, 0, 0, 1], [0, 0, 0, 2, 0, 0]])
print(A)
# convert to sparse matrix (CSR method)
S = csr_matrix(A)
print(S)
# reconstruct dense matrix
B = S.todense()
print(B)

Output:

[[1 0 0 1 0 0]
 [0 0 2 0 0 1]
 [0 0 0 2 0 0]]

  (0, 0)	1
  (0, 3)	1
  (1, 2)	2
  (1, 5)	1
  (2, 3)	2

[[1 0 0 1 0 0]
 [0 0 2 0 0 1]
 [0 0 0 2 0 0]]
```
`19.`	What is the output of the following code?:
```python
# create tensor
from numpy import array
T = array([
  [[1,2,3],    [4,5,6],    [7,8,9]],
  [[11,12,13], [14,15,16], [17,18,19]],
  [[21,22,23], [24,25,26], [27,28,29]],
  ])
print(T.shape)
print(T)
```
`20.`	Comment the following code:
```python
# Create a pipeline that extracts features from the data then creates a model
from pandas import read_csv
from sklearn.model_selection import KFold
from sklearn.model_selection import cross_val_score
from sklearn.pipeline import Pipeline
from sklearn.pipeline import FeatureUnion
from sklearn.linear_model import LogisticRegression
from sklearn.decomposition import PCA
from sklearn.feature_selection import SelectKBest
# load data
url = "https://raw.githubusercontent.com/jbrownlee/Datasets/master/pima-indians-diabetes.data.csv"
names = ['preg', 'plas', 'pres', 'skin', 'test', 'mass', 'pedi', 'age', 'class']
dataframe = read_csv(url, names=names)
array = dataframe.values
X = array[:,0:8]
Y = array[:,8]
# create feature union
features = []
features.append(('pca', PCA(n_components=3)))
features.append(('select_best', SelectKBest(k=6)))
feature_union = FeatureUnion(features)
# create pipeline
estimators = []
estimators.append(('feature_union', feature_union))
estimators.append(('logistic', LogisticRegression()))
model = Pipeline(estimators)
# evaluate pipeline
seed = 7
kfold = KFold(n_splits=10, random_state=seed)
results = cross_val_score(model, X, Y, cv=kfold)
print(results.mean())

Output: 0.776042378674
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM0OTYxNzk3OV19
-->