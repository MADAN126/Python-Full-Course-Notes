# Python Docstrings

## What is a Docstring?

A docstring (Documentation String) is a string literal used to describe the purpose, behavior, usage, or functionality of a module, function, class, or method.

Docstrings act as built-in documentation and help programmers understand what a piece of code does without reading its implementation.

---

## Why are Docstrings Needed?

When programs become large, it becomes difficult to remember the purpose of every function or class.

Docstrings provide:

- Self-documentation
- Better code readability
- Easier maintenance
- Quick understanding of functionality
- Support for automatic documentation generation tools

---

## Where is a Docstring Written?

A docstring must be the first statement inside a:

- Function
- Method
- Class
- Module

It is written immediately after the definition.

### Syntax

```python
def function_name():
    """Docstring"""
    statements
```

---

## Function Docstring Example

```python
def square(num):
    """Returns the square of a number"""
    return num ** 2
```

Calling the function:

```python
square(5)
```

Output:

```text
25
```

---

## Accessing a Docstring

Every function stores its docstring in a special attribute called `__doc__`.

```python
print(square.__doc__)
```

Output:

```text
Returns the square of a number
```

---

## How Python Stores a Docstring

```python
def square(num):
    """Returns the square of a number"""
    return num ** 2
```

Python internally stores:

```text
square
 ├── code
 └── __doc__
```

The documentation becomes part of the function object.

---

## Example: Even or Odd Function

```python
def evenodd(num):
    """
    Determines whether a number is even or odd.
    """

    if num % 2 == 0:
        print("Even Number")
    else:
        print("Odd Number")
```

Calling:

```python
evenodd(2)
```

Output:

```text
Even Number
```

Calling:

```python
evenodd(3)
```

Output:

```text
Odd Number
```

Viewing documentation:

```python
print(evenodd.__doc__)
```

Output:

```text
Determines whether a number is even or odd.
```

---

## Multi-Line Docstrings

Docstrings can span multiple lines.

```python
def add(a, b):
    """
    Adds two numbers.

    Parameters:
        a : First number
        b : Second number

    Returns:
        Sum of a and b
    """
    return a + b
```

This is useful when detailed explanations are needed.

---

## Docstring vs Comment

### Comment

```python
# Calculate square
return num ** 2
```

- Intended for programmers reading the source code.
- Ignored by Python.
- Cannot be accessed during runtime.

---

### Docstring

```python
"""Returns the square of a number"""
```

- Intended as official documentation.
- Stored by Python.
- Can be accessed using `__doc__`.
- Used by help systems and documentation tools.

---

## Using help()

Python can automatically display docstrings using `help()`.

```python
help(square)
```

Output:

```text
Help on function square:

square(num)
    Returns the square of a number
```

---

## Class Docstring Example

```python
class Student:
    """Represents a student object."""

    def __init__(self, name):
        self.name = name
```

Accessing:

```python
print(Student.__doc__)
```

Output:

```text
Represents a student object.
```

---

## Module Docstring Example

```python
"""
This module contains utility functions
for mathematical operations.
"""
```

A module docstring is placed at the top of a Python file.

---

## Best Practices

- Write meaningful descriptions.
- Explain what the function does, not how it does it.
- Keep simple functions concise.
- Use multi-line docstrings for complex functions.
- Place the docstring immediately after the definition.

---

## Key Points

- A docstring is a documentation string.
- It is written immediately after a function, class, method, or module definition.
- Python stores docstrings in the `__doc__` attribute.
- Docstrings can be viewed using `__doc__` or `help()`.
- They improve readability, maintainability, and documentation.
- Unlike comments, docstrings are available at runtime.

---

## Interview Definition

**A docstring is a special string literal written immediately after the definition of a module, function, class, or method. It is used to document the purpose and behavior of the code and can be accessed using the `__doc__` attribute or the `help()` function.**