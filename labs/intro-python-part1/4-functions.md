# Step 4: Functions

_"Don't Repeat Yourself (DRY)"_

Find yourself writing blocks of identical or nearly identical code in several places throughout your script (or in several of your scripts)? It's time to create a **function**. Functions let you write a piece of code once, give it a name, and then call that piece of code whenever you need it. They can (optionally) accept input arguments and return an output allowing you to create operations that take some input(s) and return some output according to your needs.

_**Python function syntax:**_

```python
def function_name(arg_1, arg_2):
    statements...
    return value
```

> **Again indentation is important!**

You use the `def` keyword to define a function, and you must follow the same rules when naming functions as you do when naming variables:

* Cannot start with a number [0-9]
* Cannot conflict with a language keyword
* Can contain: [A-Za-z0-9_-]

> Recommendations for naming (variables, classes, functions, etc.) can be found in [PEP8](https://www.python.org/dev/peps/pep-0008/).

When defining a function, arguments are variable names that you create.  Later on when you call your function, you will pass in values for each of the arguments and these values will be assigned to the variable names you defined.  These variables can be used within the body of your function to do as you need to carry out the purpose of your function.

Your function may optionally `return` some value.

_Example:_

```python
def add(num1, num2):
...     result = num1 + num2
...     return result
...
>>>
>>> add(3, 5)
8
```

> **Note:** _Defining_ a function (`def`) only "creates" it for later use. Your  function's code doesn't actually run until you call it (see the `add()` example above). No addition was performed until we called the add function and supplied values for its arguments with the `add(3, 5)` statement. You typically define a function once and then call it many times; passing in arguments and getting outputs each time.

A function doesn't have to have any arguments or return any values. You could simply be calling a function to do some predefined set of actions.

```python
>>> def say_hello():
...     print("Hello!")
>>>
>>> say_hello()
Hello!
```

> **Note:** A function implicitly returns `None` if it reaches the end of the function's block of statements. `None` is a special Python _singleton_ value. It essentially means "no value." `None` is the closest thing Python has to a `null` value that is present in some other languages.

**Next: Hands-on exercise**
