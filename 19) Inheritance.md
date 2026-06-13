# INHERITANCE IN PYTHON

## Definition

Inheritance is an OOP feature that allows one class to acquire the properties and methods of another class.

It promotes:

- Code Reusability
- Reduced Duplication
- Easier Maintenance
- Extension of Existing Classes

---

# Real Meaning

Instead of creating everything from scratch:

```text
Existing Class
      ↓
Reuse it
      ↓
Add new features
```

---

# Parent and Child Classes

```text
Parent Class
↓
(Base Class)
(Super Class)

Child Class
↓
(Derived Class)
(Sub Class)
```

---

# IS-A Relationship

Inheritance is used when:

```text
Child IS-A Parent
```

Examples:

```text
Student IS-A Person

Teacher IS-A Person

Car IS-A Vehicle

Dog IS-A Animal
```

---

# Basic Syntax

```python
class Parent:
    pass


class Child(Parent):
    pass
```

---

# Single Inheritance

## Definition

One child inherits from one parent.

---

# Structure

```text
Person
   ↓
Student
```

---

# Example

```python
class Person:

    def __init__(self, name, age, gender):
        self.name = name
        self.age = age
        self.gender = gender

    def PersonInfo(self):
        print("Name:", self.name)
        print("Age:", self.age)
        print("Gender:", self.gender)
```

Child:

```python
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

    def StudentInfo(self):

        print("Student ID:", self.studentid)
        print("Fees:", self.fees)
```

---

# Creating Student Object

```python
stud1 = Student(
    "Asif",
    24,
    "Male",
    123,
    1200
)
```

Access parent method:

```python
stud1.PersonInfo()
```

Output:

```text
Name: Asif
Age: 24
Gender: Male
```

---

Access child method:

```python
stud1.StudentInfo()
```

Output:

```text
Student ID: 123
Fees: 1200
```

---

# Execution Flow

```text
Student Object Created
        ↓
Student.__init__()
        ↓
Person.__init__()
        ↓
Parent attributes initialized
        ↓
Child attributes initialized
        ↓
Object ready
```

---

# Teacher Example

Another child of Person.

```python
class Teacher(Person):

    def __init__(self,
                 name,
                 age,
                 gender,
                 empid,
                 salary):

        Person.__init__(
            self,
            name,
            age,
            gender
        )

        self.empid = empid
        self.salary = salary

    def TeacherInfo(self):

        print("Employee ID:", self.empid)
        print("Salary:", self.salary)
```

---

Object:

```python
teacher1 = Teacher(
    "Basit",
    36,
    "Male",
    456,
    80000
)
```

Output:

```python
teacher1.PersonInfo()
teacher1.TeacherInfo()
```

```text
Name: Basit
Age: 36
Gender: Male
Employee ID: 456
Salary: 80000
```

---

# Why Inheritance?

Without inheritance:

```text
Student class
↓
Duplicate name
Duplicate age
Duplicate gender

Teacher class
↓
Duplicate name
Duplicate age
Duplicate gender
```

Lots of repeated code.

---

With inheritance:

```text
Person
↓
Common properties stored once

Student
Teacher
↓
Only unique features added
```

---

# super()

## Definition

`super()` gives access to the parent class.

Instead of writing:

```python
Person.__init__(...)
```

we write:

```python
super().__init__(...)
```

---

# Why Use super()?

Benefits:

- Cleaner code.
- Avoids hardcoding parent class names.
- Supports multiple inheritance.
- Easier maintenance.

---

# Example Using super()

```python
class Student(Person):

    def __init__(self,
                 name,
                 age,
                 gender,
                 studentid,
                 fees):

        super().__init__(
            name,
            age,
            gender
        )

        self.studentid = studentid
        self.fees = fees

    def StudentInfo(self):

        super().PersonInfo()

        print("Student ID:", self.studentid)
        print("Fees:", self.fees)
```

---

Object:

```python
stud = Student(
    "Asif",
    24,
    "Male",
    123,
    1200
)

stud.StudentInfo()
```

