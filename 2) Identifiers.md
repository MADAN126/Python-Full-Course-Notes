# IDENTIFIERS

## Definition

An identifier is the name given to program elements such as:

- Variables
- Functions
- Classes
- Modules
- Objects

Identifiers help Python distinguish one entity from another.

Example:

```python
age = 20
```

Here,

```python
age
```

is an identifier.

---

# Rules for Identifiers

## 1. Cannot Start with a Digit

❌ Invalid

```python
1var = 10
```

Output:

```python
SyntaxError: invalid syntax
```

Reason:

Python reads identifiers from left to right.

If the first character is a digit, Python treats it as a number, not a name.

---

✅ Valid

```python
var1 = 10
```

```python
student2 = 50
```

---

## 2. Cannot Contain Special Symbols

Allowed special character:

```python
_
```

Not allowed:

```text
@
#
$
%
&
!
-
+
*
.
?
```

---

❌ Invalid

```python
val2@ = 35
```

Output:

```python
SyntaxError: invalid syntax
```

---

✅ Valid

```python
val_2 = 35
```

```python
student_name = "John"
```

---

## 3. Keywords Cannot Be Used

Keywords already have predefined meanings in Python.

---

❌ Invalid

```python
import = 125
```

Output:

```python
SyntaxError: invalid syntax
```

---

✅ Valid

```python
imports = 125
```

```python
import_count = 125
```

---

## 4. Can Start with a Letter

Lowercase letters:

```python
a to z
```

Uppercase letters:

```python
A to Z
```

---

Examples:

```python
name = "Alex"

Age = 25

Student = "John"
```

All are valid identifiers.

---

## 5. Underscore (_) Is Allowed

Identifiers can begin with an underscore.

Examples:

```python
_value = 100

_student = "Sam"
```

Valid identifiers.

---

## 6. Python Is Case Sensitive

Uppercase and lowercase are treated differently.

Example:

```python
age = 20
Age = 30
AGE = 40
```

These are three different identifiers.

---

# Correct Examples

```python
val2 = 10

val_ = 99

student_name = "David"

_marks = 450

totalAmount = 5000
```

---

# Invalid Examples

```python
1name = "Alex"      # Starts with digit

user@id = 10        # Contains @

class = "Python"    # Keyword used

first-name = "Sam"  # Hyphen not allowed

total amount = 50   # Space not allowed
```

---

# Valid vs Invalid

| Identifier | Valid | Reason |
|----------|---------|---------|
| `name` | ✅ | Letters only |
| `name1` | ✅ | Letters and digits |
| `_name` | ✅ | Underscore allowed |
| `student_name` | ✅ | Underscore allowed |
| `1name` | ❌ | Starts with digit |
| `user@id` | ❌ | Special character |
| `for` | ❌ | Keyword |
| `first-name` | ❌ | Hyphen not allowed |
| `total amount` | ❌ | Spaces not allowed |

---

# Identifier Naming Guidelines

Although these are not rules, they improve readability.

Variable:

```python
student_name
total_marks
employee_id
```

Function:

```python
calculate_total()
display_result()
```

Class:

```python
Student
BankAccount
EmployeeDetails
```

Constant:

```python
MAX_SIZE
PI_VALUE
DEFAULT_PORT
```

---

# Execution Flow

```text
Python encounters a name
          ↓
Does it follow naming rules?
          ↓
      Yes      No
       ↓        ↓
Identifier   SyntaxError
is created
```

---

# Important Points

- Identifiers are names given to program elements.
- They can contain letters, digits, and underscores.
- They cannot start with digits.
- They cannot contain special symbols except `_`.
- Keywords cannot be used as identifiers.
- Python identifiers are case sensitive.

---

# Quick Revision

```text
Identifiers
↓
Names given by programmers
↓
Used for variables, functions, classes, etc.
↓
Allowed → Letters + Digits + _
↓
Cannot start with digits
↓
Cannot use special symbols
↓
Cannot use keywords
↓
Case Sensitive
```
