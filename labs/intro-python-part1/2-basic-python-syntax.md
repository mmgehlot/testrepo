# Step 2: Basic Python syntax

Now that you know how to use your interpreter, let's dive-in and start learning Python.

In all of the sections in this step, please take a minute to experiment with the Python syntax in your interactive shell.  You aren't going to break anything _(probably)_, and getting your hands on the syntax is the best way to learn it and get comfortable with it.  Don't feel like you have to type in any of our examples verbatim - try your own.  See what works and what doesn't - you'll learn from both.

### Basic data types

| Python </br> `type()` | Values                    |
|:----------------------|:--------------------------|
| `int`                 | -128, 0, 42               |
| `float`               | -1.12, 0, 3.14159         |
| `bool`                | True, False               |
| `str`                 | "Hello 😎"                |
| `bytes`               | b"Hello \xf0\x9f\x98\x8e" |

As you would expect, Python has a basic data type to store any value you need. It also has a full set of operators to work with these numeric and string types.

| Numeric Operators      | String Operators   |
|:-----------------------|:-------------------|
| `+` Addition           | `+` Concatenation  |
| `-` Subtraction        | `*` Multiplication |
| `*` Multiplication     |                    |
| `/` Division           |                    |
| `//` Floor Division    |                    |
| `%` Modulo (remainder) |                    |
| `**` Power             |                    |

Python is introspective. You can see what type of data something is with the `type()` function. For example, enterimng `type(3)` returns `<class 'int'>`. Can't remember what Python's string data type is called? Just ask it, `type("What is this?")` and it will tell you `<class 'str'>`.

_**Try playing with some of these in your interactive interpreter.**_

> **Note:** You could use the Python interactive shell as a powerful calculator. Python is used by mathematicians and scientists, and is capable of doing high-precision and complex mathematical operations (or you could use it to calculate the tip for your pizza order). Enter `2+2` and Python returns `4`.

#### Strings

In Python v3 all strings (`str`) are Unicode strings and therefore can store and work with multi-byte Unicode characters.  Note that not all Terminals or platforms support these extended character sets, so use them at your own risk, but Python supports them - hopefully everything else will catch up.

You can use any of the following to open and close a string:

* Single Quotes `' '`
* Double Quotes `" "`
* Triple Single Quotes `''' '''`
* Triple Double Quotes `""" """`

_Why all the options?_  The ability to use single or double quotes as string delineators makes it easier for you to create strings that may contain quotation marks.  For example, if you want to include double quotes inside your string, open and close the string with single quotes and vice versa.

```python
>>> 'KEEPER: "What is your favorite color?" GALAHAD: "Blue. No yel-- Auuuuuuuugh!"'
```

Without the option to use the other quotation mark style to open and close the string, you would have to `\` escape all the quotation marks inside the string.

_What about the triple quotes?_  These let your string break across lines, and cause the string to include `\n` newline characters everywhere where there are line breaks in the multiline string - essentially you can write multiline strings just by using the triple opening and closing quotes.

> **Note:** A triple-quoted string (`"""`) at the beginning of a Python file, function, or class has special meaning. These are called docstrings, and they are a great way to document what the Python file, function, or class does and how it should be used.

##### String operators

Working with strings in Python is easy.

Want to put two strings together (concatenate)?  Just add them.

```python
>>> "One" + "Two"
`OneTwo`
```

> **Note:** This doesn't insert any space between the strings. It simply joins the two strings together into a new string.

Weird enough, you can multiply strings. This is actually useful when, for example, you want to repeat a character a certain number of times.

```python
>>> "Abc" * 3
`AbcAbcAbc`
```

There are also some powerful "convenience" methods available with string objects (more on objects later):

* `"{}".format()`: The `.format()` method lets you insert named or unnamed placeholders `{}` in a string and then use the `.format()` method to insert values into those placeholders.
* `"".split()`: The `.split()` method lets you split a string into multiple strings using a separator that you provide as the delimiter.
* `"".join()`: The `.join()` method lets you put a sequence of strings together using, joining them with a separator that you provide.

_Examples:_

```python
>>> "Hi, my name is {}!".format("Chris")
'Hi, my name is Chris!'

>>> "Hi, my name is {name}, and I am a {what}!".format(name="Bob", what="coder")
'Hi, my name is Bob, and I am a coder!'

>>> "a b c".split(" ")
['a', 'b', 'c']

>>> ",".join(['a', 'b', 'c'])
'a,b,c'
```

### Defining variables

Python is **not** a _strongly typed_ language. That means, unlike some other languages, you don't have to _declare_ a variable before using it. Also, a variable name could point to one type of data one minute and then point to a different type of data another.

To define a variable in Python, simply use the assign `=` operator to assign a value to the variable name.

```python
>>> a = 3
>>> a
3
```

> **Note:** In the interactive interpreter, typing a variable name at the prompt and pressing `Enter` displays the current value of the variable. Also note that while this is a valid Python statement, if you only put a variable name on a line in your script, it won't display the output to the user. You have to use the `print()` function in a script to display output to the user (you learn how to do this shortly).

#### Variable names

* Cannot start with a number [0-9]
* Cannot conflict with a language keyword
* Can contain: [A-Za-z0-9_-]

> Recommendations for naming (variables, classes, functions, etc.) can be found in [PEP8](https://www.python.org/dev/peps/pep-0008/).

### Everything is an object!

In Python everything is an object. What does this mean? Unlike some languages that have different types of data (value types, structures, classes and objects, etc.), in Python everything is an object.

_What are objects, and what does this mean for me?_  I'm glad you asked.  Objects _(over simplified explanation)_ are purpose-built groupings of variables (called attributes) and functions (called methods) that work together to do something useful.

Creating your own classes of objects in Python is easy, but due to time constraints and the fact that you won't need to create your own classes to complete the labs that depend on this _Python Fundamentals_ module, we aren't going to cover classes here. However, you do need to know how to work with objects - especially since _"everything is an object"_.  Fortunately doing so is also straightforward, and you have already seen this in action in the string examples above.

**To access the attributes (variables) or methods (functions) contained within an object, all you need to remember is that you use "." _dot-syntax_ to do so.** Putting a period (dot) after any object lets you access the attributes and methods available within the object.

_Examples:_

```python
>>> a = 57
>>> a.bit_length()
6
>>> "WhO wRoTe THIs?".lower()
'who wrote this?'
```

> **Note:** Python is introspective. To look inside an object and see what names (attributes and methods) are defined inside it, just pass the object to the `dir(<object>)` function.

**Next: Input, output, and conditionals**
