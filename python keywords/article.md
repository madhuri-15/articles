### Article Link
[Python Basics — Keywords, All you need to know!](https://medium.com/@madhuri15/python-basics-keywords-all-you-need-to-know-275ba48970a5)

### Code 
```python
>>> help()
help> keywords
Here is a list of the Python keywords.  Enter any keyword to get more help.

False               class               from                or
None                continue            global              pass
True                def                 if                  raise
and                 del                 import              return
as                  elif                in                  try
assert              else                is                  while
async               except              lambda              with
await               finally             nonlocal            yield
break               for                 not         
```

> ***True, False***

```python
>>> 1 == 1
True
>>> 1 == 2
False
```

> ***None***
```python
def function(a, b):
    if a > b:
        print(a)
        
print(function(1, 4))
# Output: None
```
> ***and, or, not, is, in***
```python
x = 2
y = 5

# AND Operator
print(x > 1 and x < y)
# output: True

# OR Operator
print(x > 1 or x > y)
# output: True

# NOT  Operator
print(not(x > 1))
```
```python
# is 
x = 2
y = 2
print(x is y)
# ouptut: True

# in
list_ = [1, 2, 3, 4]
print(1 in list_)
# output: True

print(20 in list_)
# output: False
```
> ***if, else, elif, for, while, break, continue***
```python
# To check if given value of x is multiple of 3 or 5 or both.
x = 47

if x%3==0 and x%5==0:
    print("x is multiple of both 3 and 5.")
elif x%3==0:
    print("x is multiple of 3.")
elif x%5==0:
    print("x is multiple of 5.")
else:
    print("x is neither a multiple of 3 nor 5.")
```
```python
## for loop
for i in range(1, 10):
   print(i, end=" ")
# output: 1 2 3 4 5 6 7 8 9

## while loop
i = 1
while i < 10:
    print(i, end=" ")
    i = i+1
# output: 1 2 3 4 5 6 7 8 9
```
```python
## break
for i in range(1, 10):
    if i == 5:
        break
    print(i, end=" ")
# output: 1 2 3 4

## continue
for i in range(1, 10):
    if i == 5:
        continue
    print(i, end=" ")
# output: 1 2 3 4 5 6 7 8 9
```
> ***def, lambda, class, pass with***
```python
# function definition
def function_name():
    statements...
    
# lambda function
f = lambda x : x**2
print(f(4))
# output: 16

# class
class MyClass:
    def class_method1(self):
        statements...
        
    def class_method2(self):
        statements...
```
```python
# pass
def function_name():
    pass
    
class ClassName:
    pass
```
```python  
# with
with open('example.txt', 'r') as f:
    f.read()
    
print(f.closed())
# output: True
```
> ***return, yield***
```python
# return
def func(a):
    return a*10
print(func(5))
# output: 50

# yeild
def func(a):
    for i in range(10):
        yeild a*i
# generator object
gen_func = func(5)

print(next(gen_func)) # 1st iteration
# output: 0

print(next(gen_func)) # 2nd iteration
# output: 5

print(next(gen_func)) # 3rd iteration
# output: 10
```
> ***import, from, as***
```python
# import
import math

# from .. import ..
from math import sqrt

# as
import math as m
print(m.sqrt(25))
# output: 5
```
> ***try, except, raise, finally***

```
# try...except
def zero_division(a, b):
    try:
        result = a/b
    except ZeroDivisionError:
        return "Enter value greater than 0"
    return a / b
    
print(zero_division(1, 3))
# output: 0.3333

print(zero_division(1, 0))
# output: Enter value greater than 0
```
```python
# raise
if n == 0:
    raise ZeroDivisionError("Cannot divide")
```
> ***del, global, nonlocal***
```python
# del
>>> a = 5
>>> a
5

>>> del a
>>> a
Traceback (most recent call last):
  File "<pyshell>", line 1, in <module>
    a
NameError: name 'a' is not defined
```
```python
# global
var = 4

def function1():
    global var
    var = 5
    
def function2():
    var = 10
    
print(var) 
# output: 4

# function call
function1()
print(var)   # output: 5

function2()
print(var)   # output: 5
```

```python
# without nonlocal
def outer_func():
   a = 10
   def inner_func():
       a = 20
   inner_func()
   return a

print(output_func()) # 10

# nonlocal
def outer_func():
    a = 10
    def inner_func():
        nonlocal a
        a = 20
    inner_func()
    return a
 print(output_func()) # 20
````
> ***assert***
```python
>>> a = -1
>>> assert a < 0
>>> assert a > 0, "value must be positive"
Traceback (most recent call last):
  File "<pyshell>", line 1, in <module>
    assert a > 0, "value must be positive"
AssertionError: value must be positive
```





