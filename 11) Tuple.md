# Python Tuples

## What is a Tuple?

A tuple is an ordered collection of elements.

A tuple is very similar to a list, but there is one major difference:

```text
List   → Mutable
Tuple  → Immutable
```

Once a tuple is created, its elements cannot be modified, added, or removed.

---

# Why Use Tuples?

Use tuples when data should remain constant.

Examples:

- Days of the week
- Months of the year
- Coordinates
- Database records
- Configuration values

Example:

```python
days = (
    "Monday",
    "Tuesday",
    "Wednesday",
    "Thursday",
    "Friday",
    "Saturday",
    "Sunday"
)
```

These values should never change.

---

# Advantages of Tuples

## 1. Data Safety

Elements cannot be modified accidentally.

```python
marks = (90, 85, 70)
```

Nobody can change:

```python
marks[0] = 100
```

---

## 2. Faster than Lists

Tuple iteration is slightly faster because Python knows the data cannot change.

---

## 3. Less Memory

Tuples generally consume less memory than lists.

---

## 4. Hashable

Tuples can be used as dictionary keys (if elements are immutable).

```python
location = (12.5, 78.2)

data = {
    location: "Chennai"
}
```

---

# Tuple Creation

## Empty Tuple

```python
tup1 = ()
```

---

## Integer Tuple

```python
tup2 = (10, 30, 60)
```

---

## Float Tuple

```python
tup3 = (10.77, 30.66, 60.89)
```

---

## String Tuple

```python
tup4 = ('one', 'two', 'three')
```

---

## Nested Tuple

```python
tup5 = (
    'Asif',
    25,
    (50, 100),
    (150, 90)
)
```

---

## Mixed Tuple

```python
tup6 = (
    100,
    'Asif',
    17.765
)
```

---

## Complex Tuple

```python
tup7 = (
    'Asif',
    25,
    [50, 100],
    [150, 90],
    {'John', 'David'},
    (99, 22, 33)
)
```

---

# Length of a Tuple

```python
len(tup7)
```

Output:

```text
6
```

---

# Tuple Indexing

Tuples support indexing exactly like lists.

```text
('one', 'two', 'three')

   0      1      2
```

---

## First Element

```python
tup2[0]
```

Output:

```text
10
```

---

## First String

```python
tup4[0]
```

Output:

```text
one
```

---

## Nested Indexing

```python
tup4[0][0]
```

Output:

```text
o
```

Explanation:

```text
tup4[0]     → "one"
tup4[0][0]  → "o"
```

---

## Last Element

```python
tup4[-1]
```

Output:

```text
three
```

---

## Last Nested Tuple

```python
tup5[-1]
```

Output:

```python
(150, 90)
```

---

# Tuple Slicing

Syntax:

```python
tuple[start:end]
```

Rules:

- Start included.
- End excluded.

---

## First Three Elements

```python
mytuple[:3]
```

Output:

```python
('one', 'two', 'three')
```

---

## Middle Elements

```python
mytuple[2:5]
```

Output:

```python
('three', 'four', 'five')
```

---

## Last Three Elements

```python
mytuple[-3:]
```

Output:

```python
('six', 'seven', 'eight')
```

---

## Last Element

```python
mytuple[-1]
```

Output:

```python
'eight'
```

---

## Entire Tuple

```python
mytuple[:]
```

Output:

```python
('one', 'two', 'three', 'four', 'five', 'six', 'seven', 'eight')
```

---

# Tuple Immutability

## Cannot Change Elements

```python
mytuple[0] = 1
```

Output:

```text
TypeError
```

Reason:

```text
Tuple is immutable.
```

---

## Cannot Delete Individual Elements

```python
del mytuple[0]
```

Output:

```text
TypeError
```

Reason:

```text
Tuple does not support item deletion.
```

---

## Can Delete Entire Tuple

```python
del mytuple
```

After deletion:

```python
print(mytuple)
```

Output:

```text
NameError
```

Reason:

```text
Tuple object no longer exists.
```

---

# Loop Through a Tuple

## Normal Loop

```python
for item in mytuple:
    print(item)
```

Output:

```text
one
two
three
...
```

---

## Using enumerate()

```python
for item in enumerate(mytuple):
    print(item)
```

Output:

```text
(0, 'one')
(1, 'two')
(2, 'three')
```

---

# count()

Returns occurrence count.

```python
mytuple1 = (
    'one',
    'two',
    'three',
    'four',
    'one',
    'one'
)
```

---

## Count "one"

```python
mytuple1.count('one')
```

Output:

```text
3
```

---

## Count "two"

```python
mytuple1.count('two')
```

Output:

```text
1
```

---

# Tuple Membership

Checks whether an item exists.

---

## Present

```python
'one' in mytuple
```

Output:

```text
True
```

---

## Not Present

```python
'ten' in mytuple
```

Output:

```text
False
```

---

## Membership with if

```python
if 'three' in mytuple:
    print("Present")
else:
    print("Absent")
```

Output:

```text
Present
```

---

# index()

Returns the position of the first occurrence.

```python
mytuple = (
    'one',
    'two',
    'three',
    'four',
    'five'
)
```

---

## Find "one"

```python
mytuple.index('one')
```

Output:

```text
0
```

---

## Find "five"

```python
mytuple.index('five')
```

Output:

```text
4
```

---

# Sorting a Tuple

Tuples have no `.sort()` method because they are immutable.

---

## Using sorted()

```python
mytuple2 = (
    43,
    67,
    99,
    12,
    6,
    90,
    67
)
```

---

### Ascending

```python
sorted(mytuple2)
```

Output:

```python
[6, 12, 43, 67, 67, 90, 99]
```

Important:

```text
sorted() returns a LIST
not a tuple.
```

---

### Descending

```python
sorted(mytuple2, reverse=True)
```

Output:

```python
[99, 90, 67, 67, 43, 12, 6]
```

---

# Single Element Tuple

This is a common interview question.

Wrong:

```python
t = (5)
```

Output:

```python
int
```

Because Python treats it as a number.

---

Correct:

```python
t = (5,)
```

Output:

```python
tuple
```

---

# Tuple Packing

Creating a tuple automatically.

```python
t = 10, 20, 30
```

Output:

```python
(10, 20, 30)
```

This is called:

```text
Tuple Packing
```

---

# Tuple Unpacking

Extract values into variables.

```python
t = (10, 20, 30)

a, b, c = t
```

Output:

```python
a = 10
b = 20
c = 30
```

This is called:

```text
Tuple Unpacking
```

---

# List vs Tuple

| Feature | List | Tuple |
|----------|----------|----------|
| Syntax | [] | () |
| Ordered | Yes | Yes |
| Indexed | Yes | Yes |
| Mutable | Yes | No |
| Faster | No | Yes |
| Memory Usage | More | Less |
| append() | Yes | No |
| remove() | Yes | No |
| sort() | Yes | No |

---

# Key Points

- Tuple is an ordered collection.
- Tuple is immutable.
- Supports indexing and slicing.
- Allows duplicate values.
- Can store mixed data types.
- Faster than lists for iteration.
- Cannot add, modify, or remove individual elements.
- Supports `count()` and `index()`.
- `sorted()` returns a sorted list from a tuple.
- Single-element tuple requires a trailing comma.
- Supports packing and unpacking.

---

# Interview Definition

**A tuple is an ordered and immutable collection of elements enclosed within parentheses `()`. Tuples support indexing, slicing, iteration, packing, and unpacking, but do not allow modification of their elements after creation.**