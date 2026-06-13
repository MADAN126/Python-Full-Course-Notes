# Python Sets — Deep Practical Notes

## What is a Set?

A Set is an unordered collection of unique values.

```python
s = {1, 2, 3}
```

### Key Rules

- No duplicate values.
- No indexing.
- No slicing.
- Order is not guaranteed.
- Set itself can change.
- Individual elements cannot be modified.

---

## Why Sets Exist

Main purpose:

1. Remove duplicates.
2. Fast membership checking.
3. Mathematical set operations.

Example:

```python
nums = [1,1,2,2,3,3,4]
print(set(nums))
```

Output:

```python
{1,2,3,4}
```

---

# Set Creation

## Normal Set

```python
s = {1,2,3,4,5}
```

---

## Empty Set

Wrong:

```python
s = {}
```

Creates dictionary.

Correct:

```python
s = set()
```

---

## Mixed Data Types

```python
s = {10, "Hello", 2.5, (1,2)}
```

Valid.

---

## Invalid Set Element

```python
s = {1, [2,3]}
```

Error:

```python
TypeError
```

Reason:

Lists are mutable.

Only immutable objects can become set elements.

Allowed:

```python
int
float
str
tuple
bool
frozenset
```

Not allowed:

```python
list
dict
set
```

---

# Duplicate Removal

```python
s = {1,1,1,2,2,3}
print(s)
```

Output:

```python
{1,2,3}
```

Set automatically removes duplicates.

---

# Length

```python
s = {1,2,3,4}
len(s)
```

Output:

```python
4
```

---

# Unordered Nature

```python
s = {10,20,30}
print(s)
```

Output may appear as:

```python
{20,10,30}
```

or

```python
{30,20,10}
```

Never depend on order.

---

# Traversing a Set

```python
s = {"A","B","C"}

for item in s:
    print(item)
```

---

## Using enumerate()

```python
for i, value in enumerate(s):
    print(i, value)
```

Index produced by enumerate is temporary.

Sets do NOT have real indexes.

---

# Membership Testing

Most important real-world use.

```python
s = {"apple", "banana", "mango"}

print("apple" in s)
```

Output:

```python
True
```

---

```python
print("grape" in s)
```

Output:

```python
False
```

Membership checking in sets is extremely fast.

---

# Add Elements

## add()

```python
s = {1,2,3}

s.add(4)

print(s)
```

Output:

```python
{1,2,3,4}
```

---

## Duplicate Add

```python
s.add(4)
```

Nothing happens.

No duplicates allowed.

---

# Add Multiple Elements

## update()

```python
s = {1,2}

s.update([3,4,5])

print(s)
```

Output:

```python
{1,2,3,4,5}
```

---

```python
s.update((6,7))
```

Works.

---

# Remove Elements

## remove()

```python
s = {1,2,3}

s.remove(2)
```

Result:

```python
{1,3}
```

---

### Danger

```python
s.remove(10)
```

Error:

```python
KeyError
```

Because value doesn't exist.

---

## discard()

Safer version.

```python
s.discard(10)
```

No error.

Nothing happens.

---

### Interview Rule

```text
remove() → error if missing

discard() → no error if missing
```

---

## pop()

```python
s = {10,20,30}

s.pop()
```

Removes random element.

Because sets have no order.

---

## clear()

```python
s.clear()
```

Result:

```python
set()
```

Empty set.

---

## del

```python
del s
```

Deletes entire set object.

---

# Copying Sets

## Reference Copy

```python
a = {1,2,3}
b = a
```

Both point to same set.

```python
a.add(4)

print(b)
```

Output:

```python
{1,2,3,4}
```

Both affected.

---

## Real Copy

```python
a = {1,2,3}
b = a.copy()
```

Independent objects.

```python
a.add(4)
```

b remains unchanged.

---

# Set Operations

Most important section.

---

## Union

Meaning:

All unique elements.

