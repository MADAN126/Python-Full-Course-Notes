# PYTHON KEYWORDS

## Definition

Keywords are reserved words in Python.

- They already have predefined meanings.
- Python uses them to understand the structure of your code.
- They **cannot** be used as identifiers (variable names, function names, class names, etc.).

---

## Why Do Keywords Exist?

Python needs certain words to represent specific operations.

Examples:

| Keyword | Purpose |
|----------|-----------|
| `if` | Conditional statements |
| `for` | Loops |
| `class` | Creating classes |
| `def` | Defining functions |
| `try` | Exception handling |

Without reserved words, Python would not know how to interpret code correctly.

---

## Example

### Invalid

```python
if = 10
```

Output:

```python
SyntaxError
```

Reason:

`if` already has a predefined meaning.

---

### Valid

```python
number = 10
name = "John"
```

---

## keyword Module

Python provides the `keyword` module to work with keywords.

### Import

```python
import keyword
```

---

## List All Keywords

```python
import keyword

print(keyword.kwlist)
```

Output:

```python
[
'False', 'None', 'True',
'and', 'as', 'assert',
'async', 'await',
'break',
'class',
'continue',
'def',
'del',
'elif',
'else',
'except',
'finally',
'for',
'from',
'global',
'if',
'import',
'in',
'is',
'lambda',
'nonlocal',
'not',
'or',
'pass',
'raise',
'return',
'try',
'while',
'with',
'yield'
]
```

---

## Number of Keywords

```python
len(keyword.kwlist)
```

Output:

```python
35
```

This means the Python version being used contains 35 keywords.

---

## Check Whether a Word Is a Keyword

```python
import keyword

print(keyword.iskeyword("if"))
print(keyword.iskeyword("hello"))
```

Output:

```python
True
False
```

Explanation:

- `"if"` → Keyword
- `"hello"` → Not a keyword

---

## Commonly Used Keywords

### Conditional Statements

```python
if
elif
else
```

Example:

```python
age = 18

if age >= 18:
    print("Adult")
else:
    print("Minor")
```

---

### Loops

```python
for
while
break
continue
```

Example:

```python
for i in range(3):
    print(i)
```

---

### Functions

```python
def
return
lambda
```

Example:

```python
def add(a, b):
    return a + b
```

---

### Exception Handling

```python
try
except
finally
raise
```

Example:

```python
try:
    x = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")
```

---

### Import Statements

```python
import
from
as
```

Example:

```python
from math import sqrt as s

print(s(25))
```

---

### Boolean and Special Values

```python
True
False
None
```

Example:

```python
is_active = True
value = None
```

---

## Execution Flow

```
Python Code
     ↓
Tokenizer
     ↓
Parser
     ↓
Checks each word
     ↓
Keyword?
 ┌───────────┐
 │           │
Yes         No
 │           │
Use       Treat as
special   identifier
meaning
```

---

## Important Points

- Keywords are reserved words.
- They cannot be used as identifiers.
- The `keyword` module provides utilities related to keywords.
- `keyword.kwlist` returns all keywords.
- `keyword.iskeyword()` checks whether a word is a keyword.
- The number of keywords may vary across Python versions.

---

## Quick Revision

```text
Keywords
↓
Reserved words in Python
↓
Cannot be used as identifiers
↓
keyword.kwlist → List all keywords
↓
keyword.iskeyword(word) → Check a keyword
↓
Current version shown here → 35 keywords
```
