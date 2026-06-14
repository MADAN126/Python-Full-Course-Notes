# PYTHON OOP — UNDERSTANDING-FIRST NOTES

---

# What is OOP?

## Definition

OOP (Object-Oriented Programming) is a way of writing programs by modeling real-world things as **objects**.

Instead of thinking:

> "What functions should I write?"

You think:

> "What things exist in my system, what data do they have, and what actions can they perform?"

---

## Traditional Programming Thinking

```text
Program
│
├─ function1()
├─ function2()
├─ function3()
└─ shared variables
```

Problem:

• Data and behavior become separated.
• Large programs become difficult to manage.

---

## OOP Thinking

```text
Object
│
├─ Data (Attributes)
└─ Behavior (Methods)
```

Example:

```text
Bank Account

Data:
• account_number
• balance

Behavior:
• deposit()
• withdraw()
• check_balance()
```

Everything related to Bank Account stays together.

---

# Why OOP Exists

OOP solves problems that appear in large software systems.

Without OOP:

```python
name1 = "John"
age1 = 25

name2 = "Mike"
age2 = 30

name3 = "Sara"
age3 = 28
```

As data grows:

```text
100 people
500 people
10000 people
```

code becomes impossible to manage.

OOP groups related information.

---

# Advantages of OOP

## 1. Better Structure

Instead of:

```text
Random variables everywhere
```

You get:

```text
Person
├─ name
├─ age
└─ methods
```

---

## 2. Reusability

Write once.

Use many times.

Example:

```python
Person()
Person()
Person()
Person()
```

Same blueprint.

Different objects.

---

## 3. Easier Maintenance

Bug inside:

```python
Person.greet()
```

Fix once.

Every object benefits.

---

## 4. DRY Principle

DRY means:

```text
Don't Repeat Yourself
```

Bad:

```python
print("Hello John")

print("Hello Mike")

print("Hello Sara")
```

Good:

```python
def greet(name):
    print("Hello", name)
```

OOP naturally encourages DRY.

---

# Core OOP Concepts

```text
OOP
│
├─ Classes
├─ Objects
├─ Properties
├─ Methods
├─ Inheritance
├─ Polymorphism
├─ Encapsulation
└─ Abstraction
```

---

# Classes and Objects

## Class

A class is a blueprint.

It describes:

```text
What data objects have
What actions objects perform
```

It does NOT create anything.

---

## Object

An object is a real instance created from a class.

---

## Example

Blueprint:

```text
Car
```

Real Objects:

```text
Toyota
BMW
Audi
Tesla
```

---

## Visualization

```text
CLASS
(Car)

        ↓ creates

OBJECTS

car1
car2
car3
```

---

# Creating a Class

```python
class Car:
    pass
```

Meaning:

```text
Create blueprint called Car.
```

No objects yet.

---

# Creating Objects

```python
class Car:
    pass

car1 = Car()
car2 = Car()
```

Memory:

```text
Car Blueprint
     ↓

car1
car2
```

---

# Objects Are Independent

```python
class Person:
    pass

p1 = Person()
p2 = Person()
```

Even though created from same class:

```text
p1 ≠ p2
```

Each gets separate memory.

---

# __init__() Method

## What is it?

Special constructor method.

Runs automatically when object is created.

---

## Flow

```python
p = Person(...)
```

Python internally:

```text
Allocate memory

↓

Create object

↓

Call __init__()

↓

Return object
```

---

# Example

```python
class Person:

    def __init__(self,name,age):
        self.name = name
        self.age = age
```

Object creation:

```python
p = Person("John",25)
```

Python executes:

```python
Person.__init__(p,"John",25)
```

---

# Why __init__ Exists

Without it:

```python
p = Person()

p.name = "John"
p.age = 25
```

Manual work.

---

With __init__:

```python
p = Person("John",25)
```

Automatic initialization.

---

# Understanding self

Most misunderstood concept.

---

## self Means

```text
"The current object"
```

It is NOT a keyword.

It is simply a variable.

---

Example:

```python
p1 = Person("John",25)
```

Inside:

```python
self → p1
```

---

Another object:

```python
p2 = Person("Mike",30)
```

Inside:

```python
self → p2
```

---

# Visualization

```text
Person("John",25)

self
 ↓
p1
```

Later:

```text
Person("Mike",30)

self
 ↓
p2
```

---

# Why self Is Needed

Suppose:

```python
class Person:

    def greet():
        print(name)
```

Python asks:

```text
Whose name?
p1?
p2?
p3?
```

Impossible.

---

With self:

```python
print(self.name)
```

Python knows exactly which object.

---

# Properties

Properties store object data.

Example:

```python
self.name
self.age
```

---

Visualization:

```text
p1

name → John
age  → 25
```

---

# Instance Properties

Defined using:

```python
self.variable
```

Example:

```python
self.name
self.age
```

Stored separately for each object.

---

Example

```python
p1 = Person("John",25)
p2 = Person("Mike",30)
```

Memory:

```text
p1
name → John
age → 25

p2
name → Mike
age → 30
```

