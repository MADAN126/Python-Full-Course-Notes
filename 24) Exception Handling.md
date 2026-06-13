# ERROR & EXCEPTION HANDLING

---

# What is an Error?

An error is a problem that interrupts the normal execution of a program.

Example:

```python
print(10 / 0)
```

Output:

```python
ZeroDivisionError
```

Flow:

Program Starts
↓
Error Occurs
↓
Python Stops Execution
↓
Program Crashes

---

# What is an Exception?

An exception is an object representing an error that occurs during program execution.

Examples:

- ZeroDivisionError
- IndexError
- KeyError
- NameError
- FileNotFoundError
- TypeError
- ValueError
- ModuleNotFoundError
- AssertionError

---

# Why Exception Handling?

Without Exception Handling:

```
Program Starts
↓
Error Occurs
↓
Program Terminates
```

With Exception Handling:

```
Program Starts
↓
Error Occurs
↓
Exception Caught
↓
Alternative Logic Executes
↓
Program Continues
```

---

# try-except Structure

Syntax:

```python
try:
    risky_code
except:
    exception_handling_code
```

Flow:

Try Block
↓
No Exception?
├── Yes → Skip except
└── No
     ↓
Execute except

---

# try Block

Purpose:

Contains code that may raise exceptions.

Example:

```python
try:
    print(100 / 0)
```

Python monitors this block.

---

# except Block

Purpose:

Handles exceptions raised inside try.

Example:

```python
import sys

try:
    print(100 / 0)

except:
    print(sys.exc_info()[1], "Exception occurred")
```

Output:

```python
division by zero Exception occurred
```

Flow:

try
↓
ZeroDivisionError
↓
except executes

---

# else Block

Purpose:

Runs only if NO exception occurs.

Syntax:

```python
try:
    ...
except:
    ...
else:
    ...
```

Flow:

Try
↓
Exception?
├── Yes → except
└── No → else

Example:

```python
try:
    print(10 / 2)

except:
    print("Error")

else:
    print("No exception occurred")
```

Output:

```python
5.0
No exception occurred
```

---

# finally Block

Purpose:

Always executes.

Syntax:

```python
try:
    ...
except:
    ...
finally:
    ...
```

Flow:

Try
↓
Exception?
↓
except (if needed)
↓
finally ALWAYS runs

Example:

```python
try:
    print(100 / 0)

except:
    print("Handled")

finally:
    print("Cleanup")
```

Output:

```python
Handled
Cleanup
```

---

# Complete try-except-else-finally

Example:

```python
import sys

try:
    print(100 / 0)

except:
    print(sys.exc_info()[1], "Exception occurred")

else:
    print("No exception occurred")

finally:
    print("Run this block always")
```

Output:

```python
division by zero Exception occurred
Run this block always
```

Flow:

Try
↓
Exception Found
↓
except
↓
finally

else skipped

---

# NameError Example

Occurs when variable doesn't exist.

Example:

```python
try:
    print(x)

except:
    print("Variable x is not defined")
```

Output:

```python
Variable x is not defined
```

---

# Handling FileNotFoundError

Example:

```python
import os
import sys

try:
    os.remove("test3.txt")

except:
    print("BELOW EXCEPTION OCCURRED")
    print(sys.exc_info()[1])

finally:
    print("Run this block always")
```

Output:

```python
BELOW EXCEPTION OCCURRED
[WinError 2] The system cannot find the file specified
Run this block always
```

---

# Handling Specific Exceptions

Instead of:

```python
except:
```

Use:

```python
except ExceptionType:
```

Flow:

Exception Raised
↓
Matching except searched
↓
Matching block executes

Example:

```python
import os

try:
    x = int(input("Enter first number: "))
    y = int(input("Enter second number: "))

    print(x / y)

    os.remove("test3.txt")

except NameError:
    print("NameError occurred")

except FileNotFoundError:
    print("FileNotFoundError occurred")

except ZeroDivisionError:
    print("ZeroDivisionError occurred")
```

---

# ZeroDivisionError

Occurs when dividing by zero.

Example:

```python
try:
    print(10 / 0)

except ZeroDivisionError:
    print("ZeroDivisionError occurred")
```

Output:

