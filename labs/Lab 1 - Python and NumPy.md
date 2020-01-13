---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Name(s)
Ryan Solorzano


**Instructions:** This is an individual assignment, but you may discuss your code with your neighbors.


# Python and NumPy

While other IDEs exist for Python development and for data science related activities, one of the most popular environments is Jupyter Notebooks.

This lab is not intended to teach you everything you will use in this course. Instead, it is designed to give you exposure to some critical components from NumPy that we will rely upon routinely.

## Exercise 0
Please read and reference the following as your progress through this course. 

* [What is the Jupyter Notebook?](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.ipynb#)
* [Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Notebook Basics](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)

**In the space provided below, what are three things that still remain unclear or need further explanation?**


N/A


## Exercises 1-7
For the following exercises please read the Python appendix in the Marsland textbook and answer problems A.1-A.7 in the space provided below.


## Exercise 1

```python
# YOUR SOLUTION HERE
# a = [[2 for i in range(6)] for i in range(4)]
import numpy as np
a = np.full((6,4), 2)
print(a)
```

```python
## Exercise 2
```

```python
# YOUR SOLUTION HERE
b = np.ones((6,4), int)
np.fill_diagonal(b, 3)
print(a)
```

## Exercise 3

```python
# YOUR SOLUTION HERE
# Multiplies each element across the array i.e. A[0,0] is multiplied by B[0,0].
# Not true matrix multiplication
print(a * b)
# Is meant to be true matrix multiplication, and a 6x4 array cannot be
# multiplied by another 6x4 since the number of columns of the first array 
# does not equal the number of rows of the second, so matrix multiplication
# is impossible
# print(np.dot(a, b))
```

## Exercise 4

```python
# YOUR SOLUTION HERE
print(np.dot(a.transpose(), b))
print(np.dot(a, b.transpose()))
# The first matrix multiplication multiplies 4x6 matrix with a 6x4 matrix, which results in a 4x4 array
# The second matrix multiplication multiplies a 6x4 matrix with a 4x6 matrix, which results in a 6x6 array
# The difference comes with the nature of matrix multiplication
```

## Exercise 5

```python
# YOUR SOLUTION HERE
print("Hello World!")
```

## Exercise 6

```python
# YOUR SOLUTION HERE
c = np.random.rand(1000) 
d = np.random.randn(1000) 
e = np.random.normal(20, 5, 1000) 
f = np.random.uniform(-100, 100, 1000) 
g = np.random.randint(-10, 20, 1000) 

print("sum", np.sum(c), "mean", np.mean(c), "standard deviation", np.std(c))
print("sum", np.sum(d), "mean", np.mean(d), "standard deviation", np.std(d))
print("sum", np.sum(e), "mean", np.mean(e), "standard deviation", np.std(e))
print("sum", np.sum(f), "mean", np.mean(f), "standard deviation", np.std(f))
print("sum", np.sum(g), "mean", np.mean(g), "standard deviation", np.std(g))
```

## Exercise 7

```python
# YOUR SOLUTION HERE
import numpy as np
def count(arr, value):
    count = 0
    for idx in arr:
        count = count + 1 if idx == value else count
    return count

h = np.random.randint(0,1000,10000)
print(count(h, 1))
print(len(np.where(h == 1)[0]))
```

## Excercises 8-???
While the Marsland book avoids using another popular package called Pandas, we will use it at times throughout this course. Please read and study [10 minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html) before proceeding to any of the exercises below.


## Exercise 8
Repeat exercise A.1 from Marsland, but create a Pandas DataFrame instead of a NumPy array.

```python
# YOUR SOLUTION HERE
import pandas as pd

i = pd.DataFrame(np.full((6,4), 2))
print(i)
```

## Exercise 9
Repeat exercise A.2 using a DataFrame instead.

```python
# YOUR SOLUTION HERE
j = pd.DataFrame(np.ones((6,4)))
j.iloc[range(4), range(4)] = 3
j
```

## Exercise 10
Repeat exercise A.3 using DataFrames instead.

```python
# YOUR SOLUTION HERE
print (i * j)
# Below code will throw a ValueError since dimensions don't match
# print (pd.DataFrame.dot(i, j))
```

## Exercise 11
Repeat exercise A.7 using a dataframe.

```python
# YOUR SOLUTION HERE
def count(arr, value):
    count = 0
    for idx,rows in arr.iterrows():
        count = count + 1 if rows[0] == value else count
    return count

k = pd.DataFrame(np.random.randint(0,1000,10000))
print(count(k, 1))
print(len(np.where(k == 1)[0]))
```

## Exercises 12-14
Now let's look at a real dataset, and talk about ``.loc``. For this exercise, we will use the popular Titanic dataset from Kaggle. Here is some sample code to read it into a dataframe.

```python
titanic_df = pd.read_csv(
    "https://raw.githubusercontent.com/dlsun/data-science-book/master/data/titanic.csv"
)
titanic_df
```

Notice how we have nice headers and mixed datatypes? That is one of the reasons we might use Pandas. Please refresh your memory by looking at the 10 minutes to Pandas again, but then answer the following.


## Exercise 12
How do you select the ``name`` column without using .iloc?

```python
## YOUR SOLUTION HERE
titanic_df['name']
```

## Exercise 13
After setting the index to ``sex``, how do you select all passengers that are ``female``? And how many female passengers are there?

```python
## YOUR SOLUTION HERE
titanic_df.set_index('sex', inplace=True)
titanic_df.loc['female']
```

## Exercise 14
How do you reset the index?

```python
## YOUR SOLUTION HERE
titanic_df.reset_index(inplace=True)
titanic_df
```

```python

```
