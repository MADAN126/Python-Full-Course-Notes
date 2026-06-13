# Python Indentation

## What is Indentation?

Indentation refers to the spaces or tabs present at the beginning of a line of code.

Python uses indentation to identify and separate blocks of code. Unlike Java, C, or C++, Python does not use curly braces (`{}`) to define blocks. Instead, indentation itself becomes part of the language syntax.

Because indentation has syntactical meaning, incorrect indentation leads to program errors.

---

## Why Does Python Use Indentation?

In many programming languages, code blocks are defined using braces.

### Java Example

```java
if(age >= 18){
    System.out.println("Adult");
}
```

### Python Equivalent

```python
if age >= 18:
    print("Adult")
```

Python replaces braces with indentation, making code cleaner and more readable.

---

## What is a Code Block?

A code block is a group of statements that belong together and execute as a unit.

Examples of statements that create code blocks:

- `if`
- `elif`
- `else`
- `for`
- `while`
- `def`
- `class`
- `try`
- `except`

Whenever one of these statements ends with a colon (`:`), Python expects an indented block immediately after it.

```python
if x > 0:
    print("Positive")
```

The indented statement forms the block of the `if` statement.

---

## Colon and Indentation Relationship

A colon (`:`) indicates the start of a new block.

```python
if x > 0:
```

After encountering the colon, Python expects one or more indented statements.

```python
if x > 0:
    print("Positive")
```

If indentation is missing:

```python
if x > 0:
print("Positive")
```

Output:

```text
IndentationError: expected an indented block
```

---

## How Python Interprets Indentation

```python
if x > 0:
    print("Line 1")
    print("Line 2")
    print("Line 3")
```

All three statements belong to the same block because they have the same indentation level.

Python interprets it as:

```text
IF x > 0 THEN
    Execute Line 1
    Execute Line 2
    Execute Line 3
END IF
```

---

## Ending a Block

A block ends when indentation decreases.

```python
if x > 0:
    print("Inside Block")

print("Outside Block")
```

The second `print()` statement is outside the `if` block because its indentation level returned to the previous level.

---

## Indentation in Loops

### Example

```python
for i in range(5):
    print(i)
```

Output:

```text
0
1
2
3
4
```

The indented statement executes during every iteration of the loop.

Python interprets it as:

```text
Repeat 5 times:
    print(i)
```

---

## Multiple Statements Inside a Loop

```python
for i in range(3):
    print(i)
    print("Hello")
```

Output:

```text
0
Hello
1
Hello
2
Hello
```

Both statements belong to the loop because both are equally indented.

---

## Statement Outside the Loop

```python
for i in range(3):
    print(i)

print("Finished")
```

Output:

```text
0
1
2
Finished
```

`Finished` executes only once because it is outside the loop.

---

## Nested Indentation

A block can contain another block.

```python
for i in range(3):
    if i % 2 == 0:
        print(i)
```

Indentation levels:

```text
Level 0 -> for
Level 1 -> if
Level 2 -> print
```

Each deeper indentation level represents a deeper block.

---

## Indentation Levels

```python
if x > 0:
    print("Level 1")

    if x > 10:
        print("Level 2")

print("Level 0")
```

```text
Level 0 -> Outside all blocks
Level 1 -> Inside first block
Level 2 -> Inside nested block
```

---

## Common Errors

### Missing Indentation

```python
if x > 0:
print(x)
```

Error:

```text
IndentationError: expected an indented block
```

---

### Unequal Indentation

```python
if x > 0:
    print("A")
      print("B")
```

Error:

```text
IndentationError
```

All statements in the same block must have identical indentation.

---

### Mixing Tabs and Spaces

```python
if x > 0:
    print("A")
	print("B")
```

Mixing tabs and spaces can cause indentation-related errors.

Use 4 spaces consistently.

---

## Best Practices

- Use 4 spaces for each indentation level.
- Maintain consistent indentation throughout the program.
- Do not mix tabs and spaces.
- Align statements belonging to the same block.
- Use proper indentation to improve readability.

---

## Important Rules

1. A colon (`:`) usually starts a new block.
2. Every block must contain at least one indented statement.
3. Statements with the same indentation belong to the same block.
4. Increasing indentation enters a new block.
5. Decreasing indentation exits the current block.
6. Incorrect indentation causes `IndentationError`.

---

## Interview Definition

**Indentation is the leading whitespace before a statement. Python uses indentation to define and separate code blocks. Statements with the same indentation belong to the same block, and incorrect indentation results in an `IndentationError`.**