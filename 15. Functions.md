# FUNCTIONS IN PYTHON

## Definition

A function is a reusable block of code designed to perform a specific task.

Instead of writing the same code repeatedly, we place it inside a function and call it whenever needed.

---

# Why Functions Are Used

- Reduce code duplication.
- Improve readability.
- Break large programs into smaller modules.
- Make maintenance easier.
- Promote code reuse.

---

# Function Syntax

```python
def function_name(parameters):
    statements
    return value
```

Example:

```python
def greet():
    print("Hello Python Lovers")
```

Calling the function:

```python
greet()
```

Output:

```python
Hello Python Lovers
```

---

# Components of a Function

```python
def add(a, b):
    return a + b
```

| Component | Meaning |
|----------|-----------|
| `def` | Defines a function |
| `add` | Function name |
| `a, b` | Parameters |
| `return` | Sends result back |
| `add(10, 20)` | Function call |

---

# Parameters vs Arguments

## Parameters

Variables defined in the function declaration.

```python
def add(x, y):
    pass
```

Here:

```python
x, y
```

are parameters.

---

## Arguments

Actual values passed during function call.

```python
add(10, 20)
```

Here:

```python
10, 20
```

are arguments.

---

# Types of Functions

## 1. Built-in Functions

Predefined by Python.

Examples:

```python
print()
len()
sum()
max()
min()
type()
```

Example:

```python
print(max(10, 50, 30))
```

Output:

```python
50
```

---

## 2. User-Defined Functions

Created by programmers.

Example:

```python
def square(n):
    return n * n
```

```python
print(square(10))
```

Output:

```python
100
```

---

## 3. Anonymous Functions (Lambda)

Functions without names.

Syntax:

```python
lambda parameters: expression
```

Example:

```python
square = lambda x: x * x

print(square(5))
```

Output:

```python
25
```

---

# Functions Without Parameters

Example:

```python
def myfunc():
    print("Hello Python Lovers")
```

```python
myfunc()
```

Output:

```python
Hello Python Lovers
```

---

# Functions With Parameters

Example:

```python
def details(name, userid, country):
    print("Name:", name)
    print("User ID:", userid)
    print("Country:", country)
```

Calling:

```python
details("Asif", "asif123", "India")
```

Output:

```python
Name: Asif
User ID: asif123
Country: India
```

---

# Return Statement

Used to send data back to the caller.

Example:

```python
def square(n):
    return n * n
```

```python
result = square(10)

print(result)
```

Output:

```python
100
```

---

# Functions Returning Nothing

Example:

```python
def greet():
    print("Hello")
```

```python
print(greet())
```

Output:

```python
Hello
None
```

Explanation:

Functions without `return` automatically return:

```python
None
```

---

# Docstrings

Used to document functions.

Example:

```python
def even_odd(num):
    """
    Check whether a number is even or odd.
    """

    if num % 2 == 0:
        print(num, "is even")
    else:
        print(num, "is odd")
```

Access documentation:

```python
print(even_odd.__doc__)
```

Output:

```python
Check whether a number is even or odd.
```

---

# Positional Arguments

Arguments are matched based on position.

Example:

```python
def fullname(first, middle, last):
    print(first, middle, last)
```

```python
fullname("Asif", "Ali", "Bhat")
```

Output:

```python
Asif Ali Bhat
```

---

# Keyword Arguments

Arguments matched by parameter names.

Example:

```python
fullname(
    lastname="Bhat",
    middlename="Ali",
    firstname="Asif"
)
```

Output:

```python
Asif Ali Bhat
```

Order does not matter.

---

# Missing Arguments

Example:

```python
fullname("Asif")
```

Output:

```python
TypeError
```

Reason:

Required arguments were not provided.

---

# Default Arguments

Default values are used if arguments are omitted.

Example:

```python
def city(name="Mumbai"):
    print(name)
```

```python
city()
```

Output:

```python
Mumbai
```

---

```python
city("Chennai")
```

