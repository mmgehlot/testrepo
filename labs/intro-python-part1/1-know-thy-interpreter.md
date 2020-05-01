# Step 1: Know thy Interpreter

Python scripts are simple (UTF-8) text files.  You could write or edit one with any text editor.  You _don't_ compile them.  How are you going to execute them?  Answer: with a Python interpreter!

### Prerequisites
If you are performing these instructions at a DevNet Live! event, your workstation should already be setup. However, if you are perfomring these instructions on your own, ensure you must have carried out all the instruction under:

* Setting Up a Development Workstation for this Lab, and
* Using Git to Copy Code and Setting Up the Local Environment

### Which interpreter are you using?

~~The one installed on your developer workstation of course!~~  _(snark removed)_

Seriously though, you can have multiple interpreters on your workstation so it is important to know which interpreter you are using at any point in time.

Outside of a virtual environment, your interpreter could be _called_ by many names:

* `python`
* `py -2` _(windows only)_
* `py -3` _(windows only)_
* `python2`
* `python3`
* `python3.6`
* `python3.7`
* etc.

Inside a virtual environment, your interpreter will always go by the name `python`, which is much easier to remember and work with.

Go ahead and activate your Python virtual environment.

_**Note:**_  You need to commit to memory how to "activate your virtual environment." You must have your virtual environment activated before "pip installing" any packages or running any scripts in this module. You will need to activate your virtual environment anytime you open a new Terminal, as virtual environment activation does not persist when a Terminal session is closed.

_**Reminder: To activate your virtual environment:**_

1. Open your Terminal.
2. DevNet Express

  - If you are in a DevNet Express for DNA, change to the root directory of the `dnav3-code` repository.

  - If you are in a DevNet Express for Security track, change to the root directory of the `dne-security-code` repository.

  - If you are in a DevNet Express for Data Center Infrastructure, change to the root directory of the `dciv2-code` repository. **You should also be using the "Git Bash3" Terminal**

You cloned one of these repositories to your computer as part of the "Using Git to Copy Code and Setting Up the Local Environment" procedures. For example:

  For DevNet Express for DNA
   ```shell
   $ cd dnav3-code
   ```
   or for DevNet Express for Security track
   ```shell
   $ cd dne-security-code
   ```
   or for DevNet Express for Data Center Infrastructure, you are also creating a Python Virtual Environment.
   ```shell
   $ cd dciv2-code
   $ py -3 -m venv venv
   ```
3. Run one of the following commands (depending upon your platform) to activate your virtual environment:

_Linux / macOS:_

```shell
$ source venv/bin/activate
```

<details>
<summary> Sample Output </summary>
<pre><code>
[root@localhost]# source venv/bin/activate
(venv) [root@localhost]#
</code></pre>
</details>

_Windows:_ **(Use this command in the Git Bash3 Terminal for the DCI DevNet Express)**

```shell
$ source venv/Scripts/activate
```

> You can always tell when you are working in an activated virtual environment. The activation script prefixes your command prompt with the name of your activated virtual environment (in parentheses).

#### Verify your Interpreter
If there is ever any confusion about which interpreter you are using, there are couple of commands that can help you out:

```shell
$ which python
```

<details>
<summary> Sample Output </summary>
<pre><code>
(venv) [root@localhost]# which python
/root/dnav3-code/venv/bin/python
</code></pre>
</details>

_Will give you the full path to the interpreter._

```shell
$ python -V
```

<details>
<summary> Sample Output </summary>
<pre><code>
(venv) [root@localhost]# python -V
Python 3.6.5
</code></pre>
</details>

_Will give you the version info for the interpreter._

_**Take a minute to ensure you have your Terminal open, virtual environment activated, and are using a Python interpreter >= v3.5.**_

### Python Virtual Environments

Without virtual environments, when you `pip install` packages on your workstation, all of those packages (and their dependencies) get installed "globally." Over time this can clutter up your global Python environment, and eventually you run into version conflicts where Project A needs version X.X of a particular package and Project B needs Y.Y.

