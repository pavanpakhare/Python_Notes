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
11 [List Comprehensions](#list-comprehensions)
12. [Lambda Functions](#lambda-functions)
13. [Map, Filter, and Reduce](#map-filter-and-reduce)
14. [Error Handling](#error-handling)
15. [Working with Files](#working-with-files)
16. [Object-Oriented Programming](#object-oriented-programming)
17. [Modules and Packages](#modules-and-packages)
18. [Working with Dates and Times](#working-with-dates-and-times)
19. [Regular Expressions](#regular-expressions)
20. [Virtual Environments](#virtual-environments)

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