---

# Class Properties

Shared among ALL objects.

Example:

```python
class Person:

    species = "Human"
```

Memory:

```text
Person Class

species → Human
```

Every object uses same value.

---

# Methods

Methods are functions inside classes.

They define behavior.

---

Example

```python
def greet(self):
    print("Hello")
```

---

Visualization

```text
Person

Data:
name
age

Behavior:
greet()
walk()
eat()
```

---

# __str__()

Controls object printing.

Without __str__:

```python
print(p)
```

Output:

```text
<__main__.Person object at ...>
```

---

With __str__:

```python
def __str__(self):
    return f"{self.name}"
```

Output:

```text
John
```

---

# Inheritance

Inheritance means:

```text
Acquire existing features.
```

Child gets parent's capabilities.

---

Visualization

```text
Person
│
├─ name
├─ age
└─ greet()

      ↓

Student
```

Student automatically gets:

```text
name
age
greet()
```

---

# Parent Class

Also called:

```text
Base Class
Super Class
```

---

# Child Class

Also called:

```text
Derived Class
Subclass
```

---

# Creating Inheritance

```python
class Student(Person):
    pass
```

Meaning:

```text
Student IS-A Person
```

---

# Inheritance Flow

```text
Student

↓

Search Student

↓

Not found?

↓

Search Person
```

---

# Overriding __init__

Problem:

Child defines its own constructor.

Parent constructor stops executing.

---

Example

```python
class Student(Person):

    def __init__(self,id):
        self.id=id
```

Now:

```text
name
age
```

never initialize.

---

# Parent Constructor Call

```python
Person.__init__(self,name,age)
```

or

```python
super().__init__(name,age)
```

---

# super()

Means:

```text
"Give me access to parent."
```

---

Example

```python
super().__init__(fname,lname)
```

Equivalent to:

```python
Person.__init__(self,fname,lname)
```

but cleaner.

---

# Method Overriding

Child changes parent's behavior.

---

Parent:

```python
def greet():
    Hello Person
```

Child:

```python
def greet():
    Hello Student
```

Same method name.

Different implementation.

---

# Runtime Decision

```python
stud.greet()
```

Output:

```text
Hello Student
```

because object decides.

---

```python
person.greet()
```

Output:

```text
Hello Person
```

---

# Polymorphism

Meaning:

```text
Many Forms
```

Same interface.

Different behavior.

---

Example

```python
car.move()
boat.move()
plane.move()
```

All:

```text
move()
```

Different outputs.

---

Visualization

```text
move()

↓
Car    → Drive
Boat   → Sail
Plane  → Fly
```

---

# Encapsulation

Encapsulation means:

```text
Protect data
Control access
Hide implementation
```

---

Without Encapsulation

```python
account.balance = -100000
```

Dangerous.

---

With Encapsulation

```python
deposit()
withdraw()
```

Validation happens.

---

# Private Variables

Double underscore:

```python
__age
```

Meaning:

```text
Internal use only.
```

---

Access:

```python
person.__age
```

Error.

---

# Getter

Used to read.

```python
get_age()
```

---

# Setter

Used to modify.

```python
set_age()
```

Allows validation.

---

Example

```python
if age > 0:
    self.__age = age
```

---

# Protected Variables

Single underscore:

```python
_salary
```

Meaning:

```text
Please don't touch directly.
```

Python does NOT enforce it.

Convention only.

---

# Private Methods

Example:

```python
__validate()
```

Used internally.

---

External access:

```python
obj.__validate()
```

Error.

---

# Name Mangling

Python internally changes:

```python
__age
```

into:

```python
_Person__age
```

Purpose:

```text
Prevent accidental access.
```

Not true security.

---

# OOP Mental Model

Think like this:

```text
1. Identify objects.

2. Determine their data.

3. Determine their behaviors.

4. Find common features.

5. Use inheritance.

6. Protect important data.

7. Override behaviors when needed.
```

---

# Entire OOP Hierarchy

```text
OOP
│
├─ Class
│   └─ Blueprint
│
├─ Object
│   └─ Real Instance
│
├─ Properties
│   ├─ Instance Variables
│   └─ Class Variables
│
├─ Methods
│   ├─ Normal Methods
│   └─ Special Methods (__init__, __str__)
│
├─ Inheritance
│   ├─ Parent Class
│   └─ Child Class
│
├─ Method Overriding
│
├─ Polymorphism
│
└─ Encapsulation
    ├─ Private (__)
    ├─ Protected (_)
    ├─ Getters
    └─ Setters
```

---

---

# Abstraction

## What is Abstraction?

Abstraction means:

```text
Showing only the essential features
while hiding unnecessary implementation details.
```

In simple words:

> The user should know **WHAT an object does**, not necessarily **HOW it does it**.

---

## Real-Life Example

### Driving a Car

You know:

```text
• Press accelerator → Car moves
• Press brake → Car stops
• Turn steering → Car changes direction
```

You do NOT need to know:

```text
• How fuel injection works
• How pistons move
• How combustion happens
• How transmission changes gears
```

