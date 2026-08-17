--- #1
theme: seriph
background: 
title: Python Basics & Git
info: false
class: text-center
fonts:
  sans: Lexend
  serif: Roboto Slab
  mono: Fira Code
---

# <span class="blue">Python</span> <span class="dark">Basics</span> <span class="orange">& Git</span>

<style>
.blue {
  color: #006BB6;
}

.dark {
  color: #222222cd;
}

.orange {
  color: #F58426;
}
</style>

<span class="dark">LCD151: Methods in Computational Linguistics I</span>

<span class="dark">Instructor: Han Li</span>




---
layout: two-cols-header

---
 
# Today's Goals

::left::

## 🐍 Python Basics

- Variables & literals
- Data types
- Operators & expressions
- Control flow
- Functions

::right::

## 🔧 Git

- Why version control?
- Core concepts
- Everyday commands
- GitHub workflow
- Best practices

---
layout: center
---
   
# **Python Basics**

---

# First Python 

- A high-level, general-purpose **interpreted** programming language
- Emphasizes readability — code looks close to plain English
- Widely used in NLP, data science, web development, and scripting
- No compilation step: you run `.py` files directly
- But now we will use IDLE

<br>

``` python
>>> print("Hello, World") # print function takes one argument and display whatever you pass
>>> "Hello, World!"
```
<br>

``` python
>>> print("Hello, LCD151!") # You are using the print() function
>>> "Hello, LCD151!"
```


---

# Variables & Literals
- A **variable** is a **name** bound to a value.
- A **literal** is a specific **value** written directly in the code.
  
```python
name = "Auggie"     # string literal
age = "5"           # integer literal
weight = 10.7       # float literal
is_vax = True       # boolean literal
```

---

# Naming Variables


- Case-sensitive (`Name` ≠ `name`)
```python
name = "Auggie"    # string literal
Name = "Bazzie"    # another string literal
print(name == Name)
# False
```

- Must start with a letter or underscore
- Cannot use Python reserved words, such as `if`, `for`, or `class`

```python
# You will get SyntaxError if you do these
151enroll = 32
class = "LCD151"
```
- Use `snake_case` by convention


---

# Basic Data Types

| Type | Example | Description |
|---|---|---|
| `int` | `42` | whole numbers |
| `float` | `3.14` | decimal numbers |
| `str` | `"text"` | sequences of characters |
| `bool` | `True` / `False` | logical values |
| `None` | `None` | NoneType |

<br>
---

# Checking Data Types

Python’s built-in `type()` function tells us the data type of a value.

```python
type(42)          # <class 'int'>
type(3.14)        # <class 'float'>
type("42")        # <class 'str'>
type(True)        # <class 'bool'>
type(None)        # <class 'NoneType'
```
---
 
# Operators & Expressions

```python
# Arithmetic
3 + 2    # 5
3 - 2    # 1
3 * 2    # 6
3 / 2    # 1.5   (true division)
3 // 2   # 1     (floor division)
3 % 2    # 1     (modulo)
3 ** 2   # 9     (exponent)

# Comparison
3 == 2   # False
3 != 2   # True
3 > 2    # True

# Logical
True and False   # False
True or False    # True
not True         # False
```
---

# Practice

1. Can you predict the type? Verify from your IDLE

```python
type(10 / 2)       
type(10 // 2)      
type(1 + 1 == 2)   
type("1" + "1")    
type(1 + 1.0)      
```
<br>

2. Use the built-in function `input()` to ask the user for information

```python
age = input("Enter your age: ")
type(age)  
```
What type is `age`?
<br>

> [!TIP]
> Use `int()`, `float()`, or `str()` to convert a value from one data type to another.
>
> ```python
> age = int(input("Enter your age: "))
> ```