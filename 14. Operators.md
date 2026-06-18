# Operators in Python

## What are Operators?

Operators are special symbols used to perform operations on variables and values.

Example:

```python
a = 5
b = 2

print(a + b)  # 7
```

---

# 1. Arithmetic Operators

Used for mathematical calculations.

| Operator | Meaning | Example | Result |
|----------|----------|----------|--------|
| + | Addition | 5 + 2 | 7 |
| - | Subtraction | 5 - 2 | 3 |
| * | Multiplication | 5 * 2 | 10 |
| / | Division | 5 / 2 | 2.5 |
| % | Modulus (Remainder) | 5 % 2 | 1 |
| ** | Power | 5 ** 2 | 25 |
| // | Floor Division | 5 // 2 | 2 |

### Example

```python
a = 5
b = 2

print(a + b)
print(a - b)
print(a * b)
print(a / b)
print(a % b)
print(a ** b)
print(a // b)
```

### String Concatenation

```python
x = "Hello"
y = "World"

print(x + y)
```

Output:

```
HelloWorld
```

---

# 2. Comparison Operators

Used to compare values.

| Operator | Meaning |
|----------|----------|
| == | Equal To |
| != | Not Equal To |
| > | Greater Than |
| < | Less Than |
| >= | Greater Than or Equal To |
| <= | Less Than or Equal To |

### Example

```python
x = 20
y = 30

print(x > y)
print(x < y)
print(x == y)
print(x != y)
print(x >= y)
print(x <= y)
```

Output:

```
False
True
False
True
False
True
```

---

# 3. Logical Operators

Used to combine conditions.

| Operator | Meaning |
|----------|----------|
| and | True if both conditions are True |
| or | True if at least one condition is True |
| not | Reverses the result |

### Example

```python
x = True
y = False

print(x and y)
print(x or y)
print(not x)
```

Output:

```
False
True
False
```

### Memory Trick

- `and` → Both must be True
- `or` → Any one can be True
- `not` → Opposite result

---

# 4. Bitwise Operators

Bitwise operators work on binary values (bits).

| Operator | Meaning |
|----------|----------|
| & | AND |
| \| | OR |
| ^ | XOR |
| ~ | NOT |
| << | Left Shift |
| >> | Right Shift |

### Example

```python
x = 18
y = 6

print(x & y)
print(x | y)
print(x ^ y)
print(~x)
print(x << 2)
print(x >> 2)
```

Output:

```
2
22
20
-19
72
4
```

### Shortcut

- `<< 1` → Multiply by 2
- `<< 2` → Multiply by 4
- `>> 1` → Divide by 2
- `>> 2` → Divide by 4

---

# 5. Assignment Operators

Used to update variable values.

| Operator | Equivalent To |
|----------|---------------|
| += | x = x + value |
| -= | x = x - value |
| *= | x = x * value |
| /= | x = x / value |
| %= | x = x % value |
| **= | x = x ** value |
| //= | x = x // value |
| &= | x = x & value |
| \|= | x = x \| value |
| ^= | x = x ^ value |
| <<= | x = x << value |
| >>= | x = x >> value |

### Example

```python
x = 10

x += 5
print(x)

x *= 2
print(x)

x -= 10
print(x)
```

Output:

```
15
30
20
```

---

# 6. Membership Operators

Used to check whether a value exists in a sequence.

| Operator | Meaning |
|----------|----------|
| in | Present |
| not in | Not Present |

### Example

```python
name = "Python Programming"

print("Python" in name)
print("Java" in name)

print("Java" not in name)
```

Output:

```
True
False
True
```

---

# Quick Revision Sheet

```text
ARITHMETIC
+   Addition
-   Subtraction
*   Multiplication
/   Division
%   Modulus
**  Power
//  Floor Division

COMPARISON
==  Equal
!=  Not Equal
>   Greater Than
<   Less Than
>=  Greater Than or Equal To
<=  Less Than or Equal To

LOGICAL
and
or
not

BITWISE
&
|
^
~
<<
>>

ASSIGNMENT
+=
-=
*=
/=
%=
**=
//=
&=
|=
^=
<<=
>>=

MEMBERSHIP
in
not in
```

## Interview Definition

**Operators are special symbols used to perform operations on variables and values.**
