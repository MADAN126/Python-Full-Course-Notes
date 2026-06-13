# STATEMENTS IN PYTHON

## Definition

A statement is an instruction that Python can execute.

When Python reads a statement, it performs the specified action.

Examples of actions:

- Assigning values
- Performing calculations
- Creating collections
- Calling functions
- Controlling program flow

---

# Examples of Statements

```python
x = 10
```

Assigns a value.

---

```python
print("Hello")
```

Displays output.

---

```python
a = b + c
```

Performs a calculation and stores the result.

---

# Single-Line Statements

A complete instruction written on a single line.

## Example 1

```python
p1 = 10 + 20
```

Execution:

```text
10 + 20
↓
30
↓
Store in p1
```

Output:

```python
p1
```

```python
30
```

---

## Example 2

```python
p2 = ['a', 'b', 'c', 'd']
```

Execution:

```text
Create list
↓
Store in p2
```

Output:

```python
p2
```

```python
['a', 'b', 'c', 'd']
```

---

# Multi-Line Statements

Sometimes a statement becomes too long.

Python allows a single statement to span multiple lines.

There are two ways to do this.

---

# 1. Explicit Line Continuation (`\`)

Use a backslash (`\`) to tell Python:

> "This statement continues on the next line."

Example:

```python
p1 = 20 + 30 \
     + 40 + 50 \
     + 70 + 80
```

Execution:

```text
20 + 30 + 40 + 50 + 70 + 80
↓
290
↓
Store in p1
```

Output:

```python
290
```

---

# How Python Reads It

Python combines the lines first.

```python
p1 = 20 + 30 \
     + 40 + 50
```

becomes:

```python
p1 = 20 + 30 + 40 + 50
```

Then executes it.

---

# Important Rule

The backslash must be the last character on the line.

❌ Invalid

```python
p1 = 20 + 30 \    # Space after \
     + 40
```

This may produce errors.

---

✅ Valid

```python
p1 = 20 + 30 \
     + 40
```

---

# 2. Implicit Line Continuation

When statements are enclosed within:

```python
()
[]
{}
```

Python automatically understands that the statement continues.

No backslash is needed.

---

## List Example

```python
p2 = [
    'a',
    'b',
    'c',
    'd'
]
```

Output:

```python
['a', 'b', 'c', 'd']
```

---

# How Python Reads It

```text
Opening [
↓
Keep reading lines
↓
Find closing ]
↓
Execute statement
```

---

# Other Examples

## Parentheses

```python
total = (
    10 +
    20 +
    30
)

print(total)
```

Output:

```python
60
```

---

## Dictionaries

```python
student = {
    "name": "John",
    "age": 21,
    "city": "Chennai"
}

print(student)
```

Output:

```python
{'name': 'John', 'age': 21, 'city': 'Chennai'}
```

---

# Single-Line vs Multi-Line Statements

| Feature | Single-Line | Multi-Line |
|----------|------------|------------|
| Number of lines | One | Multiple |
| Readability | Good for short statements | Better for long statements |
| Uses `\` | No | Sometimes |
| Uses `() [] {}` | Optional | Common |
| Execution | Immediate | Combined before execution |

---

# Execution Flow

```text
Python reads a statement
          ↓
Is it complete?
      ↓        ↓
     Yes       No
      ↓         ↓
 Execute    Continue reading
                ↓
       Statement completed
                ↓
            Execute
```

---

# Important Points

- A statement is an instruction executed by Python.
- Single-line statements occupy one line.
- Multi-line statements occupy multiple lines.
- Backslash (`\`) provides explicit line continuation.
- `()`, `[]`, and `{}` provide implicit line continuation.
- Python combines multi-line statements before execution.

---

# Quick Revision

```text
Statement
↓
Instruction executed by Python

Single-Line
↓
One line
Example:
x = 10

Multi-Line
↓
Multiple lines

Explicit Continuation
↓
Use \

Implicit Continuation
↓
Use (), [], {}
```
