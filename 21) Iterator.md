# ITERABLE & ITERATOR IN PYTHON

This is one of the most important Python concepts because:

```text
for loops
lists
tuples
strings
generators
files
map()
filter()
zip()

ALL work using iterators.
```

---

# The Big Picture

```text
Iterable
↓ gives
Iterator
↓ gives
Next Element
↓
Next Element
↓
Next Element
↓
StopIteration
```

---

# What is an Iterable?

## Definition

An iterable is an object that can be traversed one element at a time.

It can produce an iterator.

---

# Examples of Iterables

```python
list
tuple
string
set
dictionary
range
```

Example:

```python
mylist = [1, 2, 3]
```

You can iterate over it:

```python
for i in mylist:
    print(i)
```

Output:

```text
1
2
3
```

---

# Iterable Rule

An object is iterable if it has:

```python
__iter__()
```

method.

---

# What is an Iterator?

## Definition

An iterator is an object that remembers its current position and returns the next element whenever asked.

---

# Iterator Rules

Iterator must implement:

```python
__iter__()
```

and

```python
__next__()
```

---

# __next__()

Purpose:

```text
Give me the next value.
```

When elements finish:

```python
StopIteration
```

is raised.

---

# Difference Between Iterable and Iterator

| Iterable | Iterator |
|----------|-----------|
| Collection of values | Produces values one-by-one |
| Has `__iter__()` | Has `__iter__()` and `__next__()` |
| Cannot remember position | Remembers current position |
| Example: list | Example: list_iterator |

---

# Visual Understanding

List:

```python
['Asif', 'Basit', 'John']
```

Iterable:

```text
Shelf full of books
```

Iterator:

```text
Finger pointing at current book
```

---

# Creating Iterator from Iterable

List:

```python
mylist = [
    'Asif',
    'Basit',
    'John',
    'Michael'
]
```

Iterator:

```python
list_iter = iter(mylist)
```

---

# What Does iter() Do?

```python
iter(mylist)
```

means:

```text
Convert iterable into iterator.
```

---

# Internal Flow

```text
mylist
↓
iter()
↓
list_iterator
↓
next()
↓
Elements returned one by one
```

---

# Using next()

```python
print(next(list_iter))
```

Output:

```text
Asif
```

---

Second call:

```python
print(next(list_iter))
```

Output:

```text
Basit
```

---

Third:

```python
print(next(list_iter))
```

Output:

```text
John
```

---

Fourth:

```python
print(next(list_iter))
```

Output:

```text
Michael
```

---

Fifth:

```python
print(next(list_iter))
```

Output:

```text
StopIteration
```

---

# Why StopIteration?

Because:

```text
No more elements exist.
```

Iterator says:

```text
I am finished.
```

---

# Internal State

Initially:

```text
['Asif','Basit','John','Michael']
 ↑
```

After first next():

```text
['Asif','Basit','John','Michael']
        ↑
```

After second:

```text
['Asif','Basit','John','Michael']
               ↑
```

After fourth:

```text
END
```

---

# __next__() Method

This:

```python
next(list_iter)
```

actually calls:

```python
list_iter.__next__()
```

Both are same.

---

Example

```python
print(list_iter.__next__())
```

Output:

```text
Asif
```

---

# for Loop Internally

When you write:

```python
for i in mylist:
    print(i)
```

Python actually does:

```python
iterator = iter(mylist)

while True:

    try:
        i = next(iterator)
        print(i)

    except StopIteration:
        break
```

---

# This Is Huge

```text
FOR LOOP
=
iter()
+
next()
+
StopIteration
```

---

# Looping Through List

```python
mylist = [
    'Asif',
    'Basit',
    'John',
    'Michael'
]

for i in mylist:
    print(i)
```

Output:

```text
Asif
Basit
John
Michael
```

---

# Looping Through Tuple

```python
mytuple = (
    'Asif',
    'Basit',
    'John',
    'Michael'
)

for i in mytuple:
    print(i)
```

Output:

```text
Asif
Basit
John
Michael
```

---

# Looping Through String

```python
mystr = "Hello Python"

for i in mystr:
    print(i)
```

Output:

```text
H
e
l
l
o

P
y
t
h
o
n
```

---

# Custom Iterator

Python allows us to build our own iterator.

Need:

```python
__iter__()
```

and

```python
__next__()
```

---

# Natural Numbers Iterator

```python
class MyIter:

    def __init__(self):
        self.num = 0

    def __iter__(self):

        self.num = 1

        return self

    def __next__(self):

        if self.num <= 10:

            val = self.num

            self.num += 1

            return val

        else:

            raise StopIteration
```

---

# Object Creation

```python
mynum = MyIter()
```

Iterator:

```python
iter1 = iter(mynum)
```

Loop:

```python
for i in iter1:
    print(i)
```

Output:

```text
1
2
3
4
5
6
7
8
9
10
```

---

# How It Works

First iteration:

```text
num = 1
return 1
num = 2
```

Second:

```text
return 2
num = 3
```

...

Tenth:

```text
return 10
num = 11
```

Then:

```text
raise StopIteration
```

---

# Odd Number Iterator

```python
class MyIter:

    def __init__(self):
        self.num = 0

    def __iter__(self):

        self.num = 1

        return self

    def __next__(self):

        if self.num <= 20:

            val = self.num

            self.num += 2

            return val

        else:

            raise StopIteration
```

---

Output

```text
1
3
5
7
9
11
13
15
17
19
```

---

# Fibonacci Iterator

```python
class MyFibonacci:

    def __init__(self):

        self.prev = 0
        self.cur = 0

    def __iter__(self):

        self.prev = 0
        self.cur = 1

        return self

    def __next__(self):

        if self.cur <= 50:

            val = self.cur

            self.cur += self.prev

            self.prev = val

            return val

        else:

            raise StopIteration
```

---

# Execution Flow

Initial:

```text
prev = 0
cur = 1
```

---

First:

```text
return 1

prev = 1
cur = 1
```

---

Second:

```text
return 1

prev = 1
cur = 2
```

---

Third:

```text
return 2

prev = 2
cur = 3
```

---

Continues:

```text
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

Stops before exceeding:

```text
50
```

---

# Iterator Protocol

An object is a proper iterator if:

```python
obj.__iter__()
```

returns itself:

```python
return self
```

AND

```python
obj.__next__()
```

returns next value.

---

# Complete Flow

```text
Iterable
↓
iter()
↓
Iterator
↓
next()
↓
Value
↓
next()
↓
Value
↓
next()
↓
StopIteration
```

---

# Iterable vs Iterator (Exam Revision)

| Feature | Iterable | Iterator |
|----------|-----------|-----------|
| Purpose | Stores data | Produces data |
| Method | `__iter__()` | `__iter__()`, `__next__()` |
| Position Tracking | No | Yes |
| Can use `for` loop | Yes | Yes |
| Examples | list, tuple, str | list_iterator |

---

# Quick Revision

```text
Iterable
↓
Can be traversed

Iterator
↓
Returns elements one-by-one

iter()
↓
Iterable → Iterator

next()
↓
Get next element

StopIteration
↓
No elements left

for loop
↓
Uses iter() and next() internally

Custom Iterator
↓
Implement __iter__()
Implement __next__()
Raise StopIteration
```
