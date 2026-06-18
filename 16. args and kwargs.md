# *args AND **kwargs IN PYTHON

## The Problem

Suppose you write:

```python
def add(a, b, c):
    return a + b + c
```

This function expects exactly 3 arguments.

Valid:

```python
add(10, 20, 30)
```

Output:

```python
60
```

---

Invalid:

```python
add(1, 2, 3, 4)
```

Output:

```python
TypeError
```

Reason:

```text
Expected → 3 arguments
Received → 4 arguments
```

Sometimes we don't know how many arguments users will pass.

Python solves this using:

```python
*args
**kwargs
```

---

# *args

## Definition

`*args` allows a function to accept any number of positional (non-keyword) arguments.

Syntax:

```python
def function(*args):
    pass
```

---

# How It Works

Python collects all extra positional arguments into a tuple.

Example:

```python
def show(*args):
    print(args)
```

Call:

```python
show(10, 20, 30)
```

Output:

```python
(10, 20, 30)
```

---

# Example: Dynamic Addition

```python
def add(*args):
    return sum(args)
```

Calls:

```python
print(add(1, 2, 3))
print(add(1, 2, 3, 4))
print(add(1, 2, 3, 4, 5))
```

Output:

```python
6
10
15
```

---

# args Is Just a Name

This works:

```python
def add(*numbers):
    print(numbers)
```

Example:

```python
add(1, 2, 3)
```

Output:

```python
(1, 2, 3)
```

Only the `*` is important.

Best practice:

```python
*args
```

---

# Iterating Through *args

Example:

```python
def show(*args):
    for value in args:
        print(value)
```

Call:

```python
show("A", "B", "C")
```

Output:

```python
A
B
C
```

---

# Argument Unpacking with *

Suppose:

```python
numbers = [1, 2, 3]
```

Function:

```python
def add(a, b, c):
    return a + b + c
```

Call:

```python
add(*numbers)
```

Python converts:

```python
[1, 2, 3]
```

into:

```python
add(1, 2, 3)
```

Output:

```python
6
```

---

# Example

```python
def some_args(arg1, arg2, arg3):
    print(arg1)
    print(arg2)
    print(arg3)

my_list = [2, 3]

some_args(1, *my_list)
```

Output:

```python
1
2
3
```

---

# Multiple Unpacking

Example:

```python
list1 = [1, 2]
list2 = [3, 4]

print(*list1, *list2)
```

Output:

```python
1 2 3 4
```

---

# **kwargs

## Definition

`**kwargs` allows a function to accept any number of keyword arguments.

Syntax:

```python
def function(**kwargs):
    pass
```

---

# How It Works

Python collects keyword arguments into a dictionary.

Example:

```python
def details(**kwargs):
    print(kwargs)
```

Call:

```python
details(Name="Asif", Age=33)
```

Output:

```python
{
    'Name': 'Asif',
    'Age': 33
}
```

---

# kwargs Is Also Just a Name

This works:

```python
def details(**data):
    print(data)
```

Only:

```python
**
```

matters.

Best practice:

```python
**kwargs
```

---

# Iterating Through **kwargs

Example:

```python
def details(**kwargs):
    for key, value in kwargs.items():
        print(key, ":", value)
```

Call:

```python
details(Name="Asif", Country="India")
```

Output:

```python
Name : Asif
Country : India
```

---

# Dictionary Unpacking with **

Dictionary:

```python
person = {
    "Name": "Asif",
    "Age": 33
}
```

Function:

```python
def details(**kwargs):
    print(kwargs)
```

Call:

```python
details(**person)
```

Python converts:

```python
details(
    Name="Asif",
    Age=33
)
```

Output:

```python
{
    'Name': 'Asif',
    'Age': 33
}
```

---

# Using All Types Together

Example:

```python
def UserDetails(
    licenseNo,
    *args,
    phoneNo=0,
    **kwargs
):
    print("License:", licenseNo)

    print("Name:")
    for value in args:
        print(value, end="")

    print("\nPhone:", phoneNo)

    for key, value in kwargs.items():
        print(key, ":", value)
```

Call:

```python
name = ["Asif", " ", "Ali", " ", "Bhat"]

info = {
    "Country": "India",
    "Age": 33
}

UserDetails(
    "BHT145",
    *name,
    phoneNo=1234567890,
    **info
)
```

Output:

```python
License: BHT145
Name:
Asif Ali Bhat
Phone: 1234567890
Country : India
Age : 33
```

---

# Order of Parameters

Correct order:

```python
def func(
    positional,
    *args,
    default_value=0,
    **kwargs
):
    pass
```

---

# Invalid Order

## Example 1

```python
def func(**kwargs, *args):
    pass
```

Output:

```python
SyntaxError
```

Reason:

```text
*args must come before **kwargs
```

---

## Example 2

```python
def func(ID=1, licenseNo):
    pass
```

Output:

```python
SyntaxError
```

Reason:

```text
Non-default argument follows default argument
```

---

# Parameter Order Rules

```text
1. Positional parameters
↓
2. Default parameters
↓
3. *args
↓
4. Keyword-only parameters
↓
5. **kwargs
```

A common valid pattern:

```python
def func(a, b=0, *args, **kwargs):
    pass
```

---

# *args vs **kwargs

| Feature | *args | **kwargs |
|----------|--------|-----------|
| Accepts | Positional arguments | Keyword arguments |
| Symbol | `*` | `**` |
| Stored As | Tuple | Dictionary |
| Example | `(1,2,3)` | `{'a':1}` |
| Unpacking | `*list` | `**dict` |

---

# Execution Flow

```text
Function Called
       ↓
Extra positional arguments?
       ↓
Collected into *args tuple
       ↓
Extra keyword arguments?
       ↓
Collected into **kwargs dictionary
       ↓
Function body executes
```

---

# Important Points

- `*args` accepts variable positional arguments.
- `*args` stores values as a tuple.
- `**kwargs` accepts variable keyword arguments.
- `**kwargs` stores values as a dictionary.
- `*` unpacks lists and tuples.
- `**` unpacks dictionaries.
- The names `args` and `kwargs` are conventions, not keywords.
- `*args` must appear before `**kwargs`.

---

# Quick Revision

```text
*args
↓
Variable positional arguments
↓
Tuple

**kwargs
↓
Variable keyword arguments
↓
Dictionary

*list
↓
Unpack list

**dict
↓
Unpack dictionary
```
