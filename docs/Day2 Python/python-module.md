# Python Module

A Python module is a file containing Python code that defines functions, classes, variables, and runnable code. Modules help organize Python code logically, making it easier to reuse and maintain

**Key Concepts of Python Modules:**  
1 Definition:

- A Python module is a .py file that contains Python definitions and statements. The module name is the filename without the .py extension.
- For example, a file named math_operations.py is a module called math_operations.

2 Importing Modules:

- You can import and use functions, classes, and variables from a module into another script using the import statement.

```
mkdir module
cd module
```

```py title="math_operations.py"
# math_operations.py

def add(a: float, b: float) -> float:
    """Returns the sum of two numbers."""
    return a + b

def subtract(a: float, b: float) -> float:
    """Returns the difference of two numbers (a - b)."""
    return a - b

def multiply(a: float, b: float) -> float:
    """Returns the product of two numbers."""
    return a * b

def divide(a: float, b: float) -> float:
    """Returns the quotient of two numbers (a / b). Raises an error if b is 0."""
    if b == 0:
        raise ValueError("Cannot divide by zero.")
    return a / b

def power(base: float, exponent: int) -> float:
    """Returns the result of raising base to the power of exponent."""
    return base ** exponent

def square_root(a: float) -> float:
    """Returns the square root of a number."""
    if a < 0:
        raise ValueError("Cannot compute the square root of a negative number.")
    return a ** 0.5

def absolute(a: float) -> float:
    """Returns the absolute value of a number."""
    return abs(a)

print(__name__)
```

import module

```py title="math_lab1.py"
# Importing a module
import math_operations

# Using a function from the module
result = math_operations.add(5, 3)
print(result)
```

Alternatively, you can import specific items from a module using from ... import:

```py title="math_lab2.py"
from math_operations import add
result = add(5, 3)
print(result)

```

Built-in Modules:

- Python comes with a large standard library of modules that provide built-in functionality.
- Common examples include:

  - math: Mathematical functions (sqrt(), sin(), etc.)
  - os: Operating system-related functionality (file handling, directory management)
  - sys: System-specific parameters and functions
  - random: Random number generation
  - datetime: Working with dates and times

Example os module:

```py title="module_lab1.py"
import os

# 1. Get the current working directory
current_directory = os.getcwd()
print(f"Current working directory: {current_directory}")

# 2. List all files and directories in the current directory
files_and_dirs = os.listdir(current_directory)
print(f"Files and directories in '{current_directory}': {files_and_dirs}")

# 3. Make a new directory
new_dir = "example_directory"
os.mkdir(new_dir)
print(f"Created new directory: {new_dir}")

# 4. Change the current working directory
os.chdir(new_dir)
print(f"Changed directory to: {os.getcwd()}")

# 5. Get environment variables
path = os.getenv('PATH')
print(f"PATH environment variable: {path}")

# 6. Remove the directory (must be empty)
os.chdir('..')  # Go back to the original directory before removing
os.rmdir(new_dir)
print(f"Removed directory: {new_dir}")


```

**Key Functions:**

- os.getcwd(): Returns the current working directory.
- os.listdir(path): Returns a list of files and directories in the specified path.
- os.mkdir(path): Creates a new directory.
- os.chdir(path): Changes the current working directory to the specified path.
- os.getenv(name): Returns the value of an environment variable (e.g., 'PATH').
- os.rmdir(path): Removes an empty directory.

Example sys module:

```py title="module_lab2.py"
import sys

# 1. Get the Python version
python_version = sys.version
print(f"Python version: {python_version}")

# 2. Get the platform (e.g., Windows, Linux, macOS)
platform = sys.platform
print(f"Platform: {platform}")

# 3. Get the command-line arguments passed to the script
print("Command-line arguments:")
for arg in sys.argv:
    print(arg)

# 4. Exiting the program with a status code
if len(sys.argv) < 2:
    print("No argument provided. Exiting with status 1.")
    sys.exit(1)
else:
    print(f"Argument passed: {sys.argv[1]}")

# 5. Get the size of an object (in bytes)
import os
file_size = os.path.getsize('example_file.txt')  # Replace with an actual file
print(f"Size of 'example_file.txt': {file_size} bytes")

# 6. Add a directory to the module search path
sys.path.append('/path/to/your/modules')
print(f"Updated sys.path: {sys.path}")
```

Key Functions:

- sys.version: Returns the Python version as a string.
- sys.platform: Returns the platform on which Python is running (e.g., 'win32', 'linux').
- sys.argv: A list of command-line arguments passed to the script. The first element is the script name, followed by any arguments.
- sys.exit([status]): Exits the program with an optional status code (default is 0 for success).
- sys.path.append(path): Adds a directory to the Python module search path, enabling you to import modules from non-standard locations.

| **Module** | **Function**            | **Description**                                   |
| ---------- | ----------------------- | ------------------------------------------------- |
| `os`       | `os.getcwd()`           | Get the current working directory.                |
|            | `os.listdir(path)`      | List files and directories in the specified path. |
|            | `os.mkdir(path)`        | Create a new directory.                           |
|            | `os.chdir(path)`        | Change the current working directory.             |
|            | `os.getenv(name)`       | Get the value of an environment variable.         |
|            | `os.rmdir(path)`        | Remove an empty directory.                        |
| `sys`      | `sys.version`           | Get the Python version.                           |
|            | `sys.platform`          | Get the platform type (e.g., Windows, Linux).     |
|            | `sys.argv`              | Get command-line arguments passed to the script.  |
|            | `sys.exit([status])`    | Exit the program with an optional status code.    |
|            | `sys.path.append(path)` | Add a directory to the module search path.        |

## `__main__`

The **name** Variable:

The special **name** variable helps distinguish whether a Python file is being run as a script or being imported as a module.
If the file is being run directly, **name** is set to "**main**". If it is imported as a module, **name** is set to the module's name.

```py title="module_lab3.py"
def main():
    print("call when run script")
    print(__name__)

if __name__ == "__main__":
    print("This is a script")
    main()
else:
    print("This is imported as a module")
```

!!! info 'What is **name** == "**main**" '

    `__name__` variable will return `__name__` when run as script directly
    `__name__` variable will return "nameof library"

```py title="module_lab3.py modify"
import math_operations

def main():
    print("call when run script")
    print(__name__)

if __name__ == "__main__":
    print("This is a script")
    main()
else:
    print("This is imported as a module")
```
