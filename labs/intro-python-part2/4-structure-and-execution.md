# Step 4: Python script structure and execution

When you call the Python interpreter and tell it to run a script, the interpreter does so "synchronously," meaning that it starts at the top of your script and goes line by line executing each statement one at a time. If a particular statement takes a while to compute or is waiting on a response from some external source (like making an API call and waiting on the response), Python stops and waits for the current statement to finish executing before moving on to the next one.

This makes understanding the flow of your script and how to troubleshoot it much easier as everything is predictably and sequentially loaded and executed.

This sequential execution also brings with it some considerations, such as the need to define a function before you can use it. Considerations like these have given rise to common patterns for structuring Python files.

> **Note:**  A Python file may be referred to by a couple of different names. It may be called a **script** (usually denoting that it is intended to be executed), or it may be called a **module** (denoting that its contents are meant to be imported and used by another calling script).

### Sample script

Take a look at the following sample script (`intro-python/part2/structure.py` in the sample code repository), then let's take a look at its structure and the Python interpreter's execution process running this script.

```python
#!/usr/bin/env python
# """Module docstring."""

# Imports
import os
import sys

# Module Constants
START_MESSAGE = "CLI Inspection Script"

# Module "Global" Variables
location = os.path.abspath(__file__)

# Module Functions and Classes
def main(*args):
    """My main script function.

    Displays the full patch to this script, and a list of the arguments passed
    to the script.
    """
    print(START_MESSAGE)
    print("Script Location:", location)
    print("Arguments Passed:", args)

# Check to see if this file is the "__main__" script being executed
if __name__ == '__main__':
    _, *script_args = sys.argv
    main(*script_args)
```

#### Structure and Execution

When we run this script with from the Terminal, the Python interpreter will start with the first line and execute each statement in succession.

**Flow:**

1. <em>The "<a href="https://en.wikipedia.org/wiki/Shebang_(Unix)">Shebang</a>" Line</em>: The first statement in many executable Python scripts isn't meant for the Python interpreter. This line tells the shell attempting to run the script what interpreter should be used to "execute" the script.

   ```python
   #!/usr/bin/env python
   ```

   The Python interpreter sees this line as a comment and ignores it.

