# Step 3: Input, output, and conditionals

In all of the sections in this step, please take a minute to experiment with the Python syntax in your interactive interpreter.  Write your own input statements, create some if blocks, define some functions... Explore! Your own creativity and getting your fingers on the keyboard is the best way to learn a language's basic syntax.

### Getting input

Need to prompt the user for some information?  Use the `input()` function.  It will display your prompt to the user and return their input, which you can assign to a variable.

```python
>>> answer = input("What is the air-speed velocity of an unladen swallow? ")
What is the air-speed velocity of an unladen swallow? Huh? I... I don't know that.
>>> answer
'Huh? I... I don't know that.'
```

> **Note:** The input function always returns a string (`str`) and it doesn't do any sort of validation - that is all up to you!

### Displaying output

Use the `print()` function to display output to the user. It accepts a variable number of parameters, converts them all to strings (`str`) and then joins them together with a space `" "` separator between each of the items.  This is a quick and easy way to combine several items and display the output to the user.

```python
>>> coconuts = 2
>>> print("I have", coconuts, "coconuts")
'I have 2 coconuts'
```

### Conditionals

With variables comes the possibility (likelihood) that you may not know what they point to, or perhaps you want to branch your code and take different paths based on some condition. That's why we have `if` and `elif` ("else if") statements.

_**Python `if` syntax:**_

```python
if expression_1:
    statements…
elif expression_2:
    statements…
else:
    statements…
```

> **Indentation is important!**  In Python, indentation is syntactically significant. Python uses indentation to identify the block of statements that are associated with a preceding statement. By [PEP8](https://www.python.org/dev/peps/pep-0008/) convention, indentation should be four (4) spaces. Most "Python aware" text editors and IDEs will automatically insert four spaces when you press the `Tab` key.

The above `if` syntax reads:

1. If `expression_1` is `True`, do the following block of indented statements
2. Else if `expression_2` is `True`, do the following block of indented statements
3. Else do the following block of indented statements

> **Note:** In this syntax, the expressions can be any Python expression that evaluates to a `True` or `False` value (see [Python Truth Value Testing](https://docs.python.org/2/library/stdtypes.html#truth-value-testing) for more details).

A conditional need not have all of these elements. You could have a single `if` statement, with some set of statements to run if it evaluates to `True`. You could have many else-if `elif` statements. You may only have one default or catch-all `else` statement.

> **Note:** Python evaluates the `if` and `elif` statements starting with the first and proceeding to the last. If any of expressions evaluate to `True`, it runs the block of statements associated with that `if`/`elif` clause and then skips the rest of the clauses and continues with the next statement after the if-block.

#### Comparison operators and logical expressions

| Comparison Operator | Meaning                  |
|:--------------------|:-------------------------|
| <                   | Less Than                |
| >                   | Greater Than             |
| <=                  | Less Than or Equal To    |
| >=                  | Greater Than or Equal To |
| ==                  | Equal To                 |
| !=                  | Not Equal To             |
| in                  | Contains Element         |

You can combine expressions with `and` or `or`. Negate an expression with `not`.

_Example:_

```python
>>> n = 5
>>> if n < 5:
...     print("n is less than five")
... elif n == 5:
...     print("n is equal to five")
... else:
...     print("n is greater than five")
...
n is equal to five
```

**Next: Functions**
