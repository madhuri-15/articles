### Article Link
[Python Basics — Variables](https://medium.com/@madhuri15/python-variables-bc14437368b0)

### Code
```python
# valid identifiers
variable1
_variable2
variable_3

# invalid identifiers
$variable1
2_variable
variable#3

```
``` python
# How to create a variable?
>>> a = 10

>>> 0 = x
SyntaxError: can't assign to literal.


# Multiple assignment
>>> a, b, c = 1, 2, 3
>>> print(a, b, c)
1 2 3

>>> a = 10
>>> print(a)
10
>>> a = 'Python'
>>> print(a)
Python

# Type casting
# a = '10'
>>> a = str(10)

# b = 10
>>> b = int(10)

# c = 10.0
>>> c = float(10)

>>> type(c)
<class 'float'>

# Deleting a variable
>>> print(a, b, c)
1 2 3
# delete a single variable
>>> del a
# Access deleted variable `a`
>>> a
    a
NameError: name 'a' is not defined.

# delete multitple variables
>>> del a, b, c
>>> a, b, c
    a, b, c
NameError: name 'a' is not defined
```