2. _The Module Docstring_: The triple-quoted string at the beginning of this Python script is a [module docstring](https://www.python.org/dev/peps/pep-0257/#what-is-a-docstring), which serves as a built-in mechanism for documenting the purpose-of and the functionality-provided-by the module.

   ```python
   """Module docstring."""
   ```

   The interpreter will save this string as a special `__doc__` variable for the module.

3. _Import Statements_: Import statements import other code into your script so that you can use their functionality.

   ```python
   # Imports
   import os
   import sys
   ```

   When the interpreter encounters an import statement, it opens the module being imported and (starting with the first line of that module) executes each of the statements in that file. The contents of that module are then available to your script through the module's name, using dot-syntax, to access the variables, functions, and classes within the module.

4. _Module "Constants"_: Module constants, named by convention using all-CAPS variable names, are simple variable definitions. Nothing in the Python language makes these "constant." Their values can be changed. As a community we recognize an all-CAPS variable name as something that we probably shouldn't change.

   ```python
   # Module Constants
   START_MESSAGE = "CLI Inspection Script"
   ```

   The interpreter creates variables with these names and values.

5. _Module-level "Global" Variables_: Every function and class within the module will have at least "read access" to these variables as they exist at the top-level "global" scope within a module.

   ```python
   # Module "Global" Variables
   location = os.path.abspath(__file__)
   ```

   The interpreter creates variables with these names and values.

6. _Module Functions and Classes_: As the interpreter encounters new function or class definitions, it creates and stores them in memory to make them available to subsequent portions of your code.

   ```python
   # Module Functions and Classes
   def main(*args):
       """My main script function.

       Displays the full patch to this script, and a list of the arguments passed
       to the script.
       """
       print(START_MESSAGE)
       print("Script Location:", location)
       print("Arguments Passed:", args)
   ```

   Note that the statements within a function (or class) definition aren't "executed" when they are defined.  They are "loaded" and made available for future use in your script.  You must call a function (supplying any needed arguments) to execute its block of statements.

7. _The `if __name__ == '__main__'` Block_: Some Python files could serve as both a script (to be executed) and a module (which could be imported).  When a Python script is executed, it is given the internal `__name__` of `__main__` by the Python interpreter.  All other modules, when they are imported by some calling script, will see their `__name__` as their own module name. This allows us to use the `__name__` variable to determine (at run time) if our Python file is being executed or imported, and we can use if-clauses like this to take actions, execute functions, etc., if our file is the one being executed.

   ```python
   # Check to see if this file is the "__main__" script being executed
   if __name__ == '__main__':
       _, *script_args = sys.argv
       main(*script_args)
   ```

   If this file is the "`__main__`" script being executed, the if statement will evaluate to `True` and the interpreter proceeds with executing the statements inside the if-block. This allows us to parse any command line parameters, initialize any global variables, etc., and then call our script's "main" function.

   > **Note:** You can call your "main" function whatever you like. There is no special significance of the function name `main()`.

#### Order

_Why use this order for structuring a Python file?_ The linear execution order of statements within a Python file drives this ordering convention.  Modules have to be imported before you can use them. Your script must create module-level constants and variables before using them.  Functions and classes have to be defined before they can be referenced and used.  ...and so on.  This linearity creates a chain of prerequisites that dictates the order in which things must be created.

### Imports

You will see two different syntaxes used for importing functionality into a script:

1. The Import Statement

   ```python
   import os
   ```

2. From... Import...

   ```python
   from os.path import abspath
   ```

In both of these examples, we are importing functionality from the `os` module. In the first example, we imported the `os` module and would access the functionality within it using dot-syntax. (i.e. `os.path.abspath()`). In the second example, we import the `abspath` function from the `os.path` module, and we can now call it directly: `abspath()`, without having to use the full `os.path.abspath()` syntax. The `from ___ import ___` syntax provides a way for us to pull in only the functionality we need, and simplify the names of deeply nested resources.

### Variable Scope

A quick note on variable scoping. Variables are said to be defined in the scope in which they are created.

#### Module Scope

Variables created outside of any function or class, are defined at "module-scope" and can be accessed by every function and class created within that module.

#### Local Scope

Variables created inside of a function or class, are defined only within the "local scope" in which they have been created.  They may only be accessed by statements executing within the local scope in which they were created.

> **Note:** Function arguments are locally scoped variables.

#### Variable Scoping Example

Review the following code example, which illustrates variables being created at local and module-level scopes.

```python
#!/usr/bin/env python
"""Demonstrate module vs. locally scoped variables."""

# Create a module variable
module_variable = "I am a module variable."

# Define a function that expects to receive a value for an argument variable
def my_function(argument_variable):
    """Showing how module, argument, and local variables are used."""
    # Create a local variable
    local_variable = "I am a local variable."

    print(module_variable, "...and I can be accessed inside a function.")
    print(argument_variable, "...and I can be passed to a function.")
    print(local_variable, "...and I can ONLY be accessed inside a function.")

# Call the function; supplying the value for the argument variable
my_function(argument_variable="I am a argument variable.")

# Let's try accessing that local variable here at module scope
print("\nTrying to access local_variable outside of its function...")
try:
    print(local_variable)
except NameError as error:
    print(error)
```

**Note the Following:**

1. The `module_variable` is created outside of any function or class.
2. The `local_variable` is created inside a function.
3. The `argument_variable`'s name is defined as part of the function definition, but its value isn't assigned until the function is called.

_**Now, run this script on your developer workstation to see the output:**_

```shell
$ python intro-python/part2/variable_scope.py
```

<details>
<summary> Click for Expected Output </summary>
<pre><code>
(venv) [root@localhost]# python intro-python/part2/variable_scope.py
I am a module variable. ...and I can be accessed inside a function.
I am a argument variable. ...and I can be passed to a function.
I am a local variable. ...and I can ONLY be accessed inside a function.

Trying to access local_variable outside of its function...
name 'local_variable' is not defined
</code></pre>
</details>

**Next: Debugging basics**