Output:

```text
Name: Asif
Age: 24
Gender: Male
Student ID: 123
Fees: 1200
```

---

# Types of Inheritance

```text
1. Single
2. Multiple
3. Multi-Level
4. Hierarchical
5. Hybrid
```

---

# 1. Single Inheritance

One child inherits one parent.

Structure:

```text
Person
   ↓
Student
```

Example:

```python
class Person:
    pass

class Student(Person):
    pass
```

---

# 2. Multiple Inheritance

## Definition

One child inherits from multiple parents.

---

# Structure

```text
Father      Mother
    \        /
     \      /
      Child
```

---

# Example

```python
class Father:

    def skills1(self):
        print("Driving")


class Mother:

    def skills2(self):
        print("Cooking")


class Child(Father, Mother):

    def skills3(self):
        print("Programming")
```

Object:

```python
c = Child()

c.skills1()
c.skills2()
c.skills3()
```

Output:

```text
Driving
Cooking
Programming
```

---

# Execution Flow

```text
Child Object
     ↓
Looks in Child
     ↓
Not found?
     ↓
Search Father
     ↓
Not found?
     ↓
Search Mother
```

This search order is called:

```text
MRO (Method Resolution Order)
```

---

# MRO Example

```python
print(Child.__mro__)
```

Output:

```text
Child
Father
Mother
object
```

Python follows this order to find methods.

---

# 3. Multi-Level Inheritance

## Definition

A child becomes a parent for another child.

---

# Structure

```text
Grandparent
      ↓
Parent
      ↓
Child
```

---

# Example

```python
class Person:

    def person(self):
        print("I am Person")


class Student(Person):

    def student(self):
        print("I am Student")


class Graduate(Student):

    def graduate(self):
        print("I am Graduate")
```

---

Object:

```python
g = Graduate()

g.person()
g.student()
g.graduate()
```

Output:

```text
I am Person
I am Student
I am Graduate
```

---

# Execution Flow

```text
Graduate Object
      ↓
Graduate
      ↓
Student
      ↓
Person
      ↓
object
```

Methods are searched upward.

---

# 4. Hierarchical Inheritance

## Definition

Multiple children inherit from the same parent.

---

# Structure

```text
        Person
       /      \
      /        \
 Student      Teacher
```

---

Example:

```python
class Person:
    pass

class Student(Person):
    pass

class Teacher(Person):
    pass
```

---

# 5. Hybrid Inheritance

## Definition

Combination of two or more inheritance types.

Usually combines:

```text
Multiple
+
Multi-Level
```

---

# Structure

```text
       A
      / \
     B   C
      \ /
       D
```

---

# object Class

Every Python class ultimately inherits from:

```python
object
```

Example:

```python
class Person:
    pass
```

Internally:

```python
class Person(object):
    pass
```

---

# Inheritance Flow Summary

```text
Create Child Object
        ↓
Child Constructor
        ↓
Parent Constructor
        ↓
Initialize Parent Data
        ↓
Initialize Child Data
        ↓
Object Ready
```

---

# Types Summary

| Type | Structure |
|--------|------------|
| Single | A → B |
| Multiple | A + B → C |
| Multi-Level | A → B → C |
| Hierarchical | A → B and A → C |
| Hybrid | Combination |

---

# Important Points

- Inheritance promotes code reuse.
- Child classes inherit parent properties and methods.
- Inheritance represents an "IS-A" relationship.
- `super()` accesses parent functionality.
- Multiple inheritance follows MRO.
- Multi-level inheritance creates inheritance chains.
- All Python classes ultimately derive from `object`.

---

# Quick Revision

```text
Inheritance
↓
Reuse existing classes

IS-A Relationship
↓
Student IS-A Person

super()
↓
Call parent methods

Single
↓
One Parent

Multiple
↓
Many Parents

Multi-Level
↓
Chain of Parents

Hierarchical
↓
One Parent → Many Children

Hybrid
↓
Combination
```
