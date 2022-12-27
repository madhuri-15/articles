# Sorting Techniques in Python
As a programmer, you must have written code to sort data at some time. Sorting data can be a critical task to do; whether sorting numbers in a particular order or sorting strings in an alphabetical manner. Python has methods to sort data in a single line without using loops. But, As a newbie, you must have been confused at some time while sorting data since Python provides two sorting methods `sort()` and `sorted()`. If yes, then this article will guide you to understand the sorting techniques of Python in simple ways.
This article will help you to understand how to use sort() and sorted() methods using different parameters to simplify the complex sorting of sequential data so, let's get started.
Python lists have a built-in list.sort() method that modifies the list in place and another built-in function is sorted() function that builds a new sorted list from an iterable.
I Difference between sort() and sorted()
list.sort() can be used to sort a list and can not be used on other iterables. It sorts' the list in place and returns None , meaning it modifies and overwrites the original list.
The sorted() method can also be used on other Python iterables such as tuples, strings, dictionaries, or sets. This method returns a new sorted list type and does not modify the original sequence type.

II Sorting Basics
A simple ascending sort is easy as by default both sort() and sorted() methods, sort the data in ascending order.
```
# using sort() built-in method.
>>> a = [4, 3, 2, 5, 1]
>>> a.sort()
>>> a
[1, 2, 3, 4, 5]
# Using sorted() method.
>>> b = [4, 3, 5, 6, 2]
>>> sorted(b)
[2, 3, 4, 5, 6]
```

list.sort() method is only defined for lists. However, you can use sorted() function for any iterable.
```
>>> t = ('b', 'e', 'a', 'd')
>>> t.sort()
Traceback (most recent call last):
  File " ", line 1, in 
    t.sort()
AttributeError: 'tuple' object has no attribute 'sort'
>>> sorted(t)
['a', 'b', 'd', 'e']
```

Have you noticed? sorted() function does not return sorted tuple but list sequence type. It always returns a list type irrespective of its input type. You can cast the input type on the sorted return object if you want to; as follows.
## III Key functions
Both sorting methods have key parameter to specify a function or other callable to be called on each element of the list before making comparisons. key parameter takes a single argument and returns a key to use for sorting purposes. This key function is called on each element of input only once, hence this technique of sorting using the key is fast.
Let's see the example of sorting using a key function; for example case-insensitive string comparison
```
>>> string = "This is test code"
# To sort words in the string in alphabetical order.
>>> sorted(string.split(" "), key=str.lower)
['code', 'is', 'test', 'This']
```
In the above code example, we pass a list of words from string and key with str.lower() function as a value.
Now, this key function is applied to each element or word in the list and then words compare with each other based on the Unicode Code Point(ASCII value) of the first letter in each string to determine ascending sort order. If the first letter is the same then they compare those words with the second letter and so on.
A common pattern to sort complex objects using some of the object's indices as keys.
When we sort the dictionary, it is sorted based on its index and returns a sorted index only. but what if we want to sort a dictionary by values this is when we can use the key function of the sorted method.
```
## Sort dictionary by values
>>> d = {2:'b', 1:'a', 4:'c', 3:'d'}
>>> sorted_d = sorted(d.items(), key= lambda x:x[1])

# Convert into dictionary
>>> dict(sorted_d)
{1:'a', 2:'b', 3:'d', 4:'c'}
```
Here, instead of the passing dictionary, we passed a list of tuples of (key, value) pair of dictionaries with a lambda function that takes values of the dictionary and sorts the dictionary in ascending order according to values.
## IV Ascending and Descending
By default, both methods sort the data in ascending order. To sort data in descending order we can use reverse parameter. Both sort() and sorted() methods accept the reverse parameter with boolean values.
```
## To sort data in descending order.
>>> students = [('John', 'A', 15), 
                ('Dave', 'B', 10), 
                ('Alice', 'B', 12)]

>>> sorted(students, key=lambda x:x[2])    # Sort by age
[('Dave', 'B', 10), ('Alice', 'B', 12), ('John', 'A', 15)]

## Sorting list of tuples students by age in descending order.
>>> sorted(students, key=lambda x:x[2], reverse=True)
[('John', 'A', 15), ('Alice', 'B', 12), ('Dave', 'B', 10)]
```

The same technique works for objects with named attributes.

for example:
```
class Student:
    def __init__(self, name, grade, age):
         self.age = age
         self.name = name
         self.grade = grade

    def __repr__(self):
        return repr((self.name, self.grade, self.age))

student_obj = [Student('John', 'A', 15), Student('Dave', 'B', 10), Student('Alice', 'B', 12)]

# Sort by age attribute
sorted(student_obj, key=lambda student: student.age)
# output: [('Dave', 'B', 10), ('Alice', 'B', 12), ('John', 'A', 15)]
```

## V Operator Module functions
Using lambda functions for the key parameter is very common but takes a long time for large data. We can do the same process in a much easier and faster way by using methods from the operator module such as itemgetter(), attrgetter() and methodcaller() functions.
```
>>> from opeator import itemgetter, attrgetter
>>> sorted(student_obj, key = itemgetter(2)) # Sort by age
[('Dave', 'B', 10), ('Alice', 'B', 12), ('John', 'A', 15)]

>>> sorted(student_obj, key = attrgetter('age'), reverse=True )
[('John', 'A', 15), ('Alice', 'B', 12), ('Dave', 'B', 10)]
    
## sorting with multiple levels such as sort by grade and age
>>> sorted(student_obj, key =attrgetter('grade', 'age'))
[('John', 'A', 15),  ('Dave', 'B', 10), ('Alice', 'B', 12]

```

## VI Complex sorting
Sorts are guaranteed to be stable. This means that when multiple records have the same key, their original order is preserved.
```
>>> data = [('red', 1), ('blue', 1), ('red', 2)]
>>> sorted(data, key=itemgetter(0))
[('blue', 1), ('red', 1), ('red', 2)]
```
Notice, how the two records for red retain their original order so that ('red', 1) is guaranteed to precede ('red', 2).

This wonderful property lets you build a complex sort in a series of sorting steps. for example: To sort students' data by descending grade and then ascending age, do the age sort first and then sort again using grade.
```
>>> s = sorted(student_obj, key=attrgetter('age')) # sort on secondary key
>>> sorted(s, key=attrgetter('grade'), reverse=True) # sort by grade, decending
[('Dave', 'B', 10), ('Alice', 'B', 12), ('John', 'A', 15)]
```

In summary: Both sort() and sorted() method can be used to sort elements in a similar manner if used properly with key and reverse parameters. However, both have different characteristics when output. So, you can use the sorted function when original data is retained otherwise you can use the sort method of the list if the data is a copy of original data or losing original data won't cause any issue.
Thank you for reading. I hope this article helps you to understand the sorting techniques of python using built-in functions.
