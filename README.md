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




