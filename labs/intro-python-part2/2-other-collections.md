# Step 2: Other Python collections

In addition to the native data structures, Python also includes a [`collections` module](https://docs.python.org/3/library/collections.html) in the Standard Library, which includes additional collections with even more "batteries included" goodness.

If you ever find yourself thinking, "this Python thing almost does what I want, but I need it to also do ____.  Surely others have had this same need," _check the docs!_  More often than you would expect, you will find that others have had the same need, and there is indeed some library or tool that will help you do exactly what you need - _or at least something "close enough."_

| Collection                                                                                | Description |
|:------------------------------------------------------------------------------------------|:--|
| [namedtuple()](https://docs.python.org/3/library/collections.html#collections.namedtuple) | factory function for creating tuple subclasses with named fields |
| [deque](https://docs.python.org/3/library/collections.html#collections.deque)             | list-like container with fast appends and pops on either end |
| [ChainMap](https://docs.python.org/3/library/collections.html#collections.ChainMap)       | dict-like class for creating a single view of multiple mappings |
| [Counter](https://docs.python.org/3/library/collections.html#collections.Counter)         | dict subclass for counting hashable objects |
| [OrderedDict](https://docs.python.org/3/library/collections.html#collections.OrderedDict) | dict subclass that remembers the order entries were added |
| [defaultdict](https://docs.python.org/3/library/collections.html#collections.defaultdict) | dict subclass that calls a factory function to supply missing values |
| [UserDict](https://docs.python.org/3/library/collections.html#collections.UserDict)       | wrapper around dictionary objects for easier dict subclassing |
| [UserList](https://docs.python.org/3/library/collections.html#collections.UserList)       | wrapper around list objects for easier list subclassing |
| [UserString](https://docs.python.org/3/library/collections.html#collections.UserString)   | wrapper around string objects for easier string subclassing |

_Table Source: [docs.python.org](https://docs.python.org/3/library/collections.html)_

The good news is, that the basic skills you developed in the previous step in learning to work with Python's native data structures will serve you well in working with these additional collections. For example, let's see how your skills apply to working with the `OrderedDict` collection.

### OrderedDict Collection

Ordered Dictionaries work almost exactly like the native `dict` data structure, with one enhancement:  _they maintain the order of the items added to them._

Since this collection isn't a _native_ data structure, but one that is included in the Standard Library (meaning it should be installed and available on every computer that has a recent enough version of Python installed), we do have to `import` it into our script to enable us to use it - we'll learn more about imports shortly.

Check out this example of using an `OrderedDict`. This is doing the exact same thing we did with the `dict` example in the previous step.

```python
>>> from collections import OrderedDict
>>> od = OrderedDict()
>>> od["apples"] = 5
>>> od["pears"] = 2
>>> od["oranges"] = 9
>>>
>>> od["pears"]
2
>>> od["bananas"] = 12
>>> od
OrderedDict([('apples', 5), ('pears', 2), ('oranges', 9), ('bananas', 12)])
```

This `OrderedDict` worked just like the `dict` data structure with the following differences:

1. We did have to `import` it before we could use it.
2. We added the key-value pairs to it incrementally, to demonstrate how it maintains the order in which they were added.
3. When you look at the contents of the `OrderedDict` it looks a little different `OrderedDict(<list of tuples>)`.

Other than these differences, they work exactly the same.

**Next: Python loops**
