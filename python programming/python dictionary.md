### Article link
[Python Mapper - Dictionary](https://medium.com/@madhuri15/python-mapper-dictionary-3860367cf64e)

```python
# To create empty dictionary.
empty_dict = {}

# Dictionary with mixed types.
student_dict = {'Name':'John', 'Age':12, 'Roll_no': 20, 'Grade':'A'}

# Using 'dict()' built-in function using list of tuples of key, values
squares = [(1, 1), (2, 4), (3, 9), (4, 16)]

squares = dict(squares)
print(squares)
# Output: {1: 1, 2: 4, 3: 9, 4: 16}


# Let's access the values of student dictionary.
>>> student_dict['Name']
'John'
>>> student_dict['Grade']
'A'

# We can create a nested dictionary
>>> students = {0:{'Name':'John', 'Age':12, 'Roll_no': 20, 'Grade':'A'},
                1:{'Name':'Liam', 'Age':12, 'Roll_no': 21, 'Grade':'B'},
                2:{'Name':'Emma', 'Age':11, 'Roll_no': 22, 'Grade':'A'}}

# To access nested dictionary
>>> students[2]['Roll_no']
22

>>> squares.get(4)
16
>>> squares.get(5)
None
>>> squares[5]
... 
KeyError: 5

# To update dictionary
>>> d = {0: 'a', 1: 'b', 2: 'c'}

# Updating the value of key 2
>>> d[2] = 'd'
>>> d
{0: 'a', 1: 'b', 2: 'd'}

# Adding new data.
>>> d[3] = 'e'
>>> d
{0: 'a', 1: 'b', 2: 'd', 3: 'e'}

>>> d = {}

# Update the dictionary using another dictionary.
>>> d.update({0:'a', 1: 'b'})
>>> d
{0:'a', 1: 'b'}

# Using iterable
>>> d.update(zip((1, 2, 3), ('c', 'd', 'e')))
>>> d
{0:'a', 1: 'c', 2:'d', 3:'e'}

# To delete elements using pop() method
>>> d.pop(0)
'a'

>>> d.pop(5)
Traceback (most recent call last):
  File "<pyshell>", line 1, in <module>
    d.pop(5)
KeyError: 5

>>> d
{1: 'c', 2:'d', 3:'e'}

>>> d.popitem()
(3, 'e')

>>> del d[2]
# To delete entire dictionary object.
>>> del d

>>> d.clear()
>>> d
{}

>>> d = {0:'a', 1: 'c', 2:'d', 3:'e'}

>>> for key in d:
        print(key, d[key])
0 a
1 c
2 d
3 e

>>> d.items()
[(0, 'a'), (1, 'c'), (2, 'd'), (3, 'e')]
>>> for key, value in d.items():
        print(key, value)
0 a
1 c
2 d
3 e

# Squares
>>> squares = {x : x**2 for x in range(1, 11)}
>>> squares 
{1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36, 7: 49, 8: 64, 9: 81, 10: 100}
```
