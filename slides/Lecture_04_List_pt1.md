---
theme: seriph
background: '#fff8e6'
title: Lists
info: |
  Computational Linguistics
  Adapted from course materials by Jiwon Yun (Fall 2025)
fonts:
  sans: Lexend
  serif: Roboto Slab
  mono: Fira Code

---

# List

### LCD151 Lecture 
### Instructor: Han Li
<h3>{{ new Date().toLocaleDateString('en-US', {
  year: 'numeric',
  month: 'long',
  day: 'numeric'
}) }}</h3>

---

# Today's Goal

## Review (Questions from the previous Lab)
- `f-string` and `print`
- String basics

## List
- Lists as sequences of objects
- List operations and methods

---

# Q1: when to use `f-string` and `print()`

We know there are several ways to print 
```python
# 1. Print a string literal directly
print("hello world")

# 2. Print multiple variables
word1 = "hello"
word2 = "world"
print(word1, word2)

# 3. Print a variable and a literal
print(1, word1, 2,"world")

# 4. Use "+"
print(word1 + " " + word2)

# 5. Use an f-string
print(f"The first word is {word1}\nThe second word is {word2}")
```

---

# Q1: when to use `f-string` and `print()`

It is often up to you which method you use. However:

- Use commas for simple printing (comma automatically adds a space between the items)
- Use an f-string when you want to combine multiple variables and text in a clear, flexible format.
- Be careful with `+`: it does not add spaces automatically
- Most cases f-string provides the cleanest choice, and comma provides the simplest choice
```python
name = "Maya"
score = 95

print(f"{name} received a score of {score}.")
print(name, score) # Maya 95
```

---

# Q2: What is the point of variable swapping 

Variable swapping means exchanging the values stored in two variables.

```python
word1 = "dog"
word2 = "cat"

temp = word1    # Save "dog" as temp
word1 = word2   # Move "cat" into word1
word2 = temp    # Move the saved "dog" into word2
```
- A variable is like a container that stores a value.
- The order of assignment statements matters.
- `Temp` is commonly used to hold a value while other variables are being updated.
- Swapping is useful whenever values need to change order, such as in sorting.


--- 

# Today

## Another data type: List
- understnad what a list is;
- compare lists with strings;
- learn how to create and access a list;
- practice changing the items in a list;
- use common list operations and methods.




---

# Question

### A sequence of characters → a **string**

###  What if we want to store a group of items? → a **list**


---
layout: center
---
 
# List

## A data type for a more general sequence

---
 
# Strings vs. Lists

- A **string** is an ordered sequence of **characters**.
- A **list** is an ordered sequence of **objects**
- They can be different data types and are called **elements**


```python
# a list of int
numbers = [42, 123] 

# a list of string
cheeses = ['Cheddar', 'Edam', 'Gouda']

# a list of boolean values
pass_exam = [True, False, True]
```

---

# List Index
| Python code | Inside the computer |
|:---:|:---:|
| `['Cheddar', 'Edam', 'Gouda']` | <table><tr><td>item</td><td>'Cheddar'</td><td>'Edam'</td><td>'Gouda'</td></tr><tr><td>index</td><td>0</td><td>1</td><td>2</td></tr></table> |

<br>

| Python code | Inside the computer |
|:---:|:---:|
| `[42, 5, 5]` | <table><tr><td>item</td><td>42 </td><td>5</td><td>5</td></tr><tr><td>index</td><td>0</td><td>1</td><td>2</td></tr></table> |


 
 

---

# Note 1: List is enclosed in square brackets.

- We know a string is usually wrapped by quotes 
- A list is enclosed in square brackets.
- The elements in the list are seperated by comma

```python
[item_1, item_2, ..., item_n]
```

<v-clicks>

- A list can have only one element: `[3]`
- A list can also be empty: `[]`

</v-clicks>

---

# Note 2: Lists Can Contain Different Objects

```python
[1, 2, 3, 4, 5] # a list of int

["Hello", "World"]  # a list of str

[True, False, False]  # a list of bool

[1, "abc", False] # a list of int, str, and bool

[1, "abc", False, [1,2,3]] # a list of int, str,  bool and a list 
```
---

# A list can contain another list

`my_list = [1, 'abc', False, [1,2,3]]`

| Python code | Inside the computer |
|:---:|:---:|
| `[1, 'abc', False, [1,2,3]]` | <table><tr><td>item</td><td>1</td><td>`'abc'`</td><td>`False`</td><td>`[1,2,3]`</td></tr><tr><td>index</td><td>0</td><td>1</td><td>2</td><td>3</td></tr></table> |

