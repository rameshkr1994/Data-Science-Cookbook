## Python Questions & Answers

`1.`	Explain Python’s `zip()` function? What’s the output of the following code?

```PYTHON
list1 = ['A','B','C’]
list2 = [10,20,30]
zip(list1, list2)
```

**Answer:** 
```PYTHON
# results in a list of tuples say 
[('A',10),('B',20),('C',30)]
```

`zip()` function- it will take multiple lists say `list1`, `list2`, etc and transform them into a single list of tuples by taking the corresponding elements of the lists that are passed as parameters. Whenever the given lists are of different lengths, `zip` stops generating tuples when the first list ends.
<br><br/>
`2.`	Explain Python Lists? What’s the output of the following code?

```python
L = [2, 3, 5, 7]
L.append(11)
```

**Answer:** 

```python
# output 
[2, 3, 5, 7, 11]
```
Lists are the basic ordered and mutable data collection type in
Python. They can be defined with comma-separated values between
square brackets
<br><br/>
`3.`	What’s the output of the following code?

```python
L = [2, 3, 5, 7, 11]
L[:3]
```
**Answer:** 
```python
# output: 
[2, 3, 5]
```
`4.`	Explain Python Dictionaries? What’s the output of the following code?
```python
numbers = {'one':1, 'two':2, 'three':3}
numbers['two']
```
**Answer:** 
```python
# output: 
2
```
Dictionaries are extremely flexible mappings of keys to values, and form the basis of much of Python’s internal implementation. They can be created via a comma-separated list of key:value pairs within curly braces.

Items are accessed and set via the indexing syntax used for lists and tuples, except here the index is not a zero-based order but valid key in the dictionary.

Keep in mind that dictionaries do not maintain any sense of order for the input parameters; this is by design. This lack of ordering allows dictionaries to be implemented very efficiently, so that random element access is very fast, regardless of the size of the dictionary (if you’re curious how this works, read about the concept of a hash table).
<br><br/>
`5.`	What’s the output of the following code?
```python
for n in range(20):
    if n % 2 == 0:
        continue
    print(n, end=' ')
```
**Answer:** 
```python
# output 
1 3 5 7 9 11 13 15 17 19
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
**Answer:** 
```python
# output 
[1, 1, 2, 3, 5]
```
`7.`	What’s the output of the following code?
```python
N = 10 ** 12
for i in range(N):
    if i >= 10: break
    print(i, end=', ')
```
**Answer:** 
```python
# output 
0, 1, 2, 3, 4, 5, 6, 7, 8, 9,
```
`8.`	What’s the output of the following code?
```python
[(i, j) for i in range(2) for j in range(3)]
```
**Answer:** 
```python
# output 
[(0, 0), (0, 1), (0, 2), (1, 0), (1, 1), (1, 2)]
```
`9.`	What’s the output of the following code?
```python
email = re.compile('\w+@\w+\.[a-z]{3}')
text = "To email Guido, try guido@python.org \
or the older address guido@google.com."
email.findall(text)
```
**Answer:** 
```python
# output 
['guido@python.org', 'guido@google.com']
```
`10.`	What’s the output of the following code?
```python
regex = re.compile(r'\w\s\w')
regex.findall('the fox is 9 years old')
```
**Answer:** 
```python
# output 
['e f', 'x i', 's 9', 's o']
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
**Answer:** 
```python
# output
array([1, 2, 3, 4, 5, 6, 7, 8, 9])

array([[1, 2, 3],
       [4, 5, 6],
       [7, 8, 9]])

array([[1, 4, 7],
       [2, 5, 8],
       [3, 6, 9]])
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
**Answer:** 
```python
# output
[1 2 3]

6.0
```
The L1 norm of a vector can be calculated in NumPy using the norm() function with a
parameter to specify the norm order, in this case 1.

L1(v) = ||v||1 = |a1| + |a2| + |a3|
<br><br/>
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
**Answer:** 
This is an example of broadcasting one-dimensional array to two-dimensional array
```python
# output
[[2 4 6]
 [2 4 6]]
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
**Answer:** 
```python
array([[0, 0, 1],
       [1, 0, 0],
       [0, 0, 1],
       [0, 1, 0],
       [0, 0, 1]])
```
One-hot encoding allows us to turn nomial categorical data into features with numerical values, while not matematically imply any ordinal relationship between the classes.
<br><br/>
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
**Answer:** 
```python
C: 10
Coefficient of each feature: [[-0.0855264  -3.75409972  4.40427765  0.        ]]
Training accuracy: 1.0
Test accuracy: 1.0

C: 1
Coefficient of each feature: [[ 0.         -2.28800472  2.5766469   0.        ]]
Training accuracy: 1.0
Test accuracy: 1.0

C: 0.1
Coefficient of each feature: [[ 0.         -0.82310456  0.97171847  0.        ]]
Training accuracy: 1.0
Test accuracy: 1.0

C: 0.001
Coefficient of each feature: [[ 0.  0.  0.  0.]]
Training accuracy: 0.5
Test accuracy: 0.5
```
Logistic Regression With A `L1` Penalty With Various Regularization Strengths. This code shows the effect of the regularization parameter `C` on the coefficients and model accuracy. The usefulness of `L1` is that it can push feature coefficients to `0`, creating a method for feature selection. In the code below we run a logistic regression with a `L1` penalty four times, each time decreasing the value of `C`. We should expect that as `C `decreases, more coefficients become `0`.

Notice that as `C` decreases the model coefficients become smaller (for example from `4.36276075` when `C=10` to `0.0.97175097` when `C=0.1`), until at `C=0.001` all the coefficients are zero. This is the effect of the regularization penalty becoming more prominent.
<br><br/>
`16.`	What’s the output of the following code?
```python
df['elderly'] = np.where(df['age']>=50, 'yes', 'no')
```
**Answer:** Create a Column Based on a Conditional in pandas. Create a new column called `df.elderly` where the value is `yes`
if `df.age` is greater than `50` and `no` if not.
<br><br/>
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
**Answer:** `df.drop(['Cochice', 'Pima'])` drops two observations.`df.drop('reports', axis=1)` drops a variable (column).
<br><br/>
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
**Answer:** In the example below, we define a 3 x 6 sparse matrix as a dense array, convert it to a CSR sparse representation, and then convert it back to a dense array by calling the todense() function.
<br><br/>
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
**Answer:** 
```python
(3, 3, 3)
[[[ 1  2  3]
  [ 4  5  6]
  [ 7  8  9]]

 [[11 12 13]
  [14 15 16]
  [17 18 19]]

 [[21 22 23]
  [24 25 26]
  [27 28 29]]]
```
The example defines a 3x3x3 tensor as a `NumPy` ndarray. Three dimensions is easier to wrap your head around. Here, we first define rows, then a list of rows stacked as columns, then a list of columns stacked as levels in a cube.
<br><br/>
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
**Answer:** 
Feature extraction is another procedure that is susceptible to data leakage.

Like data preparation, feature extraction procedures must be restricted to the data in your training dataset.

The pipeline provides a handy tool called the FeatureUnion which allows the results of multiple feature selection and extraction procedures to be combined into a larger dataset on which a model can be trained. Importantly, all the feature extraction and the feature union occurs within each fold of the cross validation procedure.

The example demonstrates the pipeline defined with four steps:

1. Feature Extraction with Principal Component Analysis (3 features)
2. Feature Extraction with Statistical Selection (6 features)
3. Feature Union
4. Learn a Logistic Regression Model

The pipeline is then evaluated using 10-fold cross validation.



<!--stackedit_data:
eyJoaXN0b3J5IjpbMjEzNzAzOTY4OV19
-->