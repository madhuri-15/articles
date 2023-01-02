### Article link
[Python Sequence Lists a complete guide](https://medium.com/mlearning-ai/python-sequence-lists-a-complete-guide-54ec7ed88323)

### Code

#### How to create a list
```python
# Creating a list
numbers = [1, 2, 3, 4]

# Creating a empty list
empty_list = []

# empty list using `list()` built-in function.
empty_list = list()

# Converting string type in list using `list()`
string_val = "Python"
char_list = list(string_val)

print(char_list)
# output - ['P', 'y', 't', 'h', 'o', 'n']

# list with mixed data types
names = ['John', 'David', 'Liam', 'Joy']
ids = (1, 2, 3, 4)
users = [names, ids, 13.4]
```
#### How to access elements from a list
```python
# Access elements using index
>>> a = [11, 22, 33]

# Index of first element
>>> a.index(11)
0

# To get the length of list `a`
>>> len(a)
3

>>> a[0]
11

""" 
The length of list `a` is 3, index of the list is 0, 1, 2. 
If you try to access value at index 3, which is not present in list `a`,
Then Python will raise indexError.
"""
>>> a[3]
Traceback (most recent call last):
  File "<pyshell>", line 1, in <module>
    a[3]
IndexError: list index out of range

# Let's try to access element of list using float type instead of integer.
>>> a[1.0]
Traceback (most recent call last):
  File "<pyshell>", line 1, in <module>
    a[1.0]
TypeError: list indices must be integers or slices, not float

# Negative indexing
>>> a[-1]
33

>>> a[-3]
11

# Accessing elements using slicing from list a
a = [11, 22, 33, 44, 55]

# Returns entire list
>>> a[:]  
[11, 22, 33, 44, 55]

# Return all values from index 2
>>> a[2:]
[33, 44, 55]

# Return all values with step 2
>>> a[::2]
[11, 33, 55]
```
#### Updating List
```python
# Create a list 
>>> a = [1, 2, 3, 4, 5]

# Update the first element.
>>> a[0] = 10
>>> a
[10, 2, 3, 4, 5]

# Update first three elements using slicing
>>> a[:3] = [11, 22, 33]
>>> a
[11, 22, 33, 4, 5]

# Appending single number
>>> a = [1, 2, 3]
>>> x = 10
>>> a.append(x)
>>> a
[1, 2, 3, 10]

# Appending single item - list
>>> x = ['a', 'b']
>>> a.append(x)
>>> a 
[1, 2, 3, 10, ['a', 'b']]

>>> b = ['a', 'b', 'c']
>>> b.extend(['d', 'e'])
>>> b
['a', 'b', 'c', 'd', 'e']

# A single value
>>> c = [0.5, 1.0, 1.5, 2.5]
>>> c.insert(3, 2.2)
>>> c 
[0.5, 1.0, 1.5, 2.2, 2.5]

# iterable
>>> c.insert(1, (0.7, 0.8))
>>> c 
[0.5, (0.7, 0.8), 1.0, 1.5, 2.2, 2.5]

>>> a = [1, 2, 3]
>>> b = [10, 20]
>>> a + b
[1, 2, 3, 10, 20]

>>> ['Hello'] * 3
['Hello', 'Hello', 'Hello']
```
#### Deleting List items
```python
>>> a = [1, 2, 3]
>>> a.remove(2)
>>> a
[1, 3]

>>> a = ['a', 'b', 'c', 'd']
>>> a.pop(1)
'b'
>>> a.pop()
'd'

# using clear() method
>>> a = [1, 2, 3]
>>> a.clear()
>>> a
[]

# using del to delete list
>>> a = [1, 2, 3, 4]

>>> del a[0]
>>> a
[2, 3, 4]

>>> del a[:2]
>>> a
[4]

>>> del a
Traceback (most recent call last):
  File "<pyshell>", line 1, in <module>
    a
NameError: name 'a' is not defined
```
#### List Comprehensions
```python
# Creating a list of using for loop
>>> squares = []
>>> for n in range(5):
...    squares.append(n**2)
...
>>> squares
[0, 1, 4, 9, 16]

# Using list comprehension
>>> squares = [n**2 for n in range(5)]
>>> squares
[0, 1, 4, 9, 16]

# List comprehension with certain condition.
"""
Create list of even number in given range.
"""
>>> evens = [x for x in range(1, 10) if x%2==0]
>>> evens
[2, 4, 6, 8]
```

#### Map function
```python
>>> def add10(n):
...    return n+10

>>> a = [1, 2, 3, 4]
>>> map(add10, a)
<map object at 0x00>
>>> list(map(add10, a)
[11, 12, 13, 14]
```

#### Filter function
```python
>>> def gt3(n):
...    return n > 3

>>> a = [1, 2, 3, 4, 5, 6]
>>> filter(gt3, a)
<filter object at 0x00>
>>> list(fiter(gt3, a))
[4, 5, 6]
```

#### List methods
- count()
```python
>>> a = [1, 2, 2, 3, 4, 2]

# Count the value 2 in list.
>>> a.count(2)
3
# Count the value 6 in list.
>>> a.count(6)
0
```

- reverse()
```python
>>> a = [1, 2, 3, 4]
>>> a.reverse()
>>> a
[4, 3, 2, 1]
```

- sort
```python
>>> a = [3, 1, 2, 5, 6]
>>> a.sort()
>>> a
[1, 2, 3, 5, 6]

# Using reverse
>>> a.sort(reverse=True)
>>> a
[6, 5, 3, 2, 1]
```

- copy()
```python
# without copy() function
>>> a = [1, 2, 3]
>>> b = a
>>> b
[1, 2, 3]

>>> b[0] = 10
>>> b
[10, 2, 3]
>>> a
[10, 2, 3]

# With copy() function
>>> a = [10, 20, 30]
>>> c = a.copy()
>>> c[0] = 1
>>> c
[1, 20, 30]
>>> a 
[10, 20, 30]
```

- min() & max() 
```python
# Use min() function to find a minimum value of the list.
>>> a = [1.2, 1.102, 0.98]
>>> min(a)
0.98

# Use max() function to find a maximum value of the list.
>>> max(a)
1.2
```
