<br>

- `[1, 2, 3]` is the fourth element of `my_list`, at index 3.
- Although `[1, 2, 3]` contains three elements of its own, it counts as one item in `my_list`.
  
---

# Your Turn


- Create a variable called `grocery`.
- Assign it a list of three things you need to buy. - Each item should be a string.
- Print the list.

---

# Example

```python
grocery = ['olives', 'peppers', 'milk']

print(grocery)
# ['olives', 'peppers', 'milk']

# Or add a label:
print(f"Grocery shopping: {grocery}")
# Grocery shopping: ['olives', 'peppers', 'milk']
```

Quick Review:
- `grocery` is a variable
- `=` assigns a value to that variable
- `['olive','pepper','milk']` a list of three string literals
  
---
layout: center
---
 
# List Operations

## Getting information from a list

---

# List Operations

Many list operations work like just string operations:

- indexing
- slicing
- concatenation
- multiplication
- `len()`, `count()`, `index()`



---

# Indexing (get one item)

```python
my_list = ["Nice", "to", "meet", "you"]


my_list[0]   # "Nice" — first element

my_list[1]   # "to"   — second element

my_list[-1]  # "you"  — last element (reverse indexing)

```


---

# Slicing (get a sublist)

```python
my_list = ["Nice", "to", "meet", "you"]


my_list[1:3]  # ["to", "meet"]
my_list[1:]   # ["to", "meet", "you"]
my_list[0:2]  # ["Nice", "to"]
my_list[:5]   # ["Nice", "to", "meet", "you"]
```

Like string slicing:
- The starting index is **included**
- The ending index is **not included**.

---

# Slicing Returns a List
- Slicing a string gives back a **substring** (type str)
- Slicing a list gives back a **sublist** (type list)

```python
my_list = ["Nice", "to", "meet", "you"]
result = my_list[1:3]

print(result)
```

```text
['to', 'meet']
```

---

# Your Turn

You are given a list of names:

```python
my_list = ["John", "Sue", "Mary"]
```

Write expressions that return:

1. A string `"John"`
2. A string `"Sue"`
3. A list containing `"Sue", "Mary"`
4. A list containing only `"Sue"`

---

# Example


```python
my_list = ["John", "Sue", "Mary"]

my_list[0]    # "John" (a string literal)

my_list[1]    # "Sue"  (a string literal)

my_list[1:]  # ["Sue", "Mary"] (a sublist from index 1 to the end)

my_list[1:2]  # ["Sue"] (a sublist starting at index 1 and stopping before index 2)
```

---

# Concatenation: Join Two Lists
You can join two strings using `+`

```python
word1 = "book"
word2 = "case"
print(word1+word2)
# bookcase
```
You can do the same to join two lists using `+`
```python
my_list = ["Nice", "to", "meet", "you"]
my_list + ["!"]
# ["Nice", "to", "meet", "you", "!"]

["!"] + my_list 
# ["!", "Nice", "to", "meet", "you"]
```
The order matters again...

---

# Multiplication: Repeat a List
You can repeat a string using `*`

```python
word = "ha"

word * 3
# hahaha
```
You can do the same to repeat a list using `*`
```python
my_list = ["one", "two"]

my_list * 2
# ['one', 'two', 'one', 'two']

```

---

#  `len()`, `.count()`, and `.index()`

Just as you can use these function or methods in strings, you can also use it to a list.
- `len(my_list)`: returns the number of items in the list.
- `my_list.count(item)`: returns how many times an item occurs in the list.
- `my_list.index(item)`: returns the index of the first occurrence of item.

```python
my_list = ["How", "do", "you", "do"]
len(my_list)
# 4

my_list.count('do')   # 2

my_list.index('do')   # 1

my_list.index('find')
# ValueError: 'find' is not in list
```

---

# Your Turn: 

```
vowels = ["a", "i", "a", "u", "a", "i"]

# Print the number of elements.

# Print the number of times "a" occurs.

# Print the index of the first "u".
```

---

# Answer:

```python
vowels = ["a", "i", "a", "u", "a", "i"]

# Print the number of elements.
print(len(vowels))
# 6


# Print the number of times "a" occurs.
print(vowels.count('a'))
# 3

# Print the index of the first "u".
print(vowels.index('u'))
# 3

```
