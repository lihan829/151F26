--- #1
theme: seriph
background: '#fff8e6'
themeConfig:
  primary: '#2c3ad3'
title: LCD151 Week 2
info: false
class: text-center
fonts:
  sans: Lexend
  serif: Roboto Slab
  mono: Fira Code
---

# Variables

### LCD151 Week 2
### Instructor: Han Li
<h3>{{ new Date().toLocaleDateString('en-US', {
  year: 'numeric',
  month: 'long',
  day: 'numeric'
}) }}</h3>


---

# Today's Goals

## 🐍 Python Basics

- Variables & literals
- `print()` and `input()`
- Data types
---

# Python 

- A high-level, general-purpose **interpreted** programming language
- Emphasizes readability — code looks close to plain English
- Widely used in NLP, data science, web development, and scripting
- The first function: `print()`


<br>

``` python
>>> print("Hello, World") # print function takes one argument and display whatever you pass
>>> "Hello, World!"
```
<br>

``` python
>>> print("Hello, LCD151!") # You are calling the print() function and pass one argument 
>>> "Hello, LCD151!"
```


---

# Variables & Literals

 But what if we don't just want to print the results of the arithmetic calculations but use those results later in our code? 

- A **variable** is a **name** bound to a value which makes it possible to reference values by that name in the future
- A **literal** is a specific **value** written directly in the code.
  
---

# Variables 

## Compare the follows

```
# a very simple calculation
print(5 + 3)
```

Instead of directly printing the values out, we can stores them as variables

```
# and now the same with variables
x = 5        # assign value 5 to the variable with name x
y = 3        # assign value 3 to the variable with name y
print(x)     # retrieve the value of variable x and print it
print(y)     # retrieve the value of variable y and print it
print(x + y) # add the values of variables x and y (5 and 3) and print the sum
```

The lines `x=5` and `y=3` are called assignment statements.

---

# Variables 

## We can assign the values of variables to variables

```
a = 5         # assign value 5 to the variable with name a 
b = 3         # assign value 3 to the variable with name b 
x = a         # assign name x to what name a refers to, i.e. 5
y = b         # assign name y to what name b refers to, i.e. 3
print(a + b)  # add a and b (same as 5 + 3)
print(a == x) # check if a and x have the same values
```
- Note that in the above, variables a and b still contain their orginal values (5 and 3, respectively).  
- It is not the case that the line `x = a` moves the content from `a` to `x`, and `a` loses its content.  
- Instead, the value of `a` is copied to `x`.

---

# Variables


Variables can hold any sort of data.

```python
name = "Auggie"     # string literal
age = 5             # integer literal
weight = 10.7       # float literal (decimals)
is_vax = True       # boolean literal (true or false)
```


---
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

# Practice

1. Can you predict the type? Verify from your IDLE

```python
type(10 / 2)       
type(10 // 2)      
type(1 + 1 == 2) # two equal signs   
type(1 + 1 = 2) # one equal sign
type("1" + "1")    
type(1 + 1.0)      
```
---

# Exercise 2

Create a profile for patient.

Create variables `name`, `age`, `temperture`, `checked_today` (true or false)
in our shared google notebook.




---

# `Input()`

A program also needs to receive input. The input could be a file, the current system time, or some value entered by the user. The last option is the simplest, as it can be handled by a single Python command: input().
 
Note: Whenever you use input(), you should immediately store it in a variable, otherwise what the user just entered gets lost. Let's look at a first example.

```python
age = input("Enter your age: ")
print(age)
```
Check what type is `age`?
---

# `Input()`

All values passed by `input()` will have a type of being a string. Please try this code:
```python
num1 = input("input first number")
num2 = input("input second number")
sum = num1 + num2 
print(sum)
```
what is the problem?

<v-click>

> [!TIP]
> Use `int()`, `float()`, or `str()` to convert a value from one data type to another.
```python
num1 = int(input("input first number"))
num2 = int(input("input second number"))
sum = num1 + num2 
print(sum)
```

</v-click>