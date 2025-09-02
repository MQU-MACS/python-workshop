---
title: "Python Workshop (Beginner)"
sub_title: "MACS × MQCyberSec"
date: 18 Sep. 2025
location: 102, 4 Research Pk. Dr.
theme:
  name: gruvbox-dark
            
---


What is Python?
===============


- High-level dynamic general-purpose language
- Created by Guido van Rossum
- History:
  - Python 1 (1991)
  - Python 2 (2000)
  - Python 3 (2008, latest: 3.13)
- Named after Monty Python

<!-- end_slide -->

Why Python?
===========

- Simple syntax, easy to pick up
- Very convenient for small programs and quick scripts

```python
def fizzbuzz(n: int) -> str | int:
    output = ""
    if n % 3 == 0:
        output += "Fizz"
    if n % 5 == 0:
        output += "Buzz"

    if output == "":
        return n
    return output
```

<!-- pause -->

- *"It is also a handy desk calculator."* –docs.python.org

```python
>>> 32 * 62
1984
```

<!-- Sources:
- https://docs.python.org/3/tutorial/appetite.html -->

<!-- end_slide -->

The Zen of Python
===========

```
>>> import this
The Zen of Python, by Tim Peters

Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!
```

<!-- end_slide -->

Why Python?
===========

### Extensive Standard Library

| import ...      |                                      |
| --------------- | ------------------------------------ |
| argparse        | Command-line arguments               |
| requests        | Simple HTTP servers                  |
| pathlib         | File/folder path operations          |
| json            | Load and save JSON                   |
| asyncio         | Do many I/O-bound things at once     |
| multiprocessing | Do many CPU-bound things at once     |
| dataclasses     | Quick scaffolding for simple classes |
| sqlite3         | Simple relational databases          |