```python
A = {1,2,3}
B = {3,4,5}

A | B
```

Output:

```python
{1,2,3,4,5}
```

---

```python
A.union(B)
```

Same result.

---

### Memory Trick

```text
Union = Combine Everything
```

---

## Intersection

Meaning:

Common elements.

```python
A = {1,2,3}
B = {3,4,5}

A & B
```

Output:

```python
{3}
```

---

```python
A.intersection(B)
```

Same result.

---

### Memory Trick

```text
Intersection = Common Ground
```

---

## Difference

Meaning:

Present in first set only.

```python
A = {1,2,3}
B = {3,4,5}

A - B
```

Output:

```python
{1,2}
```

---

```python
B - A
```

Output:

```python
{4,5}
```

---

### Memory Trick

```text
A - B

Take A
Remove everything from B
```

---

## Symmetric Difference

Meaning:

Values in either set but not both.

```python
A = {1,2,3}
B = {3,4,5}

A ^ B
```

Output:

```python
{1,2,4,5}
```

---

### Memory Trick

```text
Keep outsiders
Remove common members
```

---

# Update Variants

These modify original set.

---

## intersection_update()

```python
A.intersection_update(B)
```

A becomes common values only.

---

## difference_update()

```python
A.difference_update(B)
```

A keeps only unique values.

---

## symmetric_difference_update()

```python
A.symmetric_difference_update(B)
```

A becomes exclusive values.

---

# Subset

Meaning:

Everything inside B exists in A.

```python
A = {1,2,3,4,5}
B = {2,3}

B.issubset(A)
```

Output:

```python
True
```

---

### Memory Trick

```text
Subset = Smaller box inside bigger box
```

---

# Superset

Meaning:

Contains all elements of another set.

```python
A.issuperset(B)
```

Output:

```python
True
```

---

### Memory Trick

```text
Superset = Bigger box
```

---

# Disjoint Sets

Meaning:

No common elements.

```python
A = {1,2,3}
B = {7,8,9}

A.isdisjoint(B)
```

Output:

```python
True
```

---

### Memory Trick

```text
Disjoint = Completely Separate
```

---

# Built-in Functions

## Sum

```python
sum({1,2,3})
```

Output:

```python
6
```

---

## Max

```python
max({5,2,8})
```

Output:

```python
8
```

---

## Min

```python
min({5,2,8})
```

Output:

```python
2
```

---

## Sorted

```python
s = {8,2,5,1}

sorted(s)
```

Output:

```python
[1,2,5,8]
```

Returns List.

Original set unchanged.

---

# Set vs List vs Tuple

| Feature | List | Tuple | Set |
|----------|----------|----------|----------|
| Ordered | ✅ | ✅ | ❌ |
| Indexed | ✅ | ✅ | ❌ |
| Mutable | ✅ | ❌ | ✅ |
| Duplicates | ✅ | ✅ | ❌ |
| Fast Search | ❌ | ❌ | ✅ |

---

# Interview Kill Points

### Q1: Why use Set?

```text
To remove duplicates and perform fast membership testing.
```

---

### Q2: Can Set contain List?

```text
No.
Lists are mutable and unhashable.
```

---

### Q3: Can Set contain Tuple?

```text
Yes.
Tuples are immutable.
```

---

### Q4: Difference between remove() and discard()?

```text
remove() → KeyError if absent

discard() → No error if absent
```

---

### Q5: Why no indexing in Set?

```text
Because sets are unordered.
```

---

# One-Line Revision

```text
Set = Unordered + Unique + Fast Search

add()      → add one item
update()   → add many items
remove()   → delete (error if absent)
discard()  → delete (safe)
clear()    → empty set
copy()     → clone set

|  → Union
&  → Intersection
-  → Difference
^  → Symmetric Difference

issubset()
issuperset()
isdisjoint()

Best use:
Remove duplicates and perform fast lookups.
```