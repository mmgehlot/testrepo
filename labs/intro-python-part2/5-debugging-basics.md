# Step 5: Debugging basics

If you are human, you are going to make mistakes (and discover the mistakes made  by other humans). When things go wrong, the Python interpreter actually provides pretty useful information about what happened - if you know how to read what it is telling you.

### How to read a stack trace

When an error occurs while running a Python script (and isn't handled or resolved by the script), it will be raised or "bubbled-up" and displayed to the user in the form of a "stack trace". A **stack trace** shows the calling "stack" of statements all the way from the top-level script that is being executed down to the statement that has produced the error.

If your script called a `main()` function, which in turn called a `create_fortune_cookie_message()` function, which raised or generated an error...

_Your "call stack" would be:_

![Call Stack](assets/images/call-stack.png)

_Your stack trace for the error would look something like:_

```python
 $ python intro-python/part2/fortune_cookie.py
Get your fortune cookie!
How many lucky numbers would you like?  5
Traceback (most recent call last):
  File "intro-python/part2/fortune_cookie.py", line 56, in <module>
    main()
  File "intro-python/part2/fortune_cookie.py", line 50, in main
    fortune_cookie_message = create_fortune_cookie_message(qty_lucky_numbers)
  File "intro-python/part2/fortune_cookie.py", line 38, in create_fortune_cookie_message
    raise NotImplementedError()
NotImplementedError
```

The stack trace starts with the line beginning with `Traceback` and ends with the generated error message (`NotImplementedError` in this example).

_How to read and understand what a stack trace is telling you:_

1. Read the **Last Line First**: This is "what went wrong." Often the error messages are clear and helpful, sometimes they aren't. Either way they should provide some hint as to what is going on.
2. Then review the call stack from **Top to Bottom**: This will show you where the error has occurred; starting with the top-level statement in the current script being executed through all of the nested function calls in the call stack down to where the error occurred. The details provided help you locate the calls and statements involved in the issue:
     * They tell where each statement is found (file and line number).
     * They display the statement for your reference.

> **Note:** When you are using functionality provided by a library or module (that you imported into your script), you will see calls that "leave" your code and start showing you calls within the imported module. For new coders, I recommend focusing only on the statements within your own code. It can be difficult to understand the logic of other developers, and they might be using more advanced or concise syntax than you are familiar with. Read, review, re-review, and debug your code first before you attempt to debug someone else's code.

Reading the above stack trace example, we can see that we have some sort of issue with something _not having been implemented_, and it looks to be within the `create_fortune_cookie_message()` function in our `intro-python/part2/fortune_cookie.py` file. We'll fix this error in the next hands-on exercise.

### Debugging your code

Advanced IDEs (Integrated Development Environments) have built-in debuggers that help you interactively debug and explore your code by pausing the execution of your code and letting you inspect the values of variables and incrementally step through the executing code; one statement at a time.  However, using an IDE's debugger is beyond the scope of this lab, and we can get quite a bit done using `print()` statements and Python's interactive shell.

#### Use `print` statements

_Want to know what the value of a variable is at some point in your script?_  Print it.

```python
print("DEBUG: a =", a)
```

_Having trouble understanding the flow of a script (what functions get called, in what order, how many times, and etc.)?_  Add some print statements.

```python
def my_function():
    print("==> Starting my_function()")
    ...
```

Sometimes what you intended when you wrote your code isn't what is happening when it is executed. By adding a print statement to the beginning (and maybe ending) of each function, with a descriptive message telling you where you are in your code, you can see the flow of your script as it runs.  You can also create descriptive print statements that show you the value of variables at key points in your code. Adding print statements like these gives you visibility into your code _at run time_.

> **Note:**  You can add visual prefixes like `==> ` or `DEBUG:` (or whatever you like) to the beginning of your debugging print statements to help visually  highlight them in the output of your script, and you can comment or uncomment the lines as needed to view or hide your debugging as you work with your code. To comment a line, just add a `#` to the beginning of the line.

#### Use the Python interactive shell

You can instruct the Python interpreter to run your script and then stay in the interactive shell by passing it the `-i` option when running your script.

```shell
$ python -i <script_name.py>
```

This will allow you to interactively test or experiment with your code by allowing you to:

* Call your functions.
* Inspect module-scope variables (remember that you can't access a locally scoped variable outside of its function).
* Incrementally build your code: run everything you have completed so far, and then use the interactive shell to figure out what you need to do next.
* Test out fixes to your code. Did you call a function incorrectly? How should you call it? Interactive testing in the interactive shell can help you figure out what your statements should be, and then you can go back and edit your code to incorporate the changes.

**Next: Hands-on exercise**