[...and much more!](https://docs.python.org/3/library/index.html)

<!-- Sources:
- https://docs.python.org/3/library/index.html -->
<!-- end_slide -->

Why Python?
===========

### Massive Third-Party Ecosystem

|                      | uv add ...             |
| -------------------- | ---------------------- |
| Web Development      | django, FastAPI, flask |
| Game Development     | pygame, pyglet, bevy   |
| Scientific Computing | numpy, pandas, scipy   |
| Machine Learning     | tensorflow, pytorch    |
| GUIs                 | PySide6, slint, kivy   |
| Cybersecurity Tools  | scapy, nmap            |

~668,000 projects available on [PyPi](https://pypi.org/)

<!-- Sources:
 - https://pypi.org/
 - https://www.python.org/about/apps/
 - https://www.geeksforgeeks.org/python/python-for-cybersecurity/ -->
<!-- end_slide -->

Getting Started
===============

## Python + uv

- Installs and manages different Python versions
- Manages project structure and dependencies
- [Install uv](https://docs.astral.sh/uv/)
- **Install Python**: `uv python install`

## VS Code + Python extension

[Install](https://code.visualstudio.com/)

### Extensions

Run these in the VS Code run box (`Ctrl`/`⌘` + `P`) to install:

- Python Language Support:   `ext install ms-python.python`
- (optional) Ruff:           `ext install charliermarsh.ruff`

<!-- end_slide -->

Getting Started
===============

## Setting up

- Create a new folder somewhere to put your Python project, and open VS Code to that folder.
- Open the terminal (`Ctrl`/`⌘` + `~`) and run:
  - `uv init .`

- Open the newly created `main.py` file.

## Commands to know

- `uv run main.py`    Execute your Python code
- `uv venv`           Create a virtual environment to store dependencies
- `uv add ...`        Install packages to your project

<!-- end_slide -->

<!-- jump_to_middle -->
[editor time]
=============

<!-- end_slide -->

Variables
===

```python
foo = 42
bar = "mars bar"
eggs = 36.60
spam = True
```

<!-- end_slide -->

Operations on Numbers
===

```python
1 + 1    # 2
3 - 5    # -2
80 * 20  # 1600

# Float division vs. integer division
5 / 3    # 1.666…
5 // 3   # 1

5 % 3  # 2

# Also: >, >=, ==, <=, <, !=
60 <= 100  # False
8 == 8     # True
```

<!-- end_slide -->

Operations on Booleans
===

```python
True and False  # False
True or False   # True

not True  # False
```

<!-- end_slide -->

Lists
===

Collections of values of potentially different types.

```python
names = ["Alice", "Bob", "Carol", "David"]
stats = [3, 3.5, 0, 5.5, 100, 4.309]

# Indexing
stats[2]  # 0

# Negative indexing (from the end of the list)
stats[-2]  # 100

# Slicing (grabbing subsets)
names[1:3]  # ["Bob", "Carol", "David"]

names.append("Mallory")
# names == ["Alice", "Bob", "Carol", "David", "Mallory"]

names.remove("Bob")
# names == ["Alice", "Carol", "David", "Mallory"]
```

<!-- end_slide -->

Operations on Strings
===

```python
"hello " + "world!"   # "hello world!"
"hi" * 5              # "hihihihihi"
"hello world!"[4:8]   # "o wo"

# Compare string order
"HAL" == "IBM"  # False
"HAL" < "IBM"   # True

# A string can behave like a list of characters
"hello world!"[-1]   # "!"
"hello world!"[4:8]  # "o wo"
```

<!-- end_slide -->

F-Strings
===

Interpolate variables inside strings.

```python
name = "Inigo Montoya"
victim = "my father"

print(f"My name is {name}. You killed {victim}. Prepare to die.")
# My name is Inigo Montoya. You killed my father. Prepare to die.
```

<!-- end_slide -->

Sets
===

Collections of *unique* values of the same type.

```python
favourite_numbers = {1, 2, 3, 7, 9, 10}

# Converting a list to a set filters out duplicates
boring_numbers = set([4, 5, 5, 6, 6, 8])
# boring_numbers == {4, 5, 6, 8}

11 in favourite_numbers  # False
5 in boring_numbers      # True

merged = favourite_numbers | boring_numbers
# merged == {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

```

<!-- end_slide -->

Dictionaries
===

Key-value pairs, equivalent to `HashMap`s in Java.

```python
en_to_fr = {
    "red": "rouge",
    "green": "vert",
    "yellow": "jaune"
}

en_to_fr["red"]  # "rouge"

en_to_fr["blue"] = "azure"
# en_to_fr == {..., "blue": "azure"}
```

<!-- end_slide -->

`if`/`elif`/`else` statements
===

```python
name = "Mallory"
admins = {"Alice", "Dave"}

if name == "Mallory":
    print("Intruder spotted")
elif name in admins:
    print(f"Hello, {name}! You are an admin.")
else:
    print(f"Hello, {name}!")
```

<!-- end_slide -->

`while` loops
===

Traditional pre-check iteration.

```python
i = 0

while i < 3:
    print(i)   # 0, 1, 2
    i += 1

while True:
    print("Infinite loop!")
```


<!-- end_slide -->


`for` loops
===

Works on *iterable* objects.

```python
for i in range(100):
    print(i)  # 0, 1, 2, ..., 99 

for name in ["Alice", "Bob", "Carol", "David"]:
    print(f"Hello, {name}!")
    # Hello, Alice!
    # Hello, Bob!
    # ...

for index, name in enumerate(["Alice", "Bob", "Carol", "David"]):
    print(f"{index}: Hello, {name}!")
    # 0: Hello, Alice!
    # 1: Hello, Bob!
    # ...

for char in "MACS":
    print(char)  # "M", "A", "C", "S"
```

<!-- end_slide -->

Functions
===

```python
admins = {"Alice", "Dave"}

def greet(name):
    if name == "Mallory":
        return "Intruder spotted!"
    elif name in admins:
        return f"Hello, {name}! You are an admin."
    else:
        return f"Hello, {name}!"

greet("Dave")     # Hello, Dave! You are an admin.
greet("Mallory")  # Intruder spotted!
```

<!-- end_slide -->

Type annotations
===

- Optional, but recommended for medium to large codebases.
- Python itself won't do any checks on types, only when it tries a nonsensical
  operation will it raise an error.
  - External tools, such as `mypy`, can do type checking before execution.

```python
def greet(name: str) -> str:
    if name == "Mallory":
        return "Intruder spotted!"
    elif name in admins:
        return f"Hello, {name}! You are an admin."
    else:
        return f"Hello, {name}!"

greet("Mallory")  # Intruder spotted!
greet(3)          # Hello, 3!
#     ^ mypy can catch this error
```

<!-- end_slide -->

Optional function arguments
===

```python
def greet(name: str, salutation: str = "") -> str:
    if name in admins:
        return f"Hello, {salutation}{name}! You are an admin."
    else:
        return f"Hello, {salutation}{name}!"

greet("Mallory")                   # Hello, Mallory!
greet("Dave", "Mr. ")             # Hello, Mr. Dave! You are an admin.
greet("Alice", salutation="Ms. ")  # Hello, Ms. Alice! You are an admin.
```

<!-- end_slide -->

Keyword-only arguments
===

```python
def greet(name: str, *, salutation: str = "") -> str:
    if name in admins:
        return f"Hello, {salutation}{name}! You are an admin."
    else:
        return f"Hello, {salutation}{name}!"

greet("Mallory")                   # Hello, Mallory!
greet("Dave", "Mr. ")              # [ error ]
greet("Alice", salutation="Ms. ")  # Hello, Ms. Alice! You are an admin.
```