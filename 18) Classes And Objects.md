# CLASSES & OBJECTS IN PYTHON

## What is a Class?

A class is a blueprint used to create objects.

It defines:

- What data an object will have.
- What actions an object can perform.

Example:

```text
Blueprint → House Plan
Object    → Actual House

Blueprint → Employee Class
Object    → Individual Employees
```

---

# What is an Object?

An object is an instance of a class.

It contains:

- Variables (attributes/properties)
- Functions (methods)

Example:

```python
emp1 = Employee(...)
emp2 = Employee(...)
```

Both are objects of the same class.

---

# Class Syntax

```python
class ClassName:
    statements
```

Example:

```python
class MyClass:
    pass
```

---

# Simple Class Example

```python
class MyClass:
    var1 = 10
```

Create object:

```python
obj1 = MyClass()
```

Access property:

```python
print(obj1.var1)
```

Output:

```python
10
```

---

# Execution Flow

```text
Class Definition
       ↓
Blueprint Created
       ↓
Object Created
       ↓
Object Gets Access
to Class Members
```

---

# Docstring

The first string inside a class is called a docstring.

It describes the purpose of the class.

Example:

```python
class Employee:
    """
    Represents an employee.
    """
```

Access:

```python
print(Employee.__doc__)
```

Output:

```python
Represents an employee.
```

---

# Constructor (__init__)

## Definition

`__init__()` is a special method.

It automatically executes when an object is created.

Used for:

- Initializing object attributes.
- Performing setup operations.

---

# Syntax

```python
class Employee:

    def __init__(self):
        pass
```

---

# Example

```python
class Employee:

    def __init__(self, name, empid):
        self.name = name
        self.empid = empid
```

Object creation:

```python
emp1 = Employee("Asif", 34163)
```

Execution:

```text
Employee("Asif",34163)
        ↓
__init__ called automatically
        ↓
self.name = "Asif"
self.empid = 34163
```

---

# self

## Definition

`self` refers to the current object.

It is used to access object attributes and methods.

Example:

```python
self.name
```

means:

```text
Current object's name
```

---

# Why self Is Needed

Without `self`:

Python cannot determine which object's data should be used.

Example:

```python
emp1.name
emp2.name
```

Both use the same class.

`self` tells Python:

```text
Use emp1's data
or
Use emp2's data
```

depending on the caller.

---

# Employee Example

```python
class Employee:

    def __init__(self, name, empid):
        self.name = name
        self.empid = empid

    def greet(self):
        print(
            "Thanks for joining ABC Company {}!!"
            .format(self.name)
        )
```

---

# Creating Objects

```python
emp1 = Employee("Asif", 34163)
```

Output:

```python
print(emp1.name)
print(emp1.empid)
```

```text
Asif
34163
```

---

Method call:

```python
emp1.greet()
```

Output:

```text
Thanks for joining ABC Company Asif!!
```

---

# What Happens Internally?

When Python sees:

```python
emp1.greet()
```

It converts it into:

```python
Employee.greet(emp1)
```

Therefore:

```python
self
```

receives:

```python
emp1
```

---

# Multiple Objects

```python
emp1 = Employee("Asif", 34163)

emp2 = Employee("Michael", 34162)
```

Objects contain separate data.

```python
print(emp1.name)
print(emp2.name)
```

Output:

```text
Asif
Michael
```

---

# Memory View

```text
Employee Class
       ↓

emp1 ----------------→ name = Asif
                        empid = 34163

emp2 ----------------→ name = Michael
                        empid = 34162
```

---

# Modifying Object Properties

Object attributes can be changed.

Example:

```python
emp1.name = "Basit"

print(emp1.name)
```

Output:

```python
Basit
```

---

# Deleting Object Properties

Example:

```python
del emp1.empid
```

Trying to access:

```python
print(emp1.empid)
```

Output:

```python
AttributeError
```

Reason:

```text
empid no longer exists.
```

---

# Deleting Objects

Example:

```python
del emp1
```

Trying to use it:

```python
print(emp1)
```

Output:

```python
NameError
```

Reason:

```text
Reference to the object was removed.
```

---

# super()

## Definition

`super()` provides access to the parent class.

Used mainly in inheritance.

Benefits:

- Avoids explicitly writing parent class names.
- Supports multiple inheritance.
- Makes code easier to maintain.

---

# Example

```python
class Person:

    def __init__(self, name):
        self.name = name


class Employee(Person):

    def __init__(self, name, empid):

        super().__init__(name)

        self.empid = empid
```

Object:

```python
emp = Employee("Asif", 34163)

print(emp.name)
print(emp.empid)
```

Output:

```text
Asif
34163
```

---

# Execution Flow of Object Creation

```text
Employee("Asif",34163)
        ↓
Memory Allocated
        ↓
Object Created
        ↓
self refers to object
        ↓
__init__ executes
        ↓
Attributes initialized
        ↓
Object returned
```

---

# Class vs Object

| Feature | Class | Object |
|----------|---------|---------|
| Meaning | Blueprint | Instance |
| Memory | Once | Separate for each object |
| Created Using | `class` | Class constructor |
| Contains | Attributes and methods | Actual data |
| Example | `Employee` | `emp1` |

---

# Important Points

- A class is a blueprint.
- Objects are instances of classes.
- Classes are created using `class`.
- `__init__()` executes automatically during object creation.
- `self` refers to the current object.
- Methods always receive `self` as the first parameter.
- Objects have independent data.
- Object attributes can be modified or deleted.
- `super()` is used to access parent class functionality.

---

# Quick Revision

```text
Class
↓
Blueprint

Object
↓
Instance of class

__init__()
↓
Constructor
Runs automatically

self
↓
Current object

super()
↓
Access parent class

Object Creation
↓
Create object
↓
Run __init__
↓
Initialize attributes
```
