# Python Data Types

## What is a Data Type?

A data type specifies the kind of value stored in a variable and determines what operations can be performed on that value.

Every value in Python is an object, and every object belongs to a specific data type.

```python
x = 10
```

Here:

- `10` is a value.
- `int` is its data type.

---

# Classification of Python Data Types

```text
Python Data Types
│
├── Numeric
│   ├── int
│   ├── float
│   └── complex
│
├── Boolean
│   └── bool
│
├── String
│   └── str
│
├── Sequence
│   ├── list
│   ├── tuple
│   └── range
│
├── Set
│   ├── set
│   └── frozenset
│
├── Mapping
│   └── dict
│
└── Binary
    ├── bytes
    ├── bytearray
    └── memoryview
```

---

# Numeric Data Types

Numeric types are used to store numerical values.

Python provides three numeric data types:

1. Integer (`int`)
2. Float (`float`)
3. Complex (`complex`)

---

# Integer (int)

## Definition

An integer is a whole number without a decimal point.

Examples:

```python
10
25
-100
5000
```

---

## Creating an Integer

```python
val1 = 10
```

---

## Checking Type

```python
type(val1)
```

Output:

```text
<class 'int'>
```

---

## Checking Object Size

```python
import sys

sys.getsizeof(val1)
```

Output:

```text
28
```

The size may vary depending on the Python version and system architecture.

---

## Checking Instance

```python
isinstance(val1, int)
```

Output:

```text
True
```

This confirms that `val1` is an object of type `int`.

---

## Integer Characteristics

- Stores whole numbers.
- Supports positive and negative values.
- Has unlimited precision in Python.
- Most commonly used numeric type.

---

# Float (float)

## Definition

A float represents a number with a decimal point.

Examples:

```python
10.5
3.14
-25.75
92.78
```

---

## Creating a Float

```python
val2 = 92.78
```

---

## Checking Type

```python
type(val2)
```

Output:

```text
<class 'float'>
```

---

## Checking Size

```python
sys.getsizeof(val2)
```

Output:

```text
24
```

---

## Checking Instance

```python
isinstance(val2, float)
```

Output:

```text
True
```

---

## Float Characteristics

- Stores decimal values.
- Used in scientific and mathematical calculations.
- Less precise than integers because of floating-point representation.

Example:

```python
10 / 3
```

Output:

```text
3.3333333333333335
```

---

# Complex (complex)

## Definition

Complex numbers contain:

- Real part
- Imaginary part

Format:

```text
a + bj
```

Where:

- `a` = Real part
- `b` = Imaginary part
- `j` = Imaginary unit

---

## Creating a Complex Number

```python
val3 = 25 + 10j
```

---

## Checking Type

```python
type(val3)
```

Output:

```text
<class 'complex'>
```

---

## Checking Size

```python
sys.getsizeof(val3)
```

Output:

```text
32
```

---

## Checking Instance

```python
isinstance(val3, complex)
```

Output:

```text
True
```

---

## Accessing Parts

```python
val3 = 25 + 10j

print(val3.real)
print(val3.imag)
```

Output:

```text
25.0
10.0
```

---

## Complex Number Usage

Complex numbers are commonly used in:

- Signal processing
- Electrical engineering
- Physics
- Scientific computing

---

# Numeric Type Comparison

| Type | Example | Description |
|--------|---------|-------------|
| int | 10 | Whole number |
| float | 10.5 | Decimal number |
| complex | 10+5j | Real + Imaginary |

---

# Boolean Data Type (bool)

## Definition

A Boolean data type represents logical values.

A Boolean can have only two possible values:

```python
True
False
```

These values are case-sensitive.

Correct:

```python
True
False
```

Incorrect:

```python
true
false
```

---

## Creating Boolean Variables

```python
bool1 = True
bool2 = False
```

---

## Checking Type

```python
type(bool1)
```

Output:

```text
<class 'bool'>
```

---

```python
type(bool2)
```

Output:

```text
<class 'bool'>
```

---

## Checking Instance

```python
isinstance(bool1, bool)
```

Output:

```text
True
```

---

# Boolean Conversion

The `bool()` function converts values into Boolean values.

---

## bool(0)

```python
bool(0)
```

Output:

```text
False
```

Reason:

```text
0 represents absence of value.
```

---

## bool(1)

```python
bool(1)
```

Output:

```text
True
```

Reason:

```text
Any non-zero number is considered True.
```

---

## bool(None)

```python
bool(None)
```

Output:

```text
False
```

Reason:

```text
None represents absence of an object.
```

---

## bool(False)

```python
bool(False)
```

Output:

```text
False
```

---

## Additional Examples

```python
bool(100)
```

Output:

```text
True
```

---

```python
bool(-25)
```

Output:

```text
True
```

---

```python
bool("")
```

Output:

```text
False
```

---

```python
bool("Python")
```

Output:

```text
True
```

---

# Truthy and Falsy Values

## Falsy Values

Python automatically treats these as `False`.

```python
False
None
0
0.0
0j
''
[]
{}
set()
```

---

## Truthy Values

Everything else is generally considered `True`.

Examples:

```python
1
10
-5
"Python"
[1, 2]
{'a': 1}
```

---

# Key Points

- A data type defines the kind of value stored in an object.
- Every value in Python belongs to a data type.
- Numeric types include `int`, `float`, and `complex`.
- Boolean type contains only `True` and `False`.
- `type()` returns the datatype of an object.
- `isinstance()` checks whether an object belongs to a specific type.
- `sys.getsizeof()` returns the memory size of an object.
- `bool()` converts values into Boolean values.
- `0`, `None`, and empty collections are treated as `False`.

---

# Interview Definition

**A data type is a classification that specifies what kind of value an object holds and what operations can be performed on it. Python provides built-in data types such as int, float, complex, bool, str, list, tuple, set, and dictionary.**