Those implementation details are hidden.

This is abstraction.

---

# Abstraction vs Encapsulation

Many people confuse these two.

## Encapsulation

Focus:

```text
Protecting data
```

Question answered:

```text
"Who can access this data?"
```

Example:

```python
self.__balance
```

Hide data from direct modification.

---

## Abstraction

Focus:

```text
Hiding complexity
```

Question answered:

```text
"How does this work internally?"
```

Example:

```python
car.start()
```

You use it without knowing the engine mechanism.

---

## Difference

| Encapsulation | Abstraction |
|---|---|
| Protects data | Hides complexity |
| Restricts access | Simplifies usage |
| Uses private/protected members | Uses abstract classes/interfaces |
| Focuses on security | Focuses on design |

---

# Why Abstraction?

Without abstraction:

```text
Users must understand every internal detail.
```

Programs become:

```text
Complex
Difficult to use
Hard to maintain
```

With abstraction:

```text
Simple interfaces

↓

Hidden implementation

↓

Easier usage
```

---

# Abstraction in Python

Python achieves abstraction mainly using:

```text
abc module
```

which stands for:

```text
Abstract Base Classes
```

---

# Abstract Class

An abstract class is a class that:

```text
Cannot be instantiated directly.
```

Its purpose is to define:

```text
Rules that child classes must follow.
```

---

## Visualization

```text
Vehicle
│
├─ move()   ← must exist
│
├───────────────┐
│               │
↓               ↓
Car           Boat
```

Vehicle says:

```text
Every vehicle must know how to move.
```

But Vehicle does NOT define HOW.

Children decide.

---

# Creating Abstract Classes

Import:

```python
from abc import ABC, abstractmethod
```

---

# Example

```python
from abc import ABC, abstractmethod

class Vehicle(ABC):

    @abstractmethod
    def move(self):
        pass
```

---

# Understanding the Code

## Step 1

```python
ABC
```

Means:

```text
This class is abstract.
```

---

## Step 2

```python
@abstractmethod
```

Means:

```text
Every child MUST implement this method.
```

---

# Child Implementation

```python
class Car(Vehicle):

    def move(self):
        print("Drive")


class Boat(Vehicle):

    def move(self):
        print("Sail")
```

---

# Usage

```python
car = Car()
boat = Boat()

car.move()
boat.move()
```

Output:

```text
Drive
Sail
```

---

# What Happens If Child Doesn't Implement?

Example:

```python
class Car(Vehicle):
    pass
```

Then:

```python
car = Car()
```

Error:

```text
TypeError:
Can't instantiate abstract class Car
with abstract method move
```

Reason:

```text
Vehicle demanded move().

Car failed to provide it.
```

---

# Why Can't We Create Abstract Objects?

Example:

```python
vehicle = Vehicle()
```

Error.

Why?

Because:

```text
Vehicle is incomplete.

It only defines requirements.

It does not provide implementation.
```

---

# Real-World Examples

## Payment System

Abstract:

```text
Payment
│
└─ pay()
```

Children:

```text
CreditCardPayment
UPIPayment
PayPalPayment
```

Each pays differently.

---

## Animal System

Abstract:

```text
Animal
│
└─ sound()
```

Children:

```text
Dog → Bark
Cat → Meow
Lion → Roar
```

---

## Employee System

Abstract:

```text
Employee
│
└─ calculate_salary()
```

Children:

```text
PermanentEmployee
ContractEmployee
Intern
```

Each calculates salary differently.

---

# Abstraction Flow

```text
Abstract Class

Defines Rules
       ↓

Child Classes

Provide Implementation
       ↓

Objects Use Implementation
```

---

# Abstraction + Polymorphism

Abstract classes often work together with polymorphism.

Example:

```python
for vehicle in vehicles:
    vehicle.move()
```

Output:

```text
Drive
Sail
Fly
```

Same method:

```text
move()
```

Different implementations.

---

# Mental Model

Think of abstraction as:

```text
A contract.
```

The parent says:

```text
"If you become my child,
you MUST provide these methods."
```

Children agree:

```text
"I'll implement them."
```

---

# OOP Hierarchy (Complete)

```text
OOP
│
├─ Class
│
├─ Object
│
├─ Properties
│
├─ Methods
│
├─ Inheritance
│
├─ Method Overriding
│
├─ Polymorphism
│
├─ Encapsulation
│
└─ Abstraction
    │
    ├─ Abstract Classes (ABC)
    ├─ @abstractmethod
    ├─ Cannot Instantiate
    └─ Child Must Implement
```

---

# Encapsulation vs Abstraction

```text
Encapsulation:
"I hide and protect my data."

Abstraction:
"I hide my complexity."
```

---

# 30-Second Interview Summary

```text
Abstraction means exposing only the necessary features of an object while hiding implementation details.

Python implements abstraction using the abc module.

Abstract classes cannot be instantiated.

Methods marked with @abstractmethod act as contracts that child classes must implement.

Abstraction reduces complexity, improves maintainability, and provides a clean interface to users.
```

---