Output:

```python
Chennai
```

---

# Variable Scope

Scope determines where a variable can be accessed.

---

## Global Scope

Declared outside functions.

Accessible throughout the program.

Example:

```python
var1 = 100

def myfunc():
    print(var1)

myfunc()

print(var1)
```

Output:

```python
100
100
```

---

## Local Scope

Declared inside functions.

Accessible only inside that function.

Example:

```python
def myfunc():
    var2 = 10
    print(var2)

myfunc()
```

Output:

```python
10
```

---

Trying to access it outside:

```python
print(var2)
```

Output:

```python
NameError
```

---

# Local Variable Hides Global Variable

Example:

```python
var1 = 100

def myfunc():
    var1 = 99
    print(var1)

myfunc()

print(var1)
```

Output:

```python
99
100
```

Explanation:

Local variable takes priority inside the function.

Global value remains unchanged.

---

# Passing Mutable Objects

Lists are mutable.

Changes made inside functions affect the original list.

Example:

```python
list1 = [11, 22, 33]

def myfunc(list1):
    del list1[0]

myfunc(list1)

print(list1)
```

Output:

```python
[22, 33]
```

---

Example:

```python
list1 = [11, 22]

def myfunc(list1):
    list1.append(100)

myfunc(list1)

print(list1)
```

Output:

```python
[11, 22, 100]
```

---

# Reassigning Parameters

Example:

```python
list1 = [11, 22]

def myfunc(list1):
    list1 = [10, 100]
```

```python
myfunc(list1)

print(list1)
```

Output:

```python
[11, 22]
```

Explanation:

Only the local reference changes.

Original list remains unchanged.

---

# Immutable Objects

Example:

```python
def swap(a, b):
    temp = a
    a = b
    b = temp

a = 10
b = 20

swap(a, b)

print(a, b)
```

Output:

```python
10 20
```

Explanation:

Integers are immutable.

Reassigning parameters does not affect original variables.

---

# Recursion

A function calling itself.

---

## Factorial

```python
def factorial(num):
    if num <= 1:
        return 1
    else:
        return num * factorial(num - 1)
```

Example:

```python
factorial(4)
```

Execution:

```text
4 × factorial(3)
4 × 3 × factorial(2)
4 × 3 × 2 × factorial(1)
4 × 3 × 2 × 1
```

Output:

```python
24
```

---

## Sum of Natural Numbers

```python
def add(num):
    if num == 0:
        return 0
    else:
        return num + add(num - 1)
```

Example:

```python
add(5)
```

Output:

```python
15
```

Calculation:

```text
5 + 4 + 3 + 2 + 1
```

---

## Fibonacci Series

```python
def fibonacci(num):
    if num <= 1:
        return num
    else:
        return fibonacci(num - 1) + fibonacci(num - 2)
```

Example:

```python
for i in range(10):
    print(fibonacci(i))
```

Output:

```text
0
1
1
2
3
5
8
13
21
34
```

---

# Execution Flow of a Function

```text
Function Defined
        ↓
Stored in Memory
        ↓
Function Called
        ↓
Arguments Passed
        ↓
Parameters Receive Values
        ↓
Function Body Executes
        ↓
return?
   ↓       ↓
 Yes       No
 ↓         ↓
Send      Return
Value     None
        ↓
Control Returns to Caller
```

---

# Important Points

- Functions are reusable blocks of code.
- Defined using `def`.
- Parameters receive values.
- Arguments send values.
- Functions may return values or `None`.
- Python supports positional, keyword, and default arguments.
- Variables can have local or global scope.
- Mutable objects can be modified inside functions.
- Immutable objects cannot be modified through reassignment.
- Recursion means a function calls itself.

---

# Quick Revision

```text
Function
↓
Reusable block of code

Defined using
↓
def

Parameters
↓
Receive values

Arguments
↓
Send values

Return
↓
Sends result back

Scope
↓
Global / Local

Recursion
↓
Function calls itself
```
