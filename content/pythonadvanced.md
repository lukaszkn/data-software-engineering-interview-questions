# Python Advanced
Functions, annotations, coding style, reading and writing files, classes, iterators, standard library

* [Positional-only parameters](#Positional-only-parameters)
* [Keyword-only parameters](#Keyword-only-parameters)
* [Combining different types of parameters](#Combining-different-types-of-parameters)
* [Keyword-only arguments without `*args`](#Keyword-only-arguments-without-args)
* [Function annotations](#Function-annotations)
* [Accessing annotations](#Accessing-annotations)
* [Type hinting with annotations](#Type-hinting-with-annotations)
* [Using `Optional` and `Union` for flexible type hints](#Using-Optional-and-Union-for-flexible-type-hints)
* [Annotating functions with complex types](#Annotating-functions-with-complex-types)
* [Custom annotations](#Custom-annotations)
* [Forward references](#Forward-references)
* [Using `Callable` for function annotations](#Using-Callable-for-function-annotations)
* [Coding style PEP8](#Coding-style-PEP8)
* [Coding style: Indentation](#Coding-style-Indentation)
* [Coding style: Line length](#Coding-style-Line-length)
* [Coding style: Blank lines](#Coding-style-Blank-lines)
* [Coding style: Imports](#Coding-style-Imports)
* [Coding style: Whitespace in expressions and statements](#Coding-style-Whitespace-in-expressions-and-statements)
* [Coding style: Comments](#Coding-style-Comments)
* [Coding style: Naming conventions](#Coding-style-Naming-conventions)
* [Coding style: Programming recommendations](#Coding-style-Programming-recommendations)
* [Coding style: Exceptions](#Coding-style-Exceptions)
* [Coding style: Use of `__main__`](#Coding-style-Use-of-main)
* [Reloading modules](#Reloading-modules)
* ["Compiled" Python files](#Compiled-Python-files)
* [Why does Python compile code?](#Why-does-Python-compile-code)
* [How compiled files work](#How-compiled-files-work)
* [Location of compiled files](#Location-of-compiled-files)
* [Running a Python program without the source code (`.pyc` files)](#Running-a-Python-program-without-the-source-code-pyc-files)
* [Disabling bytecode generation](#Disabling-bytecode-generation)
* [Forcing recompilation of Python files](#Forcing-recompilation-of-Python-files)
* [Pros and cons of compiled Python files](#Pros-and-cons-of-compiled-Python-files)
* [Bytecode and the Python Virtual Machine (PVM)](#Bytecode-and-the-Python-Virtual-Machine-PVM)
* [Intra-package references](#Intra-package-references)
* [Using `__init__.py` in packages](#Using-init-py-in-packages)
* [Best practices for intra-package imports](#Best-practices-for-intra-package-imports)
* [Opening a file](#Opening-a-file)
* [Closing a file](#Closing-a-file)
* [Reading the entire file `read()`](#Reading-the-entire-file-read)
* [Reading line by line `readline()`](#Reading-line-by-line-readline)
* [Reading all lines as a list `readlines()`](#Reading-all-lines-as-a-list-readlines)
* [Iterating over the file object](#Iterating-over-the-file-object)
* [Writing strings to a file `write()`](#Writing-strings-to-a-file-write)
* [Writing multiple lines to a file `writelines()`](#Writing-multiple-lines-to-a-file-writelines)
* [Binary files](#Binary-files)
* [File modes summary](#File-modes-summary)
* [File object methods](#File-object-methods)
* [Managing file paths](#Managing-file-paths)
* [File exceptions](#File-exceptions)
* [File handling best practices](#File-handling-best-practices)
* [File `tell()` method](#File-tell-method)
* [File `seek()` method](#File-seek-method)
* [`tell()` and `seek()` common use cases](#tell-and-seek-common-use-cases)
* [Saving data with json](#Saving-data-with-json)
* [Saving structured data with `json.dump()`](#Saving-structured-data-with-json-dump)
* [Reading json data with `json.load()`](#Reading-json-data-with-json-load)
* [Converting objects to JSON strings with `json.dumps()`](#Converting-objects-to-JSON-strings-with-json-dumps)
* [Converting JSON strings to objects with `json.loads()`](#Converting-JSON-strings-to-objects-with-json-loads)
* [Handling custom data types with `json.JSONEncoder`](#Handling-custom-data-types-with-json-JSONEncoder)
* [Working with nested json structures](#Working-with-nested-json-structures)
* [Error handling with json](#Error-handling-with-json)
* [Enriching exceptions with notes](#Enriching-exceptions-with-notes)
* [How to use `add_note()`](#How-to-use-add-note)
* [Benefits of enriching exceptions](#Benefits-of-enriching-exceptions)
* [Iterators](#Iterators)
* [How iterators work](#How-iterators-work)
* [Manually creating an iterator](#Manually-creating-an-iterator)
* [Using `iter()` and `next()`](#Using-iter-and-next)
* [Iterator vs iterable](#Iterator-vs-iterable)
* [Iterating over custom collections](#Iterating-over-custom-collections)
* [Infinite iterators with `itertools`](#Infinite-iterators-with-itertools)
* [Generators as iterators](#Generators-as-iterators)
* [`os` module: Basic file and directory operations](#os-module-Basic-file-and-directory-operations)
* [`os` module: File path operations](#os-module-File-path-operations)
* [`os` module: Environment variables](#os-module-Environment-variables)
* [`os` module: Process management](#os-module-Process-management)
* [`os` module: Working with file descriptors](#os-module-Working-with-file-descriptors)
* [`os` module: Working with the `os.walk()` function](#os-module-Working-with-the-os-walk-function)
* [`os` module: Temporary files and directories](#os-module-Temporary-files-and-directories)
* [`shutil` module: Copying files and directories](#shutil-module-Copying-files-and-directories)
* [`shutil` module: Moving files and directories](#shutil-module-Moving-files-and-directories)
* [`shutil` module: Removing files and directories](#shutil-module-Removing-files-and-directories)
* [`shutil` module: Archiving files and directories](#shutil-module-Archiving-files-and-directories)
* [`shutil` module: Disk usage](#shutil-module-Disk-usage)
* [`shutil` module: File system operations](#shutil-module-File-system-operations)
* [`shutil` module: Error handling](#shutil-module-Error-handling)
* [Common string validation methods](#Common-string-validation-methods)
* [What are context managers?](#What-are-context-managers)
* [Custom context manager example](#Custom-context-manager-example)
* [Real-world uses of context managers](#Real-world-uses-of-context-managers)
* [The `contextlib` module](#The-contextlib-module)
* [Why use context managers?](#Why-use-context-managers)

## Positional-only parameters
Positional-only parameters are parameters that can only be provided by position, not by keyword. This is specified by placing a `/` in the function signature. Everything before the `/` is positional-only.

Example:
```python
def greet(name, /, greeting="Hello"):
    return f"{greeting}, {name}!"

# Valid calls
print(greet("Alice"))               # Output: Hello, Alice!
print(greet("Alice", "Hi"))         # Output: Hi, Alice!

# Invalid calls (would raise a TypeError)
# greet(name="Alice")                # Raises TypeError
# greet(name="Alice", greeting="Hi") # Raises TypeError
```
In this example, `name` is a positional-only parameter, so you cannot pass it using a keyword argument.

## Keyword-only parameters
Keyword-only parameters are parameters that must be specified by keyword, not by position. This is specified by placing a `*` in the function signature. Everything after the `*` is keyword-only.

Example:
```python
def process_data(*, data, verbose=False):
    if verbose:
        print("Processing data...")
    return data

# Valid calls
# Output: [1, 2, 3]
print(process_data(data=[1, 2, 3]))

# Output: Processing data [1, 2, 3]
print(process_data(data=[1, 2, 3], verbose=True))      

# Invalid calls (would raise a TypeError)

# process_data([1, 2, 3]) # Raises TypeError

# process_data([1, 2, 3], True) # Raises TypeError
```
In this example, data and verbose are keyword-only parameters, so you must specify them by their names.

## Combining different types of parameters
You can combine positional-only, standard, keyword-only, `*args` and `**kwargs` parameters in a single function. The general order in which parameters should be placed is:

1. Positional-only parameters
2. Positional or keyword parameters
3. `*args` (variable-length positional arguments)
4. Keyword-only parameters
5. **kwargs (variable-length keyword arguments)

Example:
```python
def complex_function(pos_only, /, standard, *args, kw_only, **kwargs):
    print(f"Positional-only: {pos_only}")
    print(f"Standard: {standard}")
    print(f"Args: {args}")
    print(f"Keyword-only: {kw_only}")
    print(f"Kwargs: {kwargs}")

complex_function(1, 2, 3, 4, 5, kw_only="Hello", extra="world")
# Output:
# Positional-only: 1
# Standard: 2
# Args: (3, 4, 5)
# Keyword-only: Hello
# Kwargs: {'extra': 'world'}
```

## Keyword-only arguments without `*args`
You can enforce keyword-only arguments without using `*args` by placing `*` before the keyword-only arguments:

Example:
```python
def greet(name, *, greeting="Hello"):
    return f"{greeting}, {name}!"

# Valid calls
print(greet("Alice"))                   # Output: Hello, Alice!
print(greet("Alice", greeting="Hi"))    # Output: Hi, Alice!

# Invalid calls (would raise a TypeError)
# greet("Alice", "Hi")                  # Raises TypeError
```

## Function annotations
Function annotations in Python provide a way to attach metadata to function arguments and return values. This metadata is typically used for type hints, though annotations can technically hold any kind of data. Annotations do not affect the runtime behavior of the function; they are purely informational and can be accessed via the function's `__annotations__` attribute.

### Basic syntax of function annotations
Annotations are specified using a colon `:` after the parameter name for argument annotations, and an arrow `->` after the parameter list for return type annotations.

Example:
```python
def greet(name: str, age: int) -> str:
    return f"Hello, {name}. You are {age} years old."
```
In this example:
- The parameter `name` is annotated with the type `str`.
- The parameter `age` is annotated with the type `int`.
- The return type of the function is annotated as `str`.

## Accessing annotations
You can access a function’s annotations using the `__annotations__` attribute, which returns a dictionary.

Example:
```python
def greet(name: str, age: int) -> str:
    return f"Hello, {name}. You are {age} years old."

print(greet.__annotations__)
# Output: {'name': 'str', 'age': 'int', 'return': 'str'}
```

## Type hinting with annotations
The most common use of function annotations is for type hinting, which helps developers and tools like linters or IDEs understand the expected types of arguments and return values.

Example:
```python
def add_numbers(a: int, b: int) -> int:
    return a + b
```
Here:
- `a` and `b` are expected to be integers.
- The function is expected to return an integer.

## Using `Optional` and `Union` for flexible type hints
Python’s `typing` module provides additional tools like `Optional` and `Union` for more complex type hints.

Example with `Optional`:
```python
from typing import Optional

def greet(name: str, age: Optional[int] = None) -> str:
    if age is None:
        return f"Hello, {name}."
    else:
        return f"Hello, {name}. You are {age} years old."
```
Here, `age: Optional[int]` indicates that `age` can be either an int or `None`.

Example with `Union`:
```python
from typing import Union

def get_value(data: Union[int, str]) -> Union[int, str]:
    return data
```

- `data: Union[int, str]` indicates that `data` can be either an `int` or a `str`.
- The return type is also `Union[int, str]` indicating that the function can return either type.

## Annotating functions with complex types
You can annotate functions with complex types, such as lists, dictionaries, tuples, and even custom classes.

Example with a `List`:
```python
from typing import List

def process_items(items: List[str]) -> int:
    return len(items)
```
- `items: List[str]` indicates that `items` should be a list of strings.

Example with a `Dictionary`:
```python
from typing import Dict

def process_data(data: Dict[str, int]) -> None:
    for key, value in data.items():
        print(f"{key}: {value}")
```
- `data: Dict[str, int]` indicates that `data` should be a dictionary with string keys and integer values.

## Custom annotations
Although type hints are the most common use of annotations, you can technically use any expression as an annotation.

Example with custom annotations:
```python
def func(x: 'An integer', y: 'Another integer') -> 'The sum of x and y':
    return x + y

print(func.__annotations__)
# Output: {'x': 'An integer', 'y': 'Another integer', 'return': 'The sum of x and y'}
```
In this example, the annotations are just strings providing a description, but they can be any data type.

## Forward references
In cases where a class or type is not yet defined, you can use a string to refer to the type.

Example:
```python
class Node:
    def __init__(self, value: int, next_node: 'Node' = None):
        self.value = value
        self.next_node = next_node
```
- Here, `'Node'` is a forward reference to a class that is defined later in the code.

## Using `Callable` for function annotations
The `typing` module provides the `Callable` type to annotate functions that are passed as arguments.

Example:
```python
from typing import Callable

def apply_function(func: Callable[[int, int], int], x: int, y: int) -> int:
    return func(x, y)

def add(a: int, b: int) -> int:
    return a + b

print(apply_function(add, 5, 3))  # Output: 8
```
- `Callable[[int, int], int]` indicates that `func` is a function that takes two `int` arguments and returns an `int`.

## Coding style PEP8
PEP 8 is the Python Enhancement Proposal that provides guidelines and best practices for writing Python code. Following PEP 8 helps ensure that your code is readable, consistent, and easy to maintain, especially when collaborating with others. Here are the key elements of PEP 8:

1. Indentation
2. Line length
3. Blank lines
4. Imports
5. Whitespace in expressions and statements
6. Comments
7. Naming conventions
8. Programming recommendations
9. Exceptions
10. Use of __main__

## Coding style: Indentation
- Use **4 spaces** per indentation level.
- Do not use tabs for indentation.
```python
def example_function():
    if True:
        print("Use 4 spaces per indentation level")
```

## Coding style: Line length
- Limit all lines to a maximum of **79 characters**.
- For docstrings or comments, the line length should be limited to **72 characters**.
- If a line is too long, consider breaking it into multiple lines using parentheses for implicit line continuation or a backslash `\` for explicit continuation.
```python
# Implicit line continuation with parentheses
def example_function(arg1, arg2, arg3, arg4, arg5):
    result = (arg1 + arg2 + arg3 +
              arg4 + arg5)
    return result
```

## Coding style: Blank lines
- Use **two blank lines** before the definition of top-level functions and classes.
- Use **one blank line** to separate methods inside a class.
```python
class MyClass:
    
    def method_one(self):
        pass
    
    def method_two(self):
        pass

def top_level_function():
    pass
```

## Coding style: Imports
- Imports should be on separate lines.
- Group imports into three categories: standard library imports, related third-party imports, and local application/library-specific imports. Separate these groups with a blank line.
- Avoid using wildcard imports (e.g., from module import *).
```python
# Correct import grouping
import os
import sys

import requests

from mymodule import myfunction
```

## Coding style: Whitespace in expressions and statements
Avoid extraneous whitespace in the following situations:
- Immediately inside parentheses, brackets, or braces.
- Before a comma, semicolon, or colon.
- Immediately before the opening parenthesis that starts the argument list of a function call.
- Immediately before the opening bracket that starts an indexing or slicing.
```python
# Correct usage
my_list = [1, 2, 3]
x = (1 + 2) * (3 / 4)

# Incorrect usage
my_list = [ 1, 2, 3 ]
x = ( 1 + 2 ) * ( 3 / 4 )
```
- Use a single space around operators and after commas, but not directly inside parentheses.
```python
# Correct usage
result = x + y
my_list = [1, 2, 3]

# Incorrect usage
result = x+y
my_list = [1,2,3]
```

## Coding style: Comments
- Comments should be complete sentences with the first word capitalized and end with a period if they are full sentences.
- Use inline comments sparingly. Place them on the same line as the statement they comment on, separated by at least two spaces.
```python
# This is a full-line comment

x = x + 1  # Increment x by 1
```
- Block comments should use a single # at the beginning of each line.
```python
# Block comment starts with a #
# and extends for multiple lines.
```
- Docstrings should be used to describe all public modules, functions, classes, and methods. Place the opening `"""` on the same line as the docstring if it's one line, otherwise on its own line if it's multi-line.
```python
def add(a, b):
    """Add two numbers."""
    return a + b

def complex_function(x, y):
    """
    Perform a complex calculation.

    Args:
        x (int): First number.
        y (int): Second number.

    Returns:
        int: Result of the calculation.
    """
    return x + y
```

## Coding style: Naming conventions
- Variables, functions, and attributes: Use `lowercase_with_underscores`.
- Classes and exceptions: Use `CapWords` (also known as PascalCase).
- Constants: Use `ALL_CAPS_WITH_UNDERSCORES`.
- Modules and packages: Use short, lowercase names. Underscores can be used if it improves readability.
```python
# Variable and function names
my_variable = 10

def my_function():
    pass

# Class names
class MyClass:
    pass

# Constant names
PI = 3.14159
```

## Coding style: Programming recommendations
- Use `is` or `is not` when comparing to `None` (e.g., `if x is None` rather than `if x == None`).
- Use the `in` operator for checking if a value is in a list, tuple, or dictionary.
- Avoid using mutable default arguments like lists or dictionaries in function definitions.
```python
# Correct way to check for None
if x is None:
    pass

# Avoid mutable default arguments
def my_function(x=None):
    if x is None:
        x = []
    # x can be safely modified now
```

## Coding style: Exceptions
- Use specific exception types rather than a generic `except` block.
- Ensure exceptions are handled properly, using `try-except` blocks where appropriate.
```python
try:
    value = int(input("Enter a number: "))
except ValueError:
    print("That's not a valid number.")
```

## Coding style: Use of `__main__`
When writing a script that can be imported as a module or run as a standalone program, include a `__name__ == "__main__"` block.

```python
def main():
    print("This is the main function.")

if __name__ == "__main__":
    main()
```

## Reloading modules
Sometimes, when you're developing a module and want to reload it after making changes, you can use the `reload()` function from the `importlib` module.

Example:
```python
import mymodule
from importlib import reload

reload(mymodule)  # Reloads the mymodule after modification
```

## "Compiled" Python files
In Python, compiled Python files are bytecode files generated by the Python interpreter when a Python script is executed. These files are stored in a format that is faster for the interpreter to run in future executions.

### What are compiled Python files?
When you run a Python program, the Python interpreter first compiles the `.py` source file into bytecode, which is a lower-level, platform-independent representation of your code. This bytecode is then executed by the Python virtual machine (PVM).

The compiled bytecode files are stored with a `.pyc` extension (Python Compiled) and are located in a `__pycache__` directory. These `.pyc` files are used to speed up the execution of Python programs by avoiding the need to recompile the source code every time the program is run.

## Why does Python compile code?
Python is an interpreted language, but it uses a two-step process:

- **Compilation**: The `.py` source code is compiled into bytecode (with `.pyc` extension).
- **Execution**: The Python virtual machine (PVM) executes the bytecode.

The purpose of this process is to improve performance. Instead of interpreting the source code line by line every time, Python only needs to compile the source code once, and future executions can directly run the compiled bytecode.

## How compiled files work
- The first time you run a Python script, Python compiles the source code into bytecode.

- This bytecode is stored in a `__pycache__` directory inside the same folder as your Python files.

- The next time you run the program, Python checks whether the `.pyc` file exists and if it corresponds to the latest version of the source code.

- If the `.pyc` file is up to date, Python skips the compilation step and directly executes the bytecode.

Example:
Assume you have a Python script called `example.py`:
```python
# example.py
print("Hello, World!")
```
When you run this script, Python compiles it into bytecode and stores it as `__pycache__/example.cpython-<version>.pyc`. The next time you run `example.py`, Python will use the `.pyc` file if no changes have been made to `example.py`.

## Location of compiled files
Compiled Python files are stored in a `__pycache__` folder within the same directory as your Python script. The naming convention for the compiled file is as follows:
- `module_name.cpython-<version>.pyc`

For example, a file compiled with Python 3.8 will have a `.pyc` file named:
- `__pycache__/example.cpython-38.pyc`

This structure allows Python to store multiple compiled files for different versions of the interpreter in the same directory.

## Running a Python program without the source code (`.pyc` files)
Python can run a program directly from its bytecode files (`.pyc`), even if the original source code (`.py` files) is not available. To run a `.pyc` file, just pass it to the Python interpreter.

For example, if you have a compiled bytecode file `example.cpython-38.pyc`, you can run it like this:

```bash
python example.cpython-38.pyc
```

## Disabling bytecode generation
If you don’t want Python to generate compiled `.pyc` files, you can prevent this by using the `PYTHONDONTWRITEBYTECODE` environment variable or by passing the `-B` flag when running Python scripts.

Example:
```bash
python -B example.py
```
This will run the script without creating a compiled `.pyc` file.

## Forcing recompilation of Python files
If you want to force Python to recompile your source files (perhaps because of changes in the code or version), you can delete the `__pycache__` directory or the corresponding `.pyc` files.

Alternatively, you can use the `compileall` module to recompile all Python source files in a directory.

Example:
```bash
python -m compileall .
```
This command will recompile all Python files in the current directory and store the `.pyc` files in the `__pycache__` folder.

## Pros and cons of compiled Python files
Pros:
- **Faster execution**: Since the source code is already compiled into bytecode, Python can skip the compilation step, resulting in faster execution times.

- **Platform independence**: Bytecode is platform-independent, so the same `.pyc` files can be used across different operating systems.

- **Precompiled bytecode**: Python programs can be distributed without the original source code.

Cons:
- **Not much performance improvement**: Although Python bytecode speeds up program execution, the improvement is modest compared to languages that are fully compiled, such as C or C++.

- **Outdated bytecode**: If the source code changes but the `.pyc` file does not get updated, running the program could lead to incorrect behavior.

- **No human readability**: Bytecode is not human-readable, making it difficult to inspect or debug.

## Bytecode and the Python Virtual Machine (PVM)
Python’s bytecode is executed by the Python virtual machine (PVM). The PVM is a part of the Python runtime system, which takes the compiled bytecode and interprets it to perform the actual execution. This is why Python is often called an "interpreted" language even though it involves an intermediate compilation step.

### Summary
- **Compiled Python files**: When a Python script is executed, the source code (.py) is compiled into bytecode and stored in `.pyc` files within the `__pycache__` folder.

- **Faster execution**: Compiling Python files into bytecode speeds up subsequent executions by skipping the recompilation step.

- **Running bytecode**: Python can run a program using its `.pyc` bytecode file, even without the original source code.

- **Disabling `.pyc` files**: You can prevent Python from generating compiled files using the `-B` flag or `PYTHONDONTWRITEBYTECODE` environment variable.

## Intra-package references
Intra-package references in Python refer to the process of referencing or importing modules, submodules, or functions within the same package. These references help organize and maintain large projects by allowing components of the package to be accessible to each other in a structured and clear way.

### Absolute imports
An absolute import specifies the full path to the module from the top-level package, starting from the package’s root directory. This is the preferred way to import modules because it is clear and unambiguous.

To import `module1` from `module2`, you would use the following absolute import in `module2.py`:
```python
# module2.py

import mypackage.module1
```

### Relative imports
- **`.`** refers to the current package/module.
- **`..`** refers to the parent package.
- **`...`** refers to the grandparent package, and so on.

Example:
```python
from . import module1

from .. import module1

from ...subpackage import submodule
```

## Using `__init__.py` in packages
The `__init__.py` file is an essential part of Python packages. It can be used to initialize the package or define what is available when importing the package.

**Empty `__init__.py`**
You can have an empty `__init__.py`, and the directory will still be treated as a package. This is enough to make it a valid Python package.

**Populating `__init__.py`**
You can place initialization code or specify imports that should be available when the package is imported.

For example, you can include in `__init__.py`:
```python
# __init__.py

from .module1 import some_function
from .module2 import another_function
```
This way, you can access those functions directly when importing the package:
```python
import mypackage

mypackage.some_function()
mypackage.another_function()
```

## Best practices for intra-package imports
- **Use absolute imports**: Absolute imports are preferred for their clarity and explicitness, especially in larger projects where relative imports might become confusing.

- **Use relative imports sparingly**: While relative imports are convenient, they can become ambiguous as the project grows, especially when modules are moved around.

- **Use `__init__.py` for package-level imports**: Organize what should be exposed at the package level within the `__init__.py` file.

- **Avoid circular imports**: Be cautious when importing modules within the same package to avoid circular dependencies, where two or more modules import each other, causing a loop.

## Opening a file
Before you can read from or write to a file, you must first open it using the built-in open() function. This function returns a file object that can be used to interact with the file.

The syntax is:
```python
file_object = open(file_path, mode)
```
- file_path: The location of the file you want to open (can be relative or absolute).
- mode: Specifies the mode in which the file is opened. Some common modes include:
  - 'r': Read (default mode). Opens the file for reading. The file must exist.
  - 'w': Write. Opens the file for writing, truncating the file first. Creates the file if it doesn’t exist.
  - 'a': Append. Opens the file for appending data to the end. Creates the file if it doesn’t exist.
  - 'b': Binary mode (used in combination with 'r', 'w', or 'a'). Handles binary data (like images).
  - 'x': Exclusive creation. Fails if the file already exists.

For example:
```python
f = open("example.txt", "r")  # Opens 'example.txt' for reading
```

## Closing a file
After working with a file, it’s important to close it to free up system resources. You can close a file using the `close()` method:

```python
f.close()
```
Alternatively, you can use a with statement to automatically close the file when you’re done:

```python
with open("example.txt", "r") as f:
    data = f.read()
```
The file will be closed automatically when the with block is exited.

## Reading the entire file `read()`
The `read()` method reads the entire contents of the file into a string.

```python
with open("example.txt", "r") as f:
    content = f.read()
    print(content)
```

## Reading line by line `readline()`
The `readline()` method reads one line from the file at a time:

```python
with open("example.txt", "r") as f:
    line = f.readline()
    while line:
        print(line, end='')  # Prints the line without adding another newline
        line = f.readline()
```

## Reading all lines as a list `readlines()`
The `readlines()` method reads all lines from the file and returns them as a list of strings:

```python
with open("example.txt", "r") as f:
    lines = f.readlines()
    for line in lines:
        print(line, end='')
```

## Iterating over the file object
You can also iterate over the file object directly, which is memory-efficient for large files:

```python
with open("example.txt", "r") as f:
    for line in f:
        print(line, end='')
```

## Writing strings to a file `write()`
The `write()` method writes a string to the file. If the file is opened in `'w'` mode, it will overwrite the file’s contents. If opened in `'a'` mode, it will append data to the end.

```python
with open("example.txt", "w") as f:
    f.write("Hello, World!\n")
    f.write("Writing to a file in Python is easy.")
```

## Writing multiple lines to a file `writelines()`
The `writelines()` method writes a list of strings to a file. It doesn’t automatically add newlines between lines, so you need to include `\n` at the end of each string if necessary.

```python
lines = ["Line 1\n", "Line 2\n", "Line 3\n"]
with open("example.txt", "w") as f:
    f.writelines(lines)
```

## Binary files
To work with binary files (like images, audio files, or any file that is not plain text), open the file in binary mode by adding `'b'` to the mode (e.g., `'rb'` for reading a binary file or `'wb'` for writing a binary file).

Example: Reading a binary file
```python
with open("image.png", "rb") as f:
    binary_data = f.read()
    print(binary_data)  # Outputs the raw bytes of the image
```

Example: Writing to a binary file
```python
with open("output.bin", "wb") as f:
    f.write(b'\x00\xFF\xAA\xBB')  # Writing some raw bytes to a file
```

## File modes summary
- **`'r'`** Open for reading (default). The file must exist.

- **`'w'`** Open for writing. Truncate the file if it exists.

- **`'a'`** Open for writing. Append to the end of the file.

- **`'b'`** Open in binary mode (used with 'r', 'w', or 'a').

- **`'x'`** Open for exclusive creation. Fails if the file exists.

- **`'t'`** Text mode (default).

- **`'+'`**	Open for reading and writing.

## File object methods
- **`read(size)`** Reads at most size characters (or bytes in binary mode).

- **`readline()`** Reads a single line from the file.

- **`readlines()`** Reads all the lines from the file as a list.

- **`write(string)	`** Writes the string to the file.

- **`writelines(lines)`** Writes a list of strings to the file.

- **`close()`** Closes the file.

## Managing file paths
Python's `os` and `pathlib` modules provide ways to handle file paths in a platform-independent way. You can use these to build paths, check if files exist, etc.

Using `os` module:
```python
import os

# Check if file exists
if os.path.exists("example.txt"):
    print("File exists")

# Get absolute file path
absolute_path = os.path.abspath("example.txt")
print(absolute_path)
```
Using pathlib module:
```python
from pathlib import Path

# Create a Path object
file_path = Path("example.txt")

# Check if the file exists
if file_path.exists():
    print(f"{file_path} exists")

# Get the absolute path
print(file_path.resolve())
```

## File exceptions
When dealing with files, errors may occur. Python provides exception handling to deal with these scenarios:

```python
try:
    with open("nonexistent.txt", "r") as f:
        content = f.read()
except FileNotFoundError:
    print("File not found!")
except IOError:
    print("An I/O error occurred")
```

## File handling best practices
- **Use the `with` statement**: This ensures the file is closed properly after you’re done with it, even if exceptions occur.

- **Handle exceptions**: Always handle potential errors, such as files not existing, using `try`/`except`.

- **Use appropriate modes**: Make sure you’re using the correct mode for reading, writing, or appending data to avoid accidentally overwriting data.

## File `tell()` method
The `tell()` method returns the current position of the file pointer, measured in bytes from the beginning of the file. It helps you know where you are in the file at any given time.

Usage of `tell()`
```python
with open("example.txt", "r") as f:
    # Read the first 10 characters
    content = f.read(10)
    
    # Get the current file pointer position
    position = f.tell()
    print(f"File pointer is at: {position} bytes")
```
In the above example, the file pointer will be at position 10 after reading the first 10 characters from the file.

## File `seek()` method
The `seek()` method is used to move the file pointer to a specific position in the file. This is useful when you want to read or write from a specific location in the file rather than from the current position.

Syntax of `seek()`
```python
f.seek(offset, whence)
```
- offset: The number of bytes to move the file pointer.
- whence: This is optional and specifies from where the offset should be applied. It can take one of the following values:
  - 0: Start of the file (default). Moves the pointer relative to the beginning of the file.
  - 1: Current file position. Moves the pointer relative to its current position.
  - 2: End of the file. Moves the pointer relative to the end of the file.

Example of `seek()`
```python
with open("example.txt", "r") as f:
    f.seek(5)  # Move the file pointer to the 5th byte from the beginning
    content = f.read(5)  # Read 5 characters starting from byte 5
    print(content)
```
In this example, the file pointer is moved to the 5th byte from the start, and the next 5 characters are read.

Using `seek()` with `whence` parameter
```python
with open("example.txt", "rb") as f:
    f.seek(0, 2)  # Move to the end of the file (whence=2)
    f.seek(-10, 2)  # Move back 10 bytes from the end of the file
    last_bytes = f.read(10)  # Read the last 10 bytes
    print(last_bytes)
```
In this example:
- The first `seek(0, 2)` moves the pointer to the end of the file.
- The second `seek(-10, 2)` moves the pointer 10 bytes back from the end.
- The `read(10)` reads the last 10 bytes of the file.

## `tell()` and `seek()` common use cases
- **Repositioning the file pointer**: You might want to skip certain portions of the file or re-read some part.
- **Random access**: When working with binary files or large files, you might need to jump to specific parts without reading the entire file.
- **Reading from or writing to specific locations**: You can use `seek()` to position the pointer at the right place before writing data.

Example: Reading the middle of a file
```python
with open("example.txt", "r") as f:
    # Move to the middle of the file
    middle = f.seek(50)  # Assume the file is at least 100 bytes long
    print(f.read(10))  # Read 10 bytes starting from the middle
```

## Saving data with json
In Python, you can use the `json` module to work with json, a popular format for storing and exchanging structured data. Python provides an easy way to serialize Python objects into JSON format and deserialize JSON back into Python objects.

To work with JSON data in Python, you'll primarily use the following methods from the json module:
- `json.dump()` Write Python object as a JSON formatted stream to a file.
- `json.dumps()` Serialize Python object to a JSON formatted string.
- `json.load()` Parse JSON from a file into a Python object.
- `json.loads()` Parse JSON from a string into a Python object.

## Saving structured data with `json.dump()`
You can save an object (like a dictionary or list) as a JSON file using `json.dump()`. This method serializes the object into JSON format and writes it to a file.

Example: Saving data to a JSON file
```python
import json

# Define some structured data (a Python dictionary)
data = {
    "name": "John",
    "age": 30,
    "is_student": False,
    "courses": ["Math", "Science"],
    "address": {
        "city": "New York",
        "zipcode": "10001"
    }
}

# Save the data as a JSON file
with open("data.json", "w") as json_file:
    json.dump(data, json_file, indent=4)  # indent=4 makes the JSON file more readable
```
In this example:
- The dictionary `data` is written to the `data.json` file.
- The `indent=4` argument ensures the JSON is formatted with indentation, making it easier to read.

## Reading json data with `json.load()`
To read structured data from a JSON file, use the `json.load()` method. This will parse the JSON file and convert it into an object (usually a dictionary or list).

Example: Reading data from a JSON file
```python
import json

# Read the data back from the JSON file
with open("data.json", "r") as json_file:
    data = json.load(json_file)

# Access the data
print(data["name"]) # Output: John
print(data["address"]["city"]) # Output: New York
```
In this example:
- The `json.load()` method is used to read the contents of `data.json` and convert it back into a dictionary.

## Converting objects to JSON strings with `json.dumps()`
If you want to convert an object into a JSON-formatted string (without saving it to a file), you can use `json.dumps()`.

Example: Convert dictionary to JSON string
```python
import json

data = {
    "name": "John",
    "age": 30,
    "is_student": False
}

# Convert Python object to JSON string
json_string = json.dumps(data, indent=4)

print(json_string)
```
In this example, the `json.dumps()` method converts the dictionary data into a JSON-formatted string that can be printed or sent over a network.

## Converting JSON strings to objects with `json.loads()`
You can parse a JSON-formatted string into an object using `json.loads()`.

Example: Convert JSON string to dictionary
```python
import json

json_string = '{"name": "John", "age": 30, "is_student": false}'

# Convert JSON string to Python object
data = json.loads(json_string)

print(data)  # Output: {'name': 'John', 'age': 30, 'is_student': False}
print(data["age"])  # Output: 30
```
Here, the `json.loads()` method converts a JSON string into a dictionary.

## Handling custom data types with `json.JSONEncoder`
By default, `json` can handle basic Python types like `str`, `int`, `list`, `dict` and `bool`. For custom data types, you need to write your own encoder.

**Example: Handling custom objects in JSON**
If you have a custom Python object (e.g., an instance of a class) that you want to convert to JSON, you need to define how the object should be serialized.

```python
import json

class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

# Define a custom encoding function
def person_encoder(obj):
    if isinstance(obj, Person):
        return {"name": obj.name, "age": obj.age}
    raise TypeError(f"Object of type {type(obj)} is not JSON serializable")

# Create a Person object
person = Person("Alice", 25)

# Serialize the Person object using the custom encoder
person_json = json.dumps(person, default=person_encoder, indent=4)

print(person_json)
```
This custom encoder converts a Person object into a dictionary that can be serialized to JSON.

## Working with nested json structures
JSON supports nested structures, meaning you can have lists of dictionaries, dictionaries inside dictionaries, etc. Python handles these easily.

Example: Nested structures
```python
import json

data = {
    "company": "ABC Corp",
    "employees": [
        {"name": "John", "age": 30},
        {"name": "Jane", "age": 25},
    ],
    "locations": {
        "headquarters": "New York",
        "branch": "San Francisco"
    }
}

# Save the nested data to a JSON file
with open("nested_data.json", "w") as json_file:
    json.dump(data, json_file, indent=4)

# Read the data back
with open("nested_data.json", "r") as json_file:
    data = json.load(json_file)

print(data["employees"][0]["name"])  # Output: John
```

## Error handling with json
When working with JSON, it’s common to encounter errors, especially when the data format is incorrect. You can handle such cases using `try`/`except`.

Example: Handling JSON decode error
```python
import json

json_string = '{"name": "John", "age": 30, "is_student": false'

try:
    data = json.loads(json_string)
except json.JSONDecodeError as e:
    print(f"Error decoding JSON: {e}")
```

## Enriching exceptions with notes
In Python 3.11 and later, you can enrich exceptions with additional information using the `add_note()` method. This allows you to add more context to the error, making it easier to debug complex problems. The notes don't change the original exception but append extra details that are displayed when the exception is printed or logged.

### Why use `add_note()`?
When exceptions occur in your code, it's often helpful to provide additional information that can help identify the cause of the problem. By enriching exceptions with notes, you can clarify error messages, provide contextual information, or offer hints for fixing the issue.

For example, if you're catching an error during file processing, you can add a note that includes the file path or details about the operation being attempted.

## How to use `add_note()`
The `add_note()` method can be called on any exception object to append a note. The note will be displayed along with the usual exception traceback when the exception is printed.

### Basic syntax
```python
exception_instance.add_note("This is additional context for the exception.")
```
**Example: Enriching exceptions with notes**
```python
try:
    raise ValueError("Invalid input!")
except ValueError as e:
    e.add_note("This occurred during input validation in the 'process_data' function.")
    e.add_note("Make sure the input is a valid number between 1 and 100.")
    raise
```
When this exception is raised, the output will look like this:
```python
Traceback (most recent call last):
  File "example.py", line 2, in <module>
    raise ValueError("Invalid input!")
ValueError: Invalid input!
  Note: This occurred during input validation in the 'process_data' function.
  Note: Make sure the input is a valid number between 1 and 100.
```

## Benefits of enriching exceptions
- **Increased clarity**: Additional context helps developers understand the circumstances of the error.

- **Improved debugging**: Notes can provide hints or background information, which can be especially useful when errors occur deep within the application.

- **Self-documenting errors**: By adding relevant information directly to the exception, you're effectively documenting the possible failure points in your code.

## Iterators
In Python, an iterator is an object that allows you to iterate over (traverse) a collection of values, such as a list, tuple, or dictionary, one element at a time. Iterators play a fundamental role in Python's for-loops and comprehension structures.

### Key concepts of iterators
- **Iterable**: An object capable of returning its elements one at a time. Examples include lists, tuples, sets, dictionaries, and strings. Any object that implements the `__iter__()` method is iterable.

- **Iterator**: An object that represents a stream of data. It is an object that implements two methods:
  - `__iter__()` Returns the iterator object itself.

  - `__next__()` Returns the next item from the iterator. If there are no more items, it raises the `StopIteration` exception.

## How iterators work
When a for loop iterates over an iterable, Python internally calls the `__iter__()` method to obtain an iterator object, and then repeatedly calls the `__next__()` method to retrieve each item from the iterator until the `StopIteration` exception is raised.

Example: Basic iteration
```python
# List (which is an iterable)
numbers = [1, 2, 3, 4]

# Get an iterator object
iterator = iter(numbers)

# Iterate using the iterator
print(next(iterator))  # Output: 1
print(next(iterator))  # Output: 2
print(next(iterator))  # Output: 3
print(next(iterator))  # Output: 4

# If we call next again, StopIteration is raised
# print(next(iterator))  # Raises StopIteration
```

## Manually creating an iterator
Any object in Python can be made into an iterator by implementing the `__iter__()` and `__next__()` methods.

Example: Custom iterator
```python
class MyIterator:
    def __init__(self, max_value):
        self.current = 0
        self.max_value = max_value

    def __iter__(self):
        return self

    def __next__(self):
        if self.current < self.max_value:
            value = self.current
            self.current += 1
            return value
        else:
            raise StopIteration

# Using the custom iterator
my_iter = MyIterator(5)
for num in my_iter:
    print(num)  # Output: 0, 1, 2, 3, 4
```
In this example, `MyIterator` class behaves like a built-in iterator. The `__iter__()` method returns the iterator object itself and `__next__()` returns the next item until it reaches `max_value`, after which it raises `StopIteration`.

## Using `iter()` and `next()`
- **`iter()`** This function returns an iterator object from an iterable.

- **`next()`** This function retrieves the next item from an iterator. If there are no more items, it raises StopIteration.

Example: Using `iter()` and `next()`
```python
# Using iter() on a list
numbers = [10, 20, 30]
it = iter(numbers)

# Using next() to retrieve elements
print(next(it))  # Output: 10
print(next(it))  # Output: 20
print(next(it))  # Output: 30
```

## Iterator vs iterable
- **Iterable**: Any object that can return an iterator. Examples: lists, tuples, strings.
  - Implements `__iter__()`.

- **Iterator**: An object that produces the next value from an iterable. It has:
  - `__iter__()` Returns the iterator object itself.
  - `__next__()` Returns the next value or raises `StopIteration` when the iteration ends.

Example: Iterable vs iterator
```python
# List is iterable, but not an iterator
numbers = [1, 2, 3]

# Using iter() to create an iterator from the list
iterator = iter(numbers)

# Now we can use next()
print(next(iterator))  # Output: 1
print(next(iterator))  # Output: 2
print(next(iterator))  # Output: 3
```

## Iterating over custom collections
You can make your custom collection class iterable by implementing the `__iter__()` method, which returns an iterator.

Example: Making a custom collection iterable
```python
class CustomCollection:
    def __init__(self, values):
        self.values = values

    def __iter__(self):
        return iter(self.values)  # Delegate iteration to the list's iterator

# Now, this class is iterable
my_collection = CustomCollection([10, 20, 30])

for item in my_collection:
    print(item)  # Output: 10, 20, 30
```

## Infinite iterators with `itertools`
`itertools` module provides several functions that return infinite iterators, such as `count()`, `cycle()` and `repeat()`.

Example: Infinite iterators
```python
import itertools

# Count from 0 indefinitely
for i in itertools.count(0):
    if i == 5:
        break
    print(i)  # Output: 0, 1, 2, 3, 4

# Cycle through a list indefinitely
counter = 0
for item in itertools.cycle(['A', 'B', 'C']):
    if counter == 6:
        break
    print(item)  # Output: A, B, C, A, B, C
    counter += 1
```

## Generators as iterators
A generator is a special type of iterator created using functions with the `yield` keyword. Unlike normal functions that return a single value and exit, generators yield a series of values, pausing between each one and resuming when `next()` is called.

Example: Generator function
```python
def my_generator():
    yield 1
    yield 2
    yield 3

gen = my_generator()

print(next(gen))  # Output: 1
print(next(gen))  # Output: 2
print(next(gen))  # Output: 3
```
Generator functions simplify the creation of iterators and provide a concise way to iterate over large data sets lazily, generating values only when needed.

## `os` module: Basic file and directory operations
- `os.getcwd()` Returns the current working directory.
- `os.chdir(path)` Changes the current working directory to the given path.
- `os.listdir(path)` Lists the files and directories in the specified path.
- `os.mkdir(path)` Creates a new directory at the given path.
- `os.rmdir(path)` Removes an empty directory.
- `os.remove(path)` Removes a file.

Example: Working with directories
```python
import os

# Get current working directory
print("Current directory:", os.getcwd())

# Create a new directory
os.mkdir("new_directory")

# Change working directory
os.chdir("new_directory")
print("Changed to:", os.getcwd())

# List contents of current directory
print(os.listdir("."))

# Go back to the original directory
os.chdir("..")
os.rmdir("new_directory")  # Remove the directory
```

## `os` module: File path operations
- `os.path.join(path, *paths)` Joins one or more path components.
- `os.path.exists(path)` Checks if a given path exists.
- `os.path.isfile(path)` Checks if the path is a file.
- `os.path.isdir(path)` Checks if the path is a directory.
- `os.path.abspath(path)` Returns the absolute path.
- `os.path.basename(path)` Returns the base name of the path.
- `os.path.dirname(path)` Returns the directory name of the path.
- `os.path.split(path)` Splits the path into a directory and file name.
- `os.path.abspath(path)` Returns the absolute path for the given relative path.

Example: Path manipulation
```python
import os

path = "/home/user/docs/file.txt"

# Get the directory name
dir_name = os.path.dirname(path)
print("Directory name:", dir_name)

# Get the base name
base_name = os.path.basename(path)
print("Base name:", base_name)

# Check if path exists
if os.path.exists(path):
    print("Path exists.")

# Check if it's a file
if os.path.isfile(path):
    print("It's a file.")

# Join paths
new_path = os.path.join("/home/user", "new_folder", "new_file.txt")
print("Joined path:", new_path)
```

## `os` module: Environment variables
The os module provides access to the environment variables of the operating system.

### Common environment functions:
- `os.environ` A mapping object representing the environment variables.

- `os.getenv(key, default=None)` Returns the value of the environment variable key, or default if the key doesn't exist.

- `os.putenv(key, value)` Sets the environment variable key to value.

- `os.unsetenv(key)` Deletes the environment variable key.

### Example: Environment variables
```python
import os

# Get the value of the 'HOME' environment variable
home_dir = os.getenv('HOME')
print("Home Directory:", home_dir)

# Set a new environment variable
os.environ['MY_VAR'] = '12345'
print("MY_VAR:", os.getenv('MY_VAR'))

# Delete the environment variable
os.unsetenv('MY_VAR')
```

## `os` module: Process management
The `os` module provides functions to interact with system processes, including executing shell commands, managing process IDs, and terminating processes.

### Key process functions:
- `os.system(command)` Executes the command in a subshell.

- `os.execvp(file, args)` Replaces the current process with the executable file and passes args as the arguments.

- `os.getpid()` Returns the process ID of the current process.

- `os.getppid()` Returns the process ID of the parent process.

- `os.kill(pid, sig)` Sends the signal sig to the process with ID pid.

### Example: Running a system command
```python
import os

# Run a system command (e.g., list files)
os.system('ls')

# Get the current process ID
print("Process ID:", os.getpid())
```

## `os` module: Working with file descriptors
The `os` module allows low-level file I/O using file descriptors, providing more control over how files are opened, read, and written.

### Key file descriptor functions:
- `os.open(path, flags)` Opens the file at path with the specified flags. Returns a file descriptor.

- `os.read(fd, n)` Reads n bytes from the file descriptor fd.

- `os.write(fd, str)` Writes the bytes in str to the file descriptor fd.

- `os.close(fd)` Closes the file descriptor fd.

### Example: Working with file descriptors
```python
import os

# Open a file for reading
fd = os.open('example.txt', os.O_RDONLY)

# Read 100 bytes from the file
data = os.read(fd, 100)
print("Data read:", data)

# Close the file
os.close(fd)
```

## `os` module: Working with the `os.walk()` function
The `os.walk()` function allows you to iterate over the directory tree, yielding the directory path, subdirectories, and files.

Example: Walking through a directory tree
```python
import os

for dirpath, dirnames, filenames in os.walk('/path/to/directory'):
    print(f"Directory: {dirpath}")
    for dirname in dirnames:
        print(f"Sub-directory: {dirname}")
    for filename in filenames:
        print(f"File: {filename}")
```

## `os` module: Temporary files and directories
The `os` module, along with the `tempfile` module, allows you to create temporary files and directories.

### Example: Creating temporary files
```python
import os
import tempfile

# Create a temporary file
with tempfile.NamedTemporaryFile(delete=False) as temp_file:
    temp_file.write(b"Temporary file content")
    print(f"Temporary file name: {temp_file.name}")

# Temporary file will be deleted when the program exits
```

## `shutil` module: Copying files and directories
The `shutil` module offers several ways to copy files and directories.

- `shutil.copy(src, dst)` Copies a file from src to dst. The metadata (like timestamps) is not preserved.

- `shutil.copy2(src, dst)` Copies a file from src to dst and preserves metadata such as timestamps.

- `shutil.copyfile(src, dst)` Copies the contents of the file src to dst without metadata.

- `shutil.copytree(src, dst)` Recursively copies an entire directory tree from src to dst.

### Example: Copying files
```python
import shutil

# Copy a file (without preserving metadata)
shutil.copy('source.txt', 'destination.txt')

# Copy a file (with metadata)
shutil.copy2('source.txt', 'destination_with_metadata.txt')

# Copy an entire directory tree
shutil.copytree('source_directory', 'destination_directory')
```

## `shutil` module: Moving files and directories
- `shutil.move(src, dst)` Moves a file or directory from src to dst. It can also rename files or directories if the source and destination are on the same filesystem.

### Example: Moving files
```python
import shutil

# Move a file to a new location
shutil.move('old_file.txt', 'new_location.txt')

# Move a directory
shutil.move('source_directory', 'destination_directory')
```

## `shutil` module: Removing files and directories
- shutil.rmtree(path): Recursively deletes a directory and all its contents (files and subdirectories).

### Example: Removing a directory and its contents
```python
import shutil

# Remove an entire directory tree
shutil.rmtree('directory_to_remove')
```

## `shutil` module: Archiving files and directories
The `shutil` module provides tools to create and extract archives (e.g., zip or tar files).

- `shutil.make_archive(base_name, format, root_dir)` Creates an archive file (e.g., zip, tar) from a directory.

  - `base_name`: The name of the archive (without the extension).
  - `format`: The format of the archive (e.g., 'zip', 'tar', 'gztar', 'bztar').
  - `root_dir`: The directory to be archived.

- `shutil.unpack_archive(filename, extract_dir=None, format=None)` Extracts an archive (e.g., zip or tar) to a directory.

### Example: Creating and extracting archives
```python
import shutil

# Create a ZIP archive of the 'my_folder' directory
shutil.make_archive('my_archive', 'zip', 'my_folder')

# Extract the ZIP archive
shutil.unpack_archive('my_archive.zip', 'extracted_folder')
```

## `shutil` module: Disk usage
- `shutil.disk_usage(path)` Returns the disk usage statistics for the given path as a tuple: (total, used, free).

### Example: Checking disk usage
```python
import shutil

# Get disk usage of the root directory
total, used, free = shutil.disk_usage('/')

print(f"Total: {total} bytes, Used: {used} bytes, Free: {free} bytes")
```

## `shutil` module: File system operations
- `shutil.chown(path, user=None, group=None)` Changes the owner and/or group of a file or directory. This is useful for Unix-like systems.

### Example: Changing ownership of a file
```python
import shutil

# Change the owner and group of a file
shutil.chown('myfile.txt', user='newuser', group='newgroup')
```

## `shutil` module: Error handling
The `shutil` module provides an error-handling mechanism that is helpful when dealing with file operations that might fail, such as permissions issues or missing files.

- `shutil.Error` A base class for exceptions raised by `shutil` functions.

### Example: Handling errors
```python
import shutil

try:
    shutil.move('non_existent_file.txt', 'new_location.txt')

except shutil.Error as e:
    print(f"Error occurred: {e}")
```

## Common string validation methods
Python provides several built-in string methods to validate the contents of strings. These methods help check if a string contains specific types of characters (e.g., alphabetic, numeric, etc.). These validation methods return boolean values (`True` or `False`), making them ideal for conditional checks.

- `isalpha()` Checks if all characters are alphabetic.

- `isdigit()` Checks if all characters are digits.

- `isalnum()` Checks if all characters are alphanumeric.

- `isdecimal()` Checks if all characters are decimal characters.

- `isnumeric()` Checks if all characters are numeric.

- `islower()` Checks if all alphabetic characters are lowercase.

- `isupper()` Checks if all alphabetic characters are uppercase.

- `istitle()` Checks if the string is in title case.

- `isspace()` Checks if the string contains only whitespace characters.

- `isascii()` Checks if all characters are ASCII.

- `isprintable()` Checks if all characters are printable.

- `isidentifier()` Checks if the string is a valid Python identifier.

## What are context managers?
A context manager is a construct that sets something up, lets you use it, and then cleans up automatically, no matter what happens (even if there's an error).

Most commonly used with the `with` statement:
```python
with open('example.txt', 'r') as file:
    data = file.read()
```

Under the hood, context managers use two special methods:
- `__enter__()` called when the with block is entered.
- `__exit__()` called when the with block is exited.

## Custom context manager example
```python
class MyContext:
    def __enter__(self):
        print("Entering context")
        return "resource"

    def __exit__(self, exc_type, exc_val, exc_tb):
        print("Exiting context")

with MyContext() as value:
    print(f"Using {value}")
```
Output:
```
Entering context
Using resource
Exiting context
```

## Real-world uses of context managers
- **File handling**: `open()` (auto-closes files)

- **Database connections**: auto-commits or rolls back

- **Locking/mutexes**: acquires and releases locks

- **Temporary settings**: change something temporarily and revert after

- **Resource management**: open/close network sockets, sessions, etc.

## The `contextlib` module
Python provides tools to build context managers easily, like contextlib.contextmanager:
```python
from contextlib import contextmanager

@contextmanager
def simple_context():
    print("Start")
    yield "Hello"
    print("End")

with simple_context() as msg:
    print(msg)
```
Output:
```
Start
Hello
End
```

## Why use context managers?
- Ensures resources are cleaned up properly

- Makes code more readable and concise

- Reduces risk of bugs (like forgetting to close a file)
