# COMMENTS IN PYTHON

## Definition

Comments are pieces of text written inside the code that Python ignores during execution.

They are used to:

- Explain the code.
- Improve readability.
- Leave notes for yourself or other developers.
- Temporarily disable code during testing.

---

# Do Comments Execute?

No.

Python skips comments completely.

Example:

```python
# This line explains the code

x = 10

print(x)
```

Output:

```python
10
```

Python ignores:

```python
# This line explains the code
```

---

# Single-Line Comments

Use the `#` symbol.

Everything after `#` on that line becomes a comment.

Syntax:

```python
# comment
```

Example:

```python
# Store student's age
age = 20

print(age)
```

Output:

```python
20
```

---

# Multiple Single-Line Comments

You can write several single-line comments.

Example:

```python
# Calculate total marks
# Add bonus marks
# Display final score

total = 450

print(total)
```

Output:

```python
450
```

---

# Multi-Line Comments

Python does not have a dedicated multi-line comment syntax.

Instead, developers often use triple quotes.

Example:

```python
'''
This is a
multi-line comment.
'''
```

or

```python
"""
This is a
multi-line comment.
"""
```

---

# Example

```python
'''
Program to calculate area
of a rectangle
'''

length = 10
width = 5

print(length * width)
```

Output:

```python
50
```

---

# Triple Quotes: Important Note

Triple quotes are actually used to create **multi-line strings**.

Example:

```python
text = """
Hello
Python
"""
```

Here,

```python
text
```

contains a string value.

---

If triple-quoted strings are not assigned to a variable, Python simply creates the string and discards it.

Example:

```python
"""
Temporary explanation
"""
```

This behaves like a comment.

---

# Comment vs String

## Comment

```python
# This is ignored by Python
```

Characteristics:

- Ignored completely.
- Cannot be accessed.
- Used only for explanation.

---

## Triple-Quoted String

```python
"""
Hello
"""
```

Characteristics:

- Creates a string object.
- Can be stored in variables.
- Used for documentation (docstrings).

Example:

```python
message = """
Hello
Python
"""

print(message)
```

Output:

```python
Hello
Python
```

---

# Docstrings

Triple quotes are commonly used to document functions, classes, and modules.

Example:

```python
def add(a, b):
    """
    Returns the sum of two numbers.
    """
    return a + b
```

Accessing the documentation:

```python
print(add.__doc__)
```

Output:

```python
Returns the sum of two numbers.
```

---

# Why Use Comments?

- Explain complex logic.
- Describe the purpose of code.
- Improve maintainability.
- Help team members understand the code.
- Document assumptions and warnings.

---

# Bad Comments

Avoid obvious comments.

❌

```python
x = x + 1    # Increment x by 1
```

The code already explains itself.

---

# Good Comments

Explain the reason behind the code.

✅

```python
# Add one extra attempt because the API
# occasionally returns incomplete results.

attempts += 1
```

---

# Important Points

- `#` is the official way to write comments in Python.
- Python ignores comments during execution.
- Triple quotes create multi-line strings.
- Unassigned triple-quoted strings are often used as multi-line comments.
- Triple quotes are mainly used for docstrings.

---

# Quick Revision

```text
Comments
↓
Used to explain code
↓
Ignored by Python

Single-line
↓
# comment

Multi-line (commonly used)
↓
''' comment '''
or
""" comment """

Triple quotes
↓
Actually create strings
↓
Used mainly for docstrings
```