Virtual environments are an elegant way to uncluttered your global Python environment, and isolate projects from each other. At first, they might sound somewhat mysterious, but they are conceptually simple.

When you create a virtual environment (like you did with the `python -m venv <virtual environment name>` command), the virtual environment module `venv` creates a new folder using the name you provided. Looking inside that folder, you will see something like the following:

```shell
venv/
├── bin
├── include
├── lib
└── pip-selfcheck.json
```

Now, when working inside an activated virtual environment and you `pip install` some _library_, where do you think that gets installed?

_That's right!_ ...in the `/lib` directory.

What about if you `pip install` some _executable_ script?

_Also correct!_ ...in the `/bin` directory.

You see, a virtual environment is essentially redirecting where packages get installed and where Python looks to find them.  Instead of installing packages in the global environment, they are instead installed in the virtual environment directory that you told `venv` to create.

You can create these virtual environments in the same directory as your project files (though you usually exclude them from version control), and then everything stays nice and neat. When you go to work on a project, you can simply activate its virtual environment and you have all the packages you need to work on that project. When you want to switch from working on Project A to working on Project B, you deactivate Project A's virtual environment and then activate Project B's.

> **Note:** Use the `deactivate` command to exit out of an active virtual environment.

When you are done with a Project and perhaps delete it from your workstation, the virtual environment directory and the packages installed in are also deleted. No more cluttering up directories with unneeded files.

Also, no matter how many Python interpreters you have installed on your workstation - when you are working in your virtual environment, the `python` command will always refer to the `python` interpreter located within the virtual environment - which is a _symbolic link_ to the interpreter that you used to create the virtual environment. As long as you are working in your virtual environment, the `python` command will point to the interpreter of your choosing (the one you used to create the environment).

### Accessing the Python Interactive Shell

Python comes equipped with a ~~Read Evaluate Print Loop (REPL)~~ _(boring name)_ Interactive Shell!  Which is awesome for playing with Python syntax, incrementally testing commands, playing with APIs and data, and so much more.

To access Python's interactive shell, just call the interpreter without providing any options or arguments.

_**Do this on your workstation:**_

```shell
$ python -i
```

> NOTE: On Windows within `git-bash`, you need to use the command `python -i` to explicitly start the `i`nteractive interpreter. On macOS, the interactive interpreter starts automatically with the `python` command.

<details>
<summary> Sample Output </summary>
<pre><code>
(venv) [root@localhost]# python -i
Python 3.6.5 (default, Apr  2 2018, 15:31:03)
[GCC 4.8.5 20150623 (Red Hat 4.8.5-16)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
</code></pre>
</details>

You can enter any valid Python statement, and the interactive shell will execute it and display its output - if it has any output. We'll use this quite a bit as we explore some of Python's basic syntax and data types. For now, just remember that you always have this tool at your fingertips anytime you want to play with or test out some Python syntax.

> **Note:** To exit the interactive interpreter, press `Ctrl-Z` and then `Enter` on Windows, or `Ctrl-D` on Linux or macOS. You can also exit the interactive shell running the Python command `exit()`.
> **Note:** If you are in the virtual environment, the Python exit command *does not deactivate the virtual environment*. For that you must use `deactivate`.

_**Now, practice exiting the interactive interpreter**_

Type the Python command `exit()` in the interactive interpreter:

```
>>> exit()
```

### Running a script

Python files (again just text files) by convention end with the extension `.py`.  To run a Python file, just pass it to your interpreter like so:

_**Run this on your workstation:**_

```shell
$ python intro-python/part1/hello.py
```

<details>
<summary> Sample Output </summary>
<pre><code>
(venv) [root@localhost]# python intro-python/part1/hello.py
Hello Python!!  ...at least I didn't say World.
</code></pre>
</details>

> **Note:** You can also instruct the interpreter to run your script and then stay in the interactive shell.  This can be useful to incrementally build or debug Python scripts.  We'll talk more about this in _Part 2_.

**Next: Basic Python syntax**
