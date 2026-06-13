# METHOD OVERRIDING IN PYTHON

## Definition

Method overriding happens when a child class provides its own implementation of a method that already exists in the parent class.

Same method name.

Same parameters.

Different implementation.

---

# Why Override?

Inheritance gives reuse.

Overriding gives customization.

```text
Parent:
"Default behavior"

Child:
"I want different behavior"
```

---

# Real-Life Example

```text
Person → greet()

Student → greet()

Teacher → greet()
```

Everyone greets.

But differently.

---

# Parent Class

```python
class Person:

    def greet(self):
        print("Hello Person")
```

Default behavior:

```text
Hello Person
```

---

# Child Class

```python
class Student(Person):

    def greet(self):
        print("Hello Student")
```

Student says:

```text
Ignore parent's version.

Use mine.
```

---

# Complete Example

```python
class Person:

    def __init__(self, name, age, gender):

        self.name = name
        self.age = age
        self.gender = gender

    def greet(self):

        print("Hello Person")


class Student(Person):

    def __init__(self,
                 name,
                 age,
                 gender,
                 studentid,
                 fees):

        Person.__init__(
            self,
            name,
            age,
            gender
        )

        self.studentid = studentid
        self.fees = fees

    def greet(self):

        print("Hello Student")
```

---

# Student Object

```python
stud = Student(
    'Gabriel',
    56,
    'Male',
    45,
    345678
)

stud.greet()
```

Output:

```text
Hello Student
```

---

# What Happened Internally?

Python sees:

```python
stud.greet()
```

Search order:

```text
Student
↓
greet() found?
↓
YES
↓
Execute Student.greet()
```

Parent method is ignored.

---

# Parent Object

```python
person1 = Person(
    'Gabriel',
    56,
    'Male'
)

person1.greet()
```

Output:

```text
Hello Person
```

---

# Internal Flow

Python sees:

```python
person1.greet()
```

Search:

```text
Person
↓
greet() found?
↓
YES
↓
Execute Person.greet()
```

---

# The Biggest Rule

## The object decides.

NOT the reference.

NOT inheritance hierarchy.

The actual object.

---

# Visualization

Parent:

```python
def greet():
    print("Hello Person")
```

Child:

```python
def greet():
    print("Hello Student")
```

Objects:

```python
Person()
↓
Hello Person

Student()
↓
Hello Student
```

---

# Method Lookup Flow

## Parent Object

```python
person1.greet()
```

Flow:

```text
person1
↓
Person
↓
greet()
↓
Hello Person
```

---

## Student Object

```python
stud.greet()
```

Flow:

```text
stud
↓
Student
↓
greet()
↓
Hello Student
```

---

# Before Overriding

Parent:

```python
class Person:

    def greet(self):
        print("Hello Person")
```

Child:

```python
class Student(Person):
    pass
```

Student object:

```python
s = Student()

s.greet()
```

Output:

```text
Hello Person
```

Reason:

```text
Student doesn't have greet().

Python goes to Person.
```

---

# After Overriding

Parent:

```python
class Person:

    def greet(self):
        print("Hello Person")
```

Child:

```python
class Student(Person):

    def greet(self):
        print("Hello Student")
```

Output:

```text
Hello Student
```

Reason:

```text
Student has its own greet().

Python stops there.
```

---

# Calling Parent Method Inside Override

Suppose we want both.

Parent greeting.

Then student greeting.

---

Example:

```python
class Student(Person):

    def greet(self):

        super().greet()

        print("Hello Student")
```

Object:

```python
s = Student()

s.greet()
```

Output:

```text
Hello Person
Hello Student
```

---

# Internal Flow

```text
s.greet()
↓
Student.greet()
↓
super().greet()
↓
Person.greet()
↓
Hello Person
↓
Back to Student.greet()
↓
Hello Student
```

---

# Overriding vs Inheritance

## Inheritance

```text
Reuse parent methods.
```

Example:

```python
Student uses Person.greet()
```

---

## Overriding

```text
Replace parent methods.
```

Example:

```python
Student defines its own greet().
```

---

# Overriding vs Overloading

## Overriding

Child changes parent method.

```python
class Parent:
    def show():
        ...

class Child(Parent):
    def show():
        ...
```

Different classes.

Inheritance required.

---

## Overloading

Same method name.

Different parameter lists.

Example (Java):

```java
add(int a,int b)

add(int a,int b,int c)
```

Python does NOT support true method overloading.

---

# Why Overriding Is Important

Without overriding:

```text
All children behave exactly like parent.
```

With overriding:

```text
Each child can have specialized behavior.
```

Example:

```text
Animal → sound()

Dog → Bark

Cat → Meow

Cow → Moo
```

Same method.

Different implementations.

---

# CONTAINERS IN PYTHON

## Definition

Containers are objects that hold other objects.

They store multiple values together.

---

# Examples

```python
list
tuple
set
dict
str
```

---

# Membership Test

Use:

```python
in
```

to check whether something exists.

---

# List Example

```python
list1 = [
    'asif',
    'john',
    'Michael',
    'Basit'
]
```

Check membership:

```python
'asif' in list1
```

Output:

```text
True
```

---

```python
'Alex' in list1
```

Output:

```text
False
```

---

# How 'in' Works

```text
'asif' in list1

↓

Compare with 'asif'
↓

Found?

↓

True
```

---

# assert Statement

## Definition

Assert checks whether a condition is true.

If true:

```text
Nothing happens.
```

If false:

```text
Program raises AssertionError.
```

---

Example

```python
assert 'john' in list1
```

Output:

```text
No output
```

Condition passed.

---

Example

```python
assert 'john1' in list1
```

Output:

```text
AssertionError
```

Reason:

```text
john1 does not exist.
```

---

# Dictionary Membership

Dictionary membership checks KEYS.

NOT values.

---

Dictionary:

```python
mydict = {
    'Name': 'Asif',
    'ID': 12345,
    'DOB': 1991,
    'Address': 'Helsinki'
}
```

---

Check value:

```python
'Asif' in mydict
```

Output:

```text
False
```

Reason:

```text
Asif is a value.
```

---

Check key:

```python
'Name' in mydict
```

Output:

```text
True
```

---

```python
'DOB' in mydict
```

Output:

```text
True
```

---

# String Membership

Strings are containers too.

Example:

```python
mystr = 'asifbhat'
```

Check substring:

```python
'as' in mystr
```

Output:

```text
True
```

---

```python
'xyz' in mystr
```

Output:

```text
False
```

---

# Quick Revision

```text
Method Overriding
↓
Child replaces parent method

Object decides
↓
Parent object → Parent method

Child object → Child method

super()
↓
Call parent version

Containers
↓
Objects holding multiple values

in
↓
Membership test

assert
↓
Condition checker

Dictionary membership
↓
Checks KEYS only

String membership
↓
Checks substrings
```
