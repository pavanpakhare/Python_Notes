# **Advanced Python Tutorial**  


This tutorial covers advanced Python concepts that will help you write **efficient, scalable, and professional** Python code.  

---

## **Table of Contents**  
1. [**Decorators**](#decorators)  
2. [**Generators & Yield**](#generators--yield)  
3. [**Context Managers (with Statement)**](#context-managers-with-statement)  
4. [**Metaclasses**](#metaclasses)  
5. [**Concurrency (Threading & Multiprocessing)**](#concurrency-threading--multiprocessing)  
6. [**Asynchronous Programming (Async/Await)**](#asynchronous-programming-asyncawait)  
7. [**Memory Management & Garbage Collection**](#memory-management--garbage-collection)  
8. [**Descriptors & Properties**](#descriptors--properties)  
9. [**Type Hints & Static Typing (MyPy)**](#type-hints--static-typing-mypy)  
10. [**Advanced Data Structures (NamedTuple, Dataclass, Enum)**](#advanced-data-structures-namedtuple-dataclass-enum)  

---

## **1. Decorators**  
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

## **2. Generators & Yield**  
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

## **3. Context Managers (`with` Statement)**  
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

## **4. Metaclasses**  
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

## **5. Concurrency (Threading & Multiprocessing)**  
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

## **6. Asynchronous Programming (Async/Await)**  
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

## **7. Memory Management & Garbage Collection**  
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

## **8. Descriptors & Properties**  
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

## **9. Type Hints & Static Typing (MyPy)**  
```python
from typing import List, Dict, Optional

def greet(name: str) -> str:
    return f"Hello, {name}!"

def process_data(data: List[int]) -> Dict[str, int]:
    return {"length": len(data), "sum": sum(data)}

result: Optional[int] = None  # Can be int or None
```

---

## **10. Advanced Data Structures**  
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

