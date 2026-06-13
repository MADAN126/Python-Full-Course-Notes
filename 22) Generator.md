# GENERATORS IN PYTHON

Generators are one of Python's smartest features.

They solve one problem:

```text
How can we produce values one-by-one
without storing everything in memory?
```

Answer:

```text
Generators
```

---

# The Problem

Suppose you want numbers from 1 to 1,000,000.

Normal approach:

```python
nums = list(range(1, 1000001))
```

Python creates:

```text
1
2
3
...
1000000
```

ALL at once.

Memory usage:

```text
Huge
```

---

# Generator Approach

Instead:

```python
yield 1
yield 2
yield 3
...
```

Only one value exists at a time.

Memory usage:

```text
Very small
```

---

# Definition

A generator is a special function that:

```text
Produces values one-by-one
instead of returning everything at once.
```

---

# Generator = Iterator

Generator automatically behaves like an iterator.

Python automatically provides:

```python
__iter__()
__next__()
```

for generators.

You don't write them.

---

# Generator vs Normal Function

Normal Function:

```python
def func():
    return value
```

Generator:

```python
def func():
    yield value
```

---

# return vs yield

## return

```python
return value
```

Meaning:

```text
Give value.
Terminate function.
Forget everything.
```

---

## yield

```python
yield value
```

Meaning:

```text
Give value.
Pause function.
Remember current state.
Continue later.
```

---

# Biggest Difference

return:

```text
START
↓
Execute
↓
Return
↓
DEAD
```

yield:

```text
START
↓
yield
↓
PAUSE
↓
Resume
↓
yield
↓
PAUSE
↓
Resume
↓
StopIteration
```

---

# Simple Generator

```python
def mygen():

    n = 1
    yield n

    n += 1
    yield n

    n += 1
    yield n

    n += 1
    yield n

    n += 1
    yield n
```

---

# Create Generator Object

```python
mygen1 = mygen()
```

Generator object:

```text
<generator object>
```

NOT:

```text
1 2 3 4 5
```

Nothing executes yet.

---

# Important Rule

Calling:

```python
mygen()
```

DOES NOT execute the function.

It only creates the generator.

Execution starts only when:

```python
next()
```

is called.

---

# Execution Flow

Generator created:

```text
n = ?
Not started
```

---

First:

```python
next(mygen1)
```

Output:

```text
1
```

Paused here:

```python
yield n
```

State remembered:

```text
n = 1
```

---

Second:

```python
next(mygen1)
```

Resumes from pause:

```python
n += 1
yield n
```

Output:

```text
2
```

---

Third:

Output:

```text
3
```

---

Fourth:

Output:

```text
4
```

---

Fifth:

Output:

```text
5
```

---

Sixth:

```python
next(mygen1)
```

Output:

```text
StopIteration
```

Generator finished.

---

# Why StopIteration?

Because generators are iterators.

All iterators follow:

```text
No values left
↓
StopIteration
```

---

# Natural Numbers Generator

```python
def mygen():

    for i in range(1,20):

        yield i
```

---

Execution

```python
mygen1 = mygen()

for i in mygen1:
    print(i)
```

Output:

```text
1
2
3
4
...
19
```

---

# Internal Flow

for loop:

```text
Generator
↓
next()
↓
yield 1

next()
↓
yield 2

next()
↓
yield 3

...

StopIteration
```

---

# Converting Generator to List

Generator:

```python
num = list(mygen())
```

Output:

```python
[
1,2,3,4,5,
6,7,8,9,
10,11,12,
13,14,15,
16,17,18,19
]
```

---

# Important

Generator:

```text
Lazy evaluation
```

List:

```text
Eager evaluation
```

---

# Lazy Evaluation

Means:

```text
Generate values only when needed.
```

Example:

Need first value:

Generator:

```text
Produces first value only.
```

List:

```text
Creates everything.
```

---

# Even Number Generator

```python
def mygen():

    for i in range(1,20):

        if i % 2 == 0:

            yield i
```

---

Output

```text
2
4
6
8
10
12
14
16
18
```

---

# Fibonacci Generator

```python
def myfibo():

    num1 = 0
    num2 = 1

    count = 0

    while count < 10:

        yield num1

        num1, num2 = num2, num1 + num2

        count += 1
```

---

# Execution

Initial:

```text
num1 = 0
num2 = 1
```

---

First yield

```text
yield 0

num1 = 1
num2 = 1
```

---

Second

```text
yield 1

num1 = 1
num2 = 2
```

---

Third

```text
yield 1

num1 = 2
num2 = 3
```

---

Continues:

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

# Store Fibonacci into List

```python
list1 = list(myfibo())
```

Output:

```python
[0,1,1,2,3,5,8,13,21,34]
```

---

# Generator Expressions

Generator expressions are:

```text
Anonymous generators.
```

Like:

```text
Lambda for generators.
```

---

# Syntax

List Comprehension:

```python
[expression for item in iterable]
```

Generator Expression:

```python
(expression for item in iterable)
```

Only difference:

```text
[]
↓

()
```

---

# List Comprehension

```python
list2 = [i**2 for i in range(10)]
```

Output:

```python
[0,1,4,9,16,25,36,49,64,81]
```

---

# What Happens?

Python creates ALL squares immediately.

Memory:

```text
Higher
```

---

# Generator Expression

```python
gen2 = (i**2 for i in range(10))
```

Output:

```text
<generator object>
```

No values generated yet.

---

# next() on Generator Expression

```python
print(next(gen2))
```

Output:

```text
0
```

---

Next:

```python
print(next(gen2))
```

Output:

```text
1
```

---

Next:

```python
print(next(gen2))
```

Output:

```text
4
```

---

Then:

```text
9
16
25
...
```

Generated only when requested.

---

# Even Generator Expression

```python
gen2 = (
    i
    for i in range(40)
    if i % 2 == 0
)
```

---

Output

```text
0
2
4
6
8
10
12
14
16
18
20
22
24
26
28
30
32
34
36
38
```

---

# Generator vs List Comprehension

| Feature | List Comprehension | Generator Expression |
|----------|-------------------|-----------------------|
| Syntax | `[]` | `()` |
| Creates all values | Yes | No |
| Memory Efficient | No | Yes |
| Lazy Evaluation | No | Yes |
| Returns | List | Generator |
| next() supported | No | Yes |

---

# Generator vs Iterator

| Generator | Iterator |
|-----------|-----------|
| Easier to write | Harder to write |
| Uses `yield` | Need `__iter__()` and `__next__()` |
| Python creates iterator methods automatically | You implement them |
| Less code | More boilerplate |

---

# Iterator vs Generator

Iterator:

```python
class MyIter:

    def __iter__(self):
        return self

    def __next__(self):
        ...
```

Generator:

```python
def mygen():

    yield value
```

Same result.

Generator is simply:

```text
Python's shortcut for building iterators.
```

---

# Complete Flow

```text
Generator Function
↓
Contains yield
↓
Generator Object Created
↓
next()
↓
yield value
↓
Pause
↓
Resume from same point
↓
yield next value
↓
Pause
↓
Repeat
↓
StopIteration
```

---

# Quick Revision

```text
Generator
↓
Special function using yield

yield
↓
Returns value + pauses execution

return
↓
Returns value + terminates execution

Generators
↓
Automatically implement iterators

next()
↓
Resumes execution after previous yield

Generator Expression
↓
(expression for item in iterable)

Advantages
↓
Memory efficient
Lazy evaluation
Cleaner than custom iterators
Ideal for large datasets
```
