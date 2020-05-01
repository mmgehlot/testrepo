# Step 1: Native Python data structures

Python comes fully equipped with a full set of native data structures.  We are going to take a look at the three most commonly used data structures: lists, tuples, and dictionaries.

As you work through this step, open your Python interactive interpreter and try creating each of the data types.  Try accessing and updating individual elements of the collections.  As you move on to working with more complex programs and APIs (and the data they return), it is essential that you be comfortable with these basic concepts.

> NOTE: On Windows within `git-bash`, you need to use the command `python -i` to explicitly start the `i`nteractive interpreter.  

### Overview

| Name </br> `type()`     | Example                                   | Notes  |
|:------------------------|:------------------------------------------|:-------|
| `list`                  | `['a', 1, 18.2]`                          | * Ordered list of items </br> * Mutable (can be changed after created) </br> * Items can be different data types </br> * Can contain duplicate items |
| `tuple`                 | `('a', 1, 18.2)`                          | * Just like a list; except: </br> * Immutable (cannot be changed) |
|                         |                                           |        |
| dictionary </br> `dict` | `{"apples": 5, "pears": 2, "oranges": 9}` | * Unordered key-value pairs </br> * Keys don’t have to be same data type </br> * Values don’t have to be same data type </br> * Keys are unique; must be immutable |

#### Lists

Lists are roughly analogous to arrays in other programming languages; however, a Python list _can contain elements of different data types_.

You create a list by using square braces `[]` and separating the elements of the list with commas, like so:

```python
>>> l = ['a', 1, 18.2]
```

You can then access and update the elements within the list via the element's index, and like all good programming languages - indexes start at `0`.  You can also append items to a list with the `.append()` method.

```python
>>> l[2]
18.2
>>> l[2] = 20.4
>>> l
['a', 1, 20.4]
>>> l.append("new")
>>> l
['a', 1, 20.4, 'new']
```

There are several other "batteries included" methods natively available with lists - [learn more in the Python docs](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists).

#### Tuples

Tuples function almost exactly like lists with one major difference: _Immutability._  A list can be change (mutated) after it is created (add items, update items, remove items, etc.). A tuple is immutable, which means it cannot be changed after creation.

You create a tuple by using parentheses `()` and separating the elements of the tuples with commas. Accessing elements via indexing works just like it does with lists, though you cannot update an element of a tuple.

```python
>>> t = ('a', 1, 18.2)
>>> t[0]
'a'
```

#### Dictionaries

Dictionaries are analogous to "hashes" in some other languages. A dictionary is a data structure that stores simple key-value pairs. They make it very easy and fast to store and retrieve a value by supplying a key to be used as an _index_ for that value.

* **Values**: The values in a Python dictionary can be anything, and like lists the types don't have to be consistent.
* **Keys**: A dictionary's keys have an important restriction - _whatever you want to use as a key has to be **immutable** and **hash-able**_. This means that you could use a tuple as a key (immutable), but not a list (mutable). Also note that all of the basic data types that you learned about in _Intro to Python - Part 1_ (`int`, `float`, `bool`, `str`, `bytes`) are immutable and can be used as dictionary keys.

You create a dictionary by using curly braces `{}`, separating a key from its value with a colon `:`, and separating the key-value pairs with commas. You access and update elements using indexing; however instead of using numerical sequential index numbers, you use use the key as the index. You can add new elements simply by assigning a value to a new key.

> **Note:** Up to Python 3.6, a dictionary's key-value pairs were stored in unordered fashion. Python 3.6 introduced order of insertion preservation which has been declared to be an official part of the Python language spec in Python 3.7 and later.

```python
>>> d = {"apples": 5, "pears": 2, "oranges": 9}
>>> d["pears"]
2
>>> d["pears"] = 6
>>> d["bananas"] = 12
>>> d
{'apples': 5, 'pears': 6, 'bananas': 12, 'oranges': 9}
```

There are a number of "batteries included" methods available for dictionaries - [learn more in the Python docs](https://docs.python.org/3/library/stdtypes.html#typesmapping).

### Learn more

Learn more about the `list`, `tuple`, and `dict` Python data structures [in the Python docs](https://docs.python.org/3/tutorial/datastructures.html).

**Extra credit:**  Python has another native data structure: a `set`.  We didn't cover it here out of an effort to keep this lab focused on providing the basic skills needed to engage with the DevNet Learning Labs that depend on this foundational lab; however, sets are powerful and probably worth you knowing that they exist and [where to find out more about them](https://docs.python.org/3/tutorial/datastructures.html#sets).

**Next: Other Python collections**
