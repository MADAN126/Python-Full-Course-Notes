# LAMBDA, FILTER, MAP AND REDUCE

These four concepts are often used together to process collections like lists and tuples.

```text
Filter → Select items
Map    → Transform items
Reduce → Combine items
Lambda → Short temporary functions
```

---

# Lambda Function

## Definition

A lambda function is an anonymous function.

Anonymous means:

```text
No function name.
```

It is usually used for small operations that are needed only once.

---

# Syntax

```python
lambda parameters: expression
```

Equivalent to:

```python
def function(parameters):
    return expression
```

---

# Example

Normal function:

```python
def add10(a):
    return a + 10
```

Lambda:

```python
add10 = lambda a: a + 10
```

Usage:

```python
print(add10(5))
```

Output:

```python
15
```

---

# Multiple Arguments

```python
product = lambda a, b: a * b

print(product(5, 6))
```

Output:

```python
30
```

---

```python
addition = lambda a, b, c: a + b + c

print(addition(5, 6, 2))
```

Output:

```python
13
```

---

# Lambda with *args

```python
res = lambda *args: sum(args)

print(res(10, 20))
print(res(10, 20, 30, 40))
```

Output:

```python
30
100
```

---

# Lambda with **kwargs

```python
res = lambda **kwargs: sum(kwargs.values())

print(res(a=10, b=20, c=30))
```

Output:

```python
60
```

---

# Returning Lambda from Functions

Example:

```python
def myfunc(n):
    return lambda a: a + n
```

Usage:

```python
add10 = myfunc(10)
add20 = myfunc(20)

print(add10(5))
print(add20(5))
```

Output:

```python
15
25
```

Explanation:

```text
n = 10 → add 10
n = 20 → add 20
```

---

# FILTER

## Definition

Filter selects elements that satisfy a condition.

It removes unwanted elements.

---

# Syntax

```python
filter(function, iterable)
```

---

# Working

```text
Take an item
↓
Apply condition
↓
True?
↓
Yes → Keep it
No  → Discard it
```

---

# Example Using Function

```python
numbers = [1,2,3,4,5,6,7,8,9]

def odd(n):
    return n % 2 == 1

odd_numbers = list(filter(odd, numbers))

print(odd_numbers)
```

Output:

```python
[1, 3, 5, 7, 9]
```

---

# Example Using Lambda

```python
numbers = [1,2,3,4,5,6,7,8,9]

odd_numbers = list(
    filter(lambda n: n % 2 == 1, numbers)
)

print(odd_numbers)
```

Output:

```python
[1, 3, 5, 7, 9]
```

---

# More Filter Examples

Even numbers:

```python
even = list(
    filter(lambda n: n % 2 == 0, numbers)
)
```

Output:

```python
[2, 4, 6, 8]
```

---

Uppercase strings:

```python
words = ['one', 'TWO', 'three', 'FOUR']

upper = list(
    filter(lambda x: x.isupper(), words)
)

print(upper)
```

Output:

```python
['TWO', 'FOUR']
```

---

Numeric strings:

```python
data = ['one', '88', '99', 'abc']

nums = list(
    filter(lambda x: x.isnumeric(), data)
)

print(nums)
```

Output:

```python
['88', '99']
```

---

# MAP

## Definition

Map transforms every element of an iterable.

It applies a function to each item.

---

# Syntax

```python
map(function, iterable)
```

---

# Working

```text
Take item
↓
Apply function
↓
Store result
↓
Move to next item
```

---

# Example Using Function

```python
def double(n):
    return n * 2

numbers = [1,2,3,4]

result = list(map(double, numbers))

print(result)
```

Output:

```python
[2, 4, 6, 8]
```

---

# Example Using Lambda

```python
numbers = [1,2,3,4]

result = list(
    map(lambda n: n * 2, numbers)
)

print(result)
```

Output:

```python
[2, 4, 6, 8]
```

---

# Square Numbers

```python
numbers = [1,2,3,4]

squares = list(
    map(lambda n: n * n, numbers)
)

print(squares)
```

Output:

```python
[1, 4, 9, 16]
```

---

# Multiple Iterables

```python
list1 = [1,2,3,4]
list2 = [5,6,7,8]

result = list(
    map(lambda x, y: x + y, list1, list2)
)

print(result)
```

Output:

```python
[6, 8, 10, 12]
```

---

# REDUCE

## Definition

Reduce repeatedly combines elements into a single value.

Unlike map and filter:

```text
Filter → Many items
Map    → Many items
Reduce → One final result
```

---

# Import

```python
from functools import reduce
```

---

# Syntax

```python
reduce(function, iterable)
```

---

# Working

Example:

```python
reduce(lambda a,b: a+b, [1,2,3,4])
```

Execution:

```text
1 + 2 = 3
3 + 3 = 6
6 + 4 = 10
```

Final Result:

```python
10
```

---

# Sum Example

```python
from functools import reduce

numbers = [2, 6, 10, 14, 18]

result = reduce(
    lambda a, b: a + b,
    numbers
)

print(result)
```

Output:

```python
50
```

---

# Product Example

```python
from functools import reduce
import operator

numbers = [1,2,3,4]

product = reduce(operator.mul, numbers)

print(product)
```

Output:

```python
24
```

Calculation:

```text
1×2×3×4
```

---

# Minimum Value

```python
numbers = [4,1,9,3]

minimum = reduce(
    lambda a,b: a if a < b else b,
    numbers
)

print(minimum)
```

Output:

```python
1
```

---

# Maximum Value

```python
maximum = reduce(
    lambda a,b: a if a > b else b,
    numbers
)

print(maximum)
```

Output:

```python
9
```

---

# String Concatenation

```python
result = reduce(
    lambda a,b: a+b,
    ["Python", " ", "Rocks"]
)

print(result)
```

Output:

```python
Python Rocks
```

---

# Putting Everything Together

Problem:

```text
Take a list
↓
Keep odd numbers
↓
Double them
↓
Find their sum
```

---

Step 1: Filter

```python
numbers = [1,2,3,4,5,6,7,8,9]

odd = list(
    filter(lambda n: n % 2 == 1, numbers)
)
```

Output:

```python
[1,3,5,7,9]
```

---

Step 2: Map

```python
doubles = list(
    map(lambda n: n * 2, odd)
)
```

Output:

```python
[2,6,10,14,18]
```

---

Step 3: Reduce

```python
total = reduce(
    lambda a,b: a+b,
    doubles
)

print(total)
```

Output:

```python
50
```

---

# Combined Version

```python
from functools import reduce

numbers = [1,2,3,4,5,6,7,8,9]

result = reduce(
    lambda a,b: a+b,
    map(
        lambda n: n*2,
        filter(
            lambda n: n%2==1,
            numbers
        )
    )
)

print(result)
```

Output:

```python
50
```

---

# Filter vs Map vs Reduce

| Feature | Filter | Map | Reduce |
|----------|---------|------|---------|
| Purpose | Select items | Transform items | Combine items |
| Output Size | Same or smaller | Same size | Single value |
| Returns | Iterator | Iterator | One value |
| Example | Odd numbers | Double numbers | Sum |

---

# Important Points

- Lambda creates short anonymous functions.
- Filter keeps elements that satisfy a condition.
- Map transforms every element.
- Reduce combines elements into one result.
- `filter()` and `map()` return iterators.
- `reduce()` is available in `functools`.
- These are commonly used together in functional programming.

---

# Quick Revision

```text
Lambda
↓
Anonymous function

Filter
↓
Select items

Map
↓
Modify items

Reduce
↓
Combine items

Pipeline
↓
Filter → Map → Reduce
```
