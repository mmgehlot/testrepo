# Step 1: Reading and writing files

Reading-from and writing-to text files is easy with Python's built-in `open()` function. It returns a file object that we can use to read-from and/or write-to the file that we opened.

_**Run the following on your developer workstation:**_

1. Open your Terminal and change directories to the root of the `dnav3-code` or `dne-security-code` or `dciv2-code` repository that you cloned to your machine.

    ```shell
    $ cd ~/code/dnav3-code
    ```

    or
    ```shell
    $ cd ~/code/dne-security-code
    ```

    or
    ```shell
    $ cd dciv2-code
    ```

2. Open your Python interactive shell.

    ```shell
    $ python -i
    ```

    <details>
    <summary> Click for Sample Output </summary>
    <pre><code>(venv) [root@localhost]# python
    Python 3.6.5 (default, Apr  2 2018, 15:31:03)
    [GCC 4.8.5 20150623 (Red Hat 4.8.5-16)] on linux
    Type "help", "copyright", "credits" or "license" for more information.
    >>>
    </code></pre>
    </details>

3. Open the file `intro-python/parsing-json/pep20.txt` for reading.

    ```python
    >>> file = open("intro-python/parsing-json/pep20.txt", mode="r")
    ```

4. Read and print the contents of the file.

    ```python
    >>> file_contents = file.read()
    >>> print(file_contents)
    ```

    <details>
    <summary> Click for Expected Output </summary>
    <pre><code>
    Beautiful is better than ugly.
    Explicit is better than implicit.
    Simple is better than complex.
    Complex is better than complicated.
    Flat is better than nested.
    Sparse is better than dense.
    Readability counts.
    Special cases aren't special enough to break the rules.
    Although practicality beats purity.
    Errors should never pass silently.
    Unless explicitly silenced.
    In the face of ambiguity, refuse the temptation to guess.
    There should be one-- and preferably only one --obvious way to do it.
    Although that way may not be obvious at first unless you're Dutch.
    Now is better than never.
    Although never is often better than *right* now.
    If the implementation is hard to explain, it's a bad idea.
    If the implementation is easy to explain, it may be a good idea.
    Namespaces are one honking great idea -- let's do more of those!
    </code></pre>
    </details>

5. Close the file.

    ```python
    >>> file.close()
    ```

### Open function

Excerpts from the [Python Docs](https://docs.python.org/3/library/functions.html#open):

```python
open(file, mode='r')
```

Open _file_ and return a corresponding [file object](https://docs.python.org/3/glossary.html#term-file-object). If the file cannot be opened, an [OSError]() is raised.

`file` is a [path-like](https://docs.python.org/3/glossary.html#term-path-like-object) object giving the pathname (absolute or relative to the current working directory) of the file to be opened.

`mode` is an optional string that specifies the mode in which the file is opened. It defaults to 'r' which means open for reading in text mode. Other common values are 'w' for writing (truncating the file if it already exists).

> **Note:** Don't forget to `.close()` files that you open. If you don't want to have to remember to close the files, use the `with` statement and let it manage the context for your open file.

### The `with` statement

Python provides a powerful (under the hood), but easy to understand, context manager capability. In this context, we want to be able to open a file work with its contents and then have Python remember to close it when we are done.  We instruct Python to do this by using the `with` statement.

_This example does exactly the same thing that we did previously, only we don't have to remember to `.close()` the file when we are done with it:_

```python
>>> with open("intro-python/parsing-json/pep20.txt", mode="r") as file:
...     file_contents = file.read()
...     print(file_contents)
...
Beautiful is better than ugly.
Explicit is better than implicit.
<output truncated for brevity>
```

Using the `with` statement we are saying:

1. `with` the (_file_object_ returned from the `open()` function) assigned to the variable name `file`:
2. Do the indented block of statements.
3. You close the file when we are done with the indented block.

> **Writing Files:** The process to write to a file is the same as reading from one. We open the file, only this time opening it in "writing" mode, with the `open(file, mode='w')` function. Then, we use the `file.write()` function to write our contents out to the file.

Now that we know how to read and write some text to files in our file system, let's learn how to work with JSON.

**Next: Parsing JSON**
