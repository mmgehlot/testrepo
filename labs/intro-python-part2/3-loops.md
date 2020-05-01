# Step 3: Python Loops

As you work through this step, open your Python interactive interpreter and experiment with creating `for` loops and `while` loops.

### Iterative loops

In Python, `for` loops are so useful that many Python coders rarely use `while` loops. A `for` loop iterates through a sequence or collection, essentially taking one item at a time and running the block of statements until all of the items have been iterated through (or you manually `break` out of the loop from within the code block).

_**Python `for` loop syntax**_

```python
for individual_item in iterator:
    statements…
```

In this syntax `individual_item` is just a variable name of your choosing, and an `iterator` is something that can be iterated.  Many things can be iterated, but for our purposes you should know that lists, tuples, dictionaries, and range sequences can all be iterated.

_What is a range sequence?_  Python has a built-in `range()` function that creates sequences. You can use the range function to produce a sequence that has say five (5) items, which you could use if you wanted your loop to run five times.

```python
>>> for i in range(5):
...     print(i)
...
0
1
2
3
4
```

The `range()` function accepts a `start`, `stop`, and optional `step` argument so you can get fancy with the sequences it can generate.

#### Choosing Variable Names

You can make your code readable by choosing your variable names wisely:

```python
>>> names = ["chris", "iftach", "jay"]
>>> for name in names:
...     print(name)
...
chris
iftach
jay
```

By naming my list of names "names" (plural) and then choosing "name" (singular) as my loop variable, this code reads as follows: "Create a list of names. For each name in the names list, print the name," and that is just what it does.

#### Iterating Through a Dictionary

If you try to iterate through a dictionary, you might be surprised by the results.

```python
>>> fruit_inventory = {"apples": 5, "pears": 2, "oranges": 9}
>>> for fruit in fruit_inventory:
...     print(fruit)
...
oranges
apples
pears
```

_What happened to the values?_ They are still there.  It's just that the iterator for a dictionary only iterates over the dictionary's keys.

_What if I want both the key and the value?_ There is an `.items()` dictionary method that will yield the key-value pairs essentially as a list of tuples, and you could iterate through this.

```python
>>> list(fruit_inventory.items())
[('oranges', 9), ('apples', 5), ('pears', 2)]
>>> for fruit in fruit_inventory.items():
...     print(fruit)
...
('oranges', 9)
('apples', 5)
('pears', 2)
```

_That's a little better, but I actually want the keys assigned to one variable and the values to another._  **Solution:** Unpacking.

Python has a feature where you can assign a collection of items to a collection of variables - this is called unpacking.

```python
>>> a, b, c = [1, 2, 3]
>>> a
1
>>> b
2
>>> c
3
```

We can use unpacking to unpack those `(key, value)` tuples that the `.items()` method returns into variable names of our choosing.

```python
>>> for fruit, quantity in fruit_inventory.items():
...     print("You have {} {}.".format(quantity, fruit))
...
You have 5 apples.
You have 2 pears.
You have 9 oranges.
```

The use of dictionaries is pervasive when working with APIs, and being comfortable with how to iterate through their contents is an important skill.

### Conditional loops

Conditional loops (`while` loops in Python) evaluate an expression before each iteration of the loop. If the expression evaluates to `True`, the loop statements are executed. If the expression evaluates to `False`, the loop statements are not executed and the script continues with the first line after the loop block.

_**Python `while` loop syntax**_

```python
while expression:
    statements…
```

In this syntax, `expression` can be any Python expression that evaluates to a `True` or `False` value (see [Python Truth Value Testing](https://docs.python.org/2/library/stdtypes.html#truth-value-testing) for more details).

_Example_

```python
>>> i = 0
>>> while i < 5:
...     print(i)
...     i += 1
...
0
1
2
3
4
```

> **Note:** This example does the same thing as the `for i in range(5)` loop only with the added overhead of having to keep track of the `i` state variable. If I had forgotten to increment `i` in my loop (the `i += 1` statement), this loop would have been an infinite loop (if `i` never went above 4). These are just a couple of reasons why `for` loops are used more widely than `while` loops in Python. In many cases `for` loops are simply easier and less error prone.

As funny as it might look, `while True:` is one of the more popular uses for while loops - for when you really do want to create an infinite loop.

```python
>>> from time import sleep
>>> while True:
...     try:
...         print("Polling.")
...         # Poll some resource
...         sleep(1)
...     except KeyboardInterrupt:
...         break
...
Polling.
Polling.
Polling.
```

> **You can use `Ctrl-C to break out of infinite loops or hung scripts.**

**Next: Python script structure and execution**