```python
ZeroDivisionError occurred
```

---

# Raising Exceptions Manually

Python allows developers to create exceptions intentionally.

Keyword:

```python
raise
```

Syntax:

```python
raise ExceptionType
```

Example:

```python
try:
    x = int(input("Enter number: "))

    if x > 50:
        raise ValueError(x)

except:
    print(sys.exc_info()[0])
```

Input:

```python
100
```

Output:

```python
<class 'ValueError'>
```

Flow:

Input
↓
Condition True
↓
raise
↓
Exception Generated
↓
except handles it

---

# Built-in Exceptions

---

# OverflowError

Occurs when result exceeds allowable numeric range.

Example:

```python
import math
import sys

try:
    print(math.exp(1000))

except OverflowError:
    print(sys.exc_info())
```

Output:

```python
OverflowError
```

---

# ZeroDivisionError

Occurs when denominator is zero.

Example:

```python
try:
    print(100 / 0)

except ZeroDivisionError:
    print("ZeroDivisionError Exception Raised")
```

Output:

```python
ZeroDivisionError Exception Raised
```

---

# NameError

Occurs when variable is undefined.

Example:

```python
try:
    print(x1)

except NameError:
    print("NameError Exception Raised")
```

Output:

```python
NameError Exception Raised
```

---

# AssertionError

Occurs when assert condition fails.

Syntax:

```python
assert condition
```

Example:

```python
try:
    a = 50
    b = "Asif"

    assert a == b

except AssertionError:
    print("Assertion Exception Raised")
```

Output:

```python
Assertion Exception Raised
```

Flow:

Condition Checked
↓
False
↓
AssertionError

---

# ModuleNotFoundError

Occurs when imported module doesn't exist.

Example:

```python
try:
    import MyModule

except ModuleNotFoundError:
    print("ModuleNotFoundError Exception Raised")
```

Output:

```python
ModuleNotFoundError Exception Raised
```

---

# KeyError

Occurs when dictionary key doesn't exist.

Example:

```python
try:
    mydict = {
        1: "Asif",
        2: "Basit",
        3: "Michael"
    }

    print(mydict[4])

except KeyError:
    print("KeyError Exception Raised")
```

Output:

```python
KeyError Exception Raised
```

Flow:

Dictionary
↓
Missing Key Accessed
↓
KeyError

---

# IndexError

Occurs when invalid index is accessed.

Example:

```python
try:
    mylist = [1, 2, 3, 4, 5]

    print(mylist[10])

except IndexError:
    print("IndexError Exception Raised")
```

Output:

```python
IndexError Exception Raised
```

Flow:

List
↓
Index Outside Range
↓
IndexError

---

# TypeError

Occurs when incompatible types are used.

Example:

```python
try:
    a = 50
    b = "Asif"

    c = a / b

except TypeError:
    print("TypeError Exception Raised")
```

Output:

```python
TypeError Exception Raised
```

Flow:

Unsupported Operation
↓
Different Data Types
↓
TypeError

---

# AttributeError

Occurs when object doesn't have requested attribute.

Example:

```python
try:
    a = 10

    print(a.upper())

except AttributeError:
    print("AttributeError Exception Raised")
```

Output:

```python
AttributeError Exception Raised
```

Flow:

Object
↓
Missing Attribute/Method
↓
AttributeError

---

# Exception Hierarchy Mental Model

```
Program
↓
try
↓
Risky Code
↓
Exception?
├── No
│   ↓
│  else
│   ↓
│ finally
│
└── Yes
    ↓
except
    ↓
finally
```

---

# Best Practices

✓ Catch specific exceptions

```python
except ZeroDivisionError:
```

instead of

```python
except:
```

---

✓ Use finally for cleanup

```python
finally:
    file.close()
```

---

✓ Use raise for business validations

```python
if age < 18:
    raise ValueError("Age must be 18+")
```

---

✓ Avoid hiding all errors

Bad:

```python
except:
    pass
```

Good:

```python
except FileNotFoundError:
    print("File missing")
```

---

# Complete Mental Model

```
Risky Code
↓
try
↓
Exception?
├── No
│   ↓
│ else
│
└── Yes
    ↓
Matching except
↓
finally
↓
Program Continues
```
