# Python Intermediate Tutorial

This tutorial builds on basic Python knowledge and covers more advanced concepts that will help you write more efficient and organized code.

## Table of Contents
1. [List Comprehensions](#list-comprehensions)
2. [Lambda Functions](#lambda-functions)
3. [Map, Filter, and Reduce](#map-filter-and-reduce)
4. [Error Handling](#error-handling)
5. [Working with Files](#working-with-files)
6. [Object-Oriented Programming](#object-oriented-programming)
7. [Modules and Packages](#modules-and-packages)
8. [Working with Dates and Times](#working-with-dates-and-times)
9. [Regular Expressions](#regular-expressions)
10. [Virtual Environments](#virtual-environments)

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
