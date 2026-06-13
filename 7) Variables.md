# Python Variables

## What is a Variable?

A variable is a name used to refer to a value stored in memory.

Variables allow us to store, access, and manipulate data during program execution.

In Python, a variable is created automatically when a value is assigned to it.

```python
p = 30
```

Here:

- `30` is an integer object.
- `p` is a variable.
- `p` refers to the object `30`.

---

## Variable Creation

Python follows a dynamic typing system.

The variable is created at runtime when a value is assigned.

```python
p = 30
```

Python internally performs:

```text
Create object 30
Create reference p
Connect p to object 30
```

---

## Variables Store References, Not Values

A common misconception is that variables store values.

In reality, variables store references to objects.

```python
p = 20
```

```text
p ───► 20
```

The variable points to the object rather than containing the object itself.

---

## Object Identity

Every object in Python has a unique identity.

The `id()` function returns the identity of an object.

```python
p = 30

id(p)
```

Output:

```text
140735029552432
```

The exact number varies from system to system.

---

## Memory Address Representation

To view the identity in hexadecimal format:

```python
hex(id(p))
```

Output:

```text
'0x7fff6d71a530'
```

This is often referred to as the memory address representation of the object.

---

## Multiple Variables Referencing the Same Object

```python
p = 20
q = 20
r = q
```

Memory representation:

```text
p ─┐
q ─┼──► 20
r ─┘
```

All three variables refer to the same integer object.

---

## Verifying with id()

```python
p = 20
q = 20
r = q

print(id(p))
print(id(q))
print(id(r))
```

Output:

```text
Same identity value
Same identity value
Same identity value
```

Since all variables point to the same object, their identities are identical.

---

## Checking Type of a Variable

The `type()` function returns the datatype of an object.

```python
p = 20

type(p)
```

Output:

```text
<class 'int'>
```

Example:

```python
p, type(p), hex(id(p))
```

Output:

```text
(20, int, memory_address)
```

---

## Variable Reassignment

Variables can be reassigned to a different object.

```python
p = 20
p = 30
```

Initially:

```text
p ───► 20
```

After reassignment:

```text
p ───► 30
```

The reference changes from one object to another.

---

## Variable Overwriting

```python
p = 20

p = p + 10
```

Step 1:

```text
p ───► 20
```

Step 2:

```python
p + 10
```

creates:

```text
30
```

Step 3:

```text
p ───► 30
```

Output:

```text
30
```

The original value is not modified. Instead, a new object is created and the variable points to it.

---

## Variable Assignment

Variables can store different types of data.

```python
intvar = 10
floatvar = 2.57
strvar = "Python Language"
```

```python
print(intvar)
print(floatvar)
print(strvar)
```

Output:

```text
10
2.57
Python Language
```

---

## Types of Variable Assignments

### 1. Single Assignment

One variable assigned one value.

```python
name = "Python"
```

```text
name ───► "Python"
```

---

### 2. Multiple Assignment

Multiple variables assigned different values in a single statement.

```python
intvar, floatvar, strvar = 10, 2.57, "Python Language"
```

Output:

```text
10
2.57
Python Language
```

Memory representation:

```text
intvar   ───► 10
floatvar ───► 2.57
strvar   ───► "Python Language"
```

---

### 3. Chain Assignment

Multiple variables assigned the same value.

```python
p1 = p2 = p3 = p4 = 44
```

Memory representation:

```text
p1 ─┐
p2 ─┼──► 44
p3 ─┤
p4 ─┘
```

Output:

```text
44 44 44 44
```

All variables reference the same object.

---

## Dynamic Typing

Python variables are not restricted to one datatype.

```python
p = 10
```

Later:

```python
p = "Python"
```

Later:

```python
p = 2.5
```

The same variable can refer to objects of different types during execution.

---

## Important Functions Related to Variables

### id()

Returns the unique identity of an object.

```python
id(p)
```

---

### hex()

Converts a decimal number into hexadecimal format.

```python
hex(id(p))
```

---

### type()

Returns the datatype of an object.

```python
type(p)
```

---

## Key Points

- A variable is a reference to an object.
- Variables are created automatically when assigned a value.
- Python variables do not directly store values; they store references.
- `id()` returns the unique identity of an object.
- `hex(id())` displays the identity in hexadecimal form.
- Multiple variables can refer to the same object.
- Variables can be reassigned at any time.
- Python supports dynamic typing.
- Multiple and chain assignments are supported.

---

## Interview Definition

**A variable is a named reference that points to an object stored in memory. Python creates a variable automatically when a value is assigned to it. Variables store references to objects, not the actual objects themselves.**