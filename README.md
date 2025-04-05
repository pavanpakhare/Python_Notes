# Python Basic Tutorial

This tutorial will introduce you to the fundamentals of Python programming. Python is a versatile, easy-to-learn language that's great for beginners.

## Table of Contents
1. [Installing Python](#installing-python)
2. [Your First Python Program](#your-first-python-program)
3. [Variables and Data Types](#variables-and-data-types)
4. [Basic Operators](#basic-operators)
5. [Input and Output](#input-and-output)
6. [Conditional Statements](#conditional-statements)
7. [Loops](#loops)
8. [Functions](#functions)
9. [Lists](#lists)
10. [Dictionaries](#dictionaries)
11. [List Comprehensions](#list-comprehensions)
12. [Lambda Functions](#lambda-functions)
13. [Map, Filter, and Reduce](#map-filter-and-reduce)
14. [Error Handling](#error-handling)
15. [Working with Files](#working-with-files)
16. [Object-Oriented Programming](#object-oriented-programming)
17. [Modules and Packages](#modules-and-packages)
18. [Working with Dates and Times](#working-with-dates-and-times)
19. [Regular Expressions](#regular-expressions)
20. [Virtual Environments](#virtual-environments)
1. [Decorators](#decorators)  
2. [Generators & Yield](#generators--yield)  
3. [Context Managers (with Statement)](#context-managers-with-statement)  
4. [Metaclasses](#metaclasses)  
5. [Concurrency (Threading & Multiprocessing)](#concurrency-threading--multiprocessing)  
6. [Asynchronous Programming (Async/Await)](#asynchronous-programming-asyncawait)  
7. [Memory Management & Garbage Collection](#memory-management--garbage-collection)  
8. [Descriptors & Properties](#descriptors--properties)  
9. [Type Hints & Static Typing (MyPy)](#type-hints--static-typing-mypy)  
10. [Advanced Data Structures (NamedTuple, Dataclass, Enum)](#advanced-data-structures-namedtuple-dataclass-enum)  


## Installing Python

1. Download Python from [python.org](https://www.python.org/downloads/)
2. Run the installer (check "Add Python to PATH" on Windows)
3. Verify installation by opening a terminal/command prompt and typing:
   ```bash
   python --version
   ```

## Your First Python Program

Create a file named `hello.py` with this content:

```python
print("Hello, World!")
```

Run it from your terminal:
```bash
python hello.py
```

## Variables and Data Types

```python
# Integer
age = 25

# Float
price = 19.99

# String
name = "Alice"

# Boolean
is_student = True

# Print variables
print("Name:", name)
print("Age:", age)
```

## Basic Operators

```python
# Arithmetic
a = 10 + 5    # Addition
b = 10 - 5    # Subtraction
c = 10 * 5    # Multiplication
d = 10 / 3    # Division (float)
e = 10 // 3   # Division (integer)
f = 10 % 3    # Modulus
g = 10 ** 2   # Exponentiation

# Comparison
x = 10
print(x > 5)  # True
print(x == 10) # True
print(x != 5) # True

# Logical
print(True and False)  # False
print(True or False)   # True
print(not True)        # False
```

## Input and Output

```python
# Getting user input
name = input("Enter your name: ")
age = int(input("Enter your age: "))  # Convert string to integer

# Formatted output
print(f"Hello {name}, you are {age} years old.")
print("Next year you'll be", age + 1)
```

## Conditional Statements

```python
# If-elif-else
temperature = float(input("Enter temperature: "))

if temperature > 30:
    print("It's hot outside!")
elif 20 <= temperature <= 30:
    print("Nice weather!")
else:
    print("It's cold outside!")
```

## Loops

```python
# For loop
for i in range(5):  # 0 to 4
    print(i)

# While loop
count = 0
while count < 5:
    print(count)
    count += 1  # Same as count = count + 1

# Loop control
for num in range(10):
    if num == 3:
        continue  # Skip this iteration
    if num == 7:
        break     # Exit loop
    print(num)
```

## Functions

```python
# Define a function
def greet(name):
    return f"Hello, {name}!"

# Call the function
message = greet("Alice")
print(message)

# Function with default parameter
def power(base, exponent=2):
    return base ** exponent

print(power(3))    # 9 (3^2)
print(power(3, 3)) # 27 (3^3)
```

## Lists

```python
# Create a list
fruits = ["apple", "banana", "cherry"]

# Access elements
print(fruits[0])  # apple
print(fruits[-1]) # cherry (last element)

# Modify list
fruits.append("orange")  # Add item
fruits[1] = "blueberry"  # Change item
del fruits[0]            # Remove item

# List operations
numbers = [1, 2, 3] + [4, 5]  # Concatenation
print(len(numbers))            # Length

# List slicing
print(numbers[1:3])  # [2, 3]
print(numbers[:2])   # [1, 2]
print(numbers[2:])   # [3, 4, 5]
```

## Dictionaries

```python
# Create a dictionary
person = {
    "name": "Alice",
    "age": 25,
    "is_student": True
}

# Access values
print(person["name"])       # Alice
print(person.get("age"))    # 25

# Add/modify items
person["email"] = "alice@example.com"
person["age"] = 26

# Dictionary methods
print(person.keys())    # dict_keys(['name', 'age', 'is_student', 'email'])
print(person.values())  # dict_values(['Alice', 26, True, 'alice@example.com'])
```

# intermedeat

## List Comprehensions

A concise way to create lists:

```python
# Basic list comprehension
squares = [x**2 for x in range(10)]
print(squares)  # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# With condition
even_squares = [x**2 for x in range(10) if x % 2 == 0]
print(even_squares)  # [0, 4, 16, 36, 64]

# Nested list comprehension
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flattened = [num for row in matrix for num in row]
print(flattened)  # [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

## Lambda Functions

Anonymous functions defined with the `lambda` keyword:

```python
# Simple lambda function
add = lambda x, y: x + y
print(add(5, 3))  # 8

# Using lambda with sorted
names = ['Alice', 'Bob', 'Charlie', 'David']
sorted_names = sorted(names, key=lambda x: len(x))
print(sorted_names)  # ['Bob', 'Alice', 'David', 'Charlie']
```

## Map, Filter, and Reduce

Functional programming tools:

```python
# Map - applies function to all items
numbers = [1, 2, 3, 4]
squared = list(map(lambda x: x**2, numbers))
print(squared)  # [1, 4, 9, 16]

# Filter - filters items based on condition
evens = list(filter(lambda x: x % 2 == 0, numbers))
print(evens)  # [2, 4]

# Reduce - applies function cumulatively
from functools import reduce
product = reduce(lambda x, y: x * y, numbers)
print(product)  # 24 (1*2*3*4)
```

## Error Handling

Using try-except blocks:

```python
try:
    # Code that might raise an exception
    num = int(input("Enter a number: "))
    result = 10 / num
    print("Result:", result)
except ValueError:
    print("That's not a valid number!")
except ZeroDivisionError:
    print("You can't divide by zero!")
except Exception as e:
    print("An error occurred:", e)
else:
    print("No exceptions occurred!")
finally:
    print("This always runs, with or without exceptions")
```

## Working with Files

Reading and writing files:

```python
# Writing to a file
with open('example.txt', 'w') as file:
    file.write("Hello, World!\n")
    file.write("This is a second line\n")

# Reading from a file
with open('example.txt', 'r') as file:
    content = file.read()
    print(content)

# Reading line by line
with open('example.txt', 'r') as file:
    for line in file:
        print(line.strip())  # strip removes newline characters
```

## Object-Oriented Programming

Classes and objects:

```python
class Dog:
    # Class attribute
    species = "Canis familiaris"

    # Initializer / Instance attributes
    def __init__(self, name, age):
        self.name = name
        self.age = age

    # Instance method
    def description(self):
        return f"{self.name} is {self.age} years old"

    # Another instance method
    def speak(self, sound):
        return f"{self.name} says {sound}"

# Create instances
dog1 = Dog("Buddy", 5)
dog2 = Dog("Molly", 3)

# Access attributes and methods
print(dog1.description())  # Buddy is 5 years old
print(dog2.speak("Woof"))  # Molly says Woof

# Inheritance
class Bulldog(Dog):
    def speak(self, sound="Woof Woof"):
        return super().speak(sound)

bulldog = Bulldog("Max", 2)
print(bulldog.speak())  # Max says Woof Woof
```

## Modules and Packages

Organizing and reusing code:

```python
# mymodule.py
def greet(name):
    return f"Hello, {name}!"

def add(a, b):
    return a + b

# main.py
import mymodule

print(mymodule.greet("Alice"))  # Hello, Alice!
print(mymodule.add(2, 3))      # 5

# Alternative imports
from mymodule import greet
print(greet("Bob"))  # Hello, Bob!

# Import with alias
import mymodule as mm
print(mm.add(5, 7))  # 12
```

## Working with Dates and Times

```python
from datetime import datetime, timedelta

# Current date and time
now = datetime.now()
print(now)  # 2023-04-15 14:30:45.123456

# Formatting dates
formatted = now.strftime("%Y-%m-%d %H:%M:%S")
print(formatted)  # 2023-04-15 14:30:45

# Date arithmetic
one_week = timedelta(weeks=1)
next_week = now + one_week
print(next_week)

# Parsing dates
date_str = "2023-04-15"
parsed_date = datetime.strptime(date_str, "%Y-%m-%d")
print(parsed_date.date())  # 2023-04-15
```

## Regular Expressions

Pattern matching with the `re` module:

```python
import re

# Search for pattern
text = "The rain in Spain"
match = re.search(r"\bS\w+", text)
if match:
    print(match.group())  # Spain

# Find all matches
words = re.findall(r"\b\w{4}\b", text)  # 4-letter words
print(words)  # ['rain', 'Spain']

# Substitution
new_text = re.sub(r"\s", "-", text)  # Replace spaces with -
print(new_text)  # The-rain-in-Spain

# Email validation pattern
email_pattern = r"^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$"
email = "user@example.com"
if re.match(email_pattern, email):
    print("Valid email")
else:
    print("Invalid email")
```

## Virtual Environments

Creating isolated Python environments:

```bash
# Create a virtual environment
python -m venv myenv

# Activate it (Windows)
myenv\Scripts\activate

# Activate it (macOS/Linux)
source myenv/bin/activate

# Install packages in the environment
pip install requests pandas

# Deactivate the environment
deactivate

# Requirements file
pip freeze > requirements.txt
pip install -r requirements.txt
```

# Advance

## **Decorators**  
Decorators allow modifying the behavior of functions or classes.  

### **Basic Decorator**
```python
def my_decorator(func):
    def wrapper():
        print("Before function call")
        func()
        print("After function call")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()
```
**Output:**  
```
Before function call  
Hello!  
After function call  
```

### **Decorator with Arguments**
```python
def repeat(num_times):
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(num_times):
                func(*args, **kwargs)
        return wrapper
    return decorator

@repeat(num_times=3)
def greet(name):
    print(f"Hello, {name}!")

greet("Alice")
```
**Output:**  
```
Hello, Alice!  
Hello, Alice!  
Hello, Alice!  
```

---

## **Generators & Yield**  
Generators allow lazy evaluation and memory-efficient iteration.  

### **Basic Generator**
```python
def count_up_to(max):
    count = 1
    while count <= max:
        yield count
        count += 1

counter = count_up_to(5)
for num in counter:
    print(num)
```
**Output:**  
```
1  
2  
3  
4  
5  
```

### **Using `yield from` (Generator Delegation)**
```python
def generator1():
    yield 1
    yield 2

def generator2():
    yield from generator1()
    yield 3

for num in generator2():
    print(num)
```
**Output:**  
```
1  
2  
3  
```

---

## **Context Managers (`with` Statement)**  
Context managers handle resource management (e.g., files, locks).  

### **Custom Context Manager (Class-based)**
```python
class ManagedFile:
    def __init__(self, filename):
        self.filename = filename

    def __enter__(self):
        self.file = open(self.filename, 'w')
        return self.file

    def __exit__(self, exc_type, exc_val, exc_tb):
        if self.file:
            self.file.close()

with ManagedFile('hello.txt') as f:
    f.write("Hello, World!")
```

### **Using `contextlib` (Function-based)**
```python
from contextlib import contextmanager

@contextmanager
def managed_file(filename):
    try:
        f = open(filename, 'w')
        yield f
    finally:
        f.close()

with managed_file('hello.txt') as f:
    f.write("Hello again!")
```

---

## **Metaclasses**  
Metaclasses control class creation (advanced OOP).  

### **Basic Metaclass**
```python
class Meta(type):
    def __new__(cls, name, bases, dct):
        dct['version'] = 1.0
        return super().__new__(cls, name, bases, dct)

class MyClass(metaclass=Meta):
    pass

print(MyClass.version)  # Output: 1.0
```

---

## **Concurrency (Threading & Multiprocessing)**  
### **Threading (I/O-bound tasks)**
```python
import threading

def print_numbers():
    for i in range(5):
        print(i)

def print_letters():
    for letter in 'ABCDE':
        print(letter)

t1 = threading.Thread(target=print_numbers)
t2 = threading.Thread(target=print_letters)

t1.start()
t2.start()

t1.join()
t2.join()
```

### **Multiprocessing (CPU-bound tasks)**
```python
import multiprocessing

def square(n):
    return n * n

if __name__ == '__main__':
    with multiprocessing.Pool(processes=4) as pool:
        results = pool.map(square, range(10))
    print(results)  # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

---

## **Asynchronous Programming (Async/Await)**  
```python
import asyncio

async def fetch_data():
    print("Fetching data...")
    await asyncio.sleep(2)
    print("Data fetched!")
    return {"data": 123}

async def main():
    task = asyncio.create_task(fetch_data())
    print("Doing other work...")
    await task
    print(task.result())  # {'data': 123}

asyncio.run(main())
```

---

## **Memory Management & Garbage Collection**  
```python
import gc

# Force garbage collection
gc.collect()

# Check object references
import sys
a = []
print(sys.getrefcount(a))  # Number of references
```

---

## **Descriptors & Properties**  
```python
class Temperature:
    def __init__(self, celsius):
        self._celsius = celsius

    @property
    def celsius(self):
        return self._celsius

    @celsius.setter
    def celsius(self, value):
        if value < -273.15:
            raise ValueError("Too cold!")
        self._celsius = value

temp = Temperature(25)
print(temp.celsius)  # 25
temp.celsius = 30    # Works
temp.celsius = -300  # Raises ValueError
```

---

## **Type Hints & Static Typing (MyPy)**  
```python
from typing import List, Dict, Optional

def greet(name: str) -> str:
    return f"Hello, {name}!"

def process_data(data: List[int]) -> Dict[str, int]:
    return {"length": len(data), "sum": sum(data)}

result: Optional[int] = None  # Can be int or None
```

---

## **Advanced Data Structures**  
### **NamedTuple** (Immutable, Lightweight)  
```python
from typing import NamedTuple

class Point(NamedTuple):
    x: int
    y: int

p = Point(10, 20)
print(p.x, p.y)  # 10 20
```

### **Dataclass** (Auto-generated `__init__`, `__repr__`)  
```python
from dataclasses import dataclass

@dataclass
class Person:
    name: str
    age: int

p = Person("Alice", 30)
print(p)  # Person(name='Alice', age=30)
```

### **Enum** (Type-safe Constants)  
```python
from enum import Enum, auto

class Color(Enum):
    RED = auto()
    GREEN = auto()
    BLUE = auto()

print(Color.RED)  # Color.RED
```


