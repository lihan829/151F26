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

We know there are several ways to print a bunch of stuff in a print()
```python
# 1. Print a string literal directly
print("hello world")

# 2. Print multiple variables
word1 = "hello"
word2 = "world"
print(word1, word2)

# 3. Print a variable and a string literal
print(word1, "world")

# 4. Use "+"
print(word1 + " " + word2)

# 4. Use an f-string
print(f"{word1} {word2}")
print(f"{word1} world")

```
All four produce the same output `hello world`

---

# Q1: when to use `f-string` and `print()`

It is often up to you which method you use. However:

- Use commas for simple printing (comma automatically adds a space between the items)
- Use an f-string when you want to combine multiple variables and text in a clear, flexible format.
- Be careful with `+`: it does not add spaces automatically, and it can only join strings.(not recommended)
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

## A sequence of characters → a **string**

## What if we want to store a group of items? -> a **list**


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

| Python code | Inside the computer |
|:---:|:---:|
| `['Cheddar', 'Edam', 'Gouda']` | <table><tr><td>item</td><td>'Cheddar'</td><td>'Edam'</td><td>'Gouda'</td></tr><tr><td>index</td><td>0</td><td>1</td><td>2</td></tr></table> |

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
[1, 2, 3, 4, 5]

["Hello", "World"]

[True, False, False]

[1, "abc", False]

[1, "abc", False, [1,2,3]]
```
---

# Your Turn


- Create a variable called grocery.
- Assign a list containing three strings to grocery
- (the strings are any items you need to buy)
- Print the list.

---

# Example

```python
grocery = ['olive','pepper','milk']

print(grocery)

print(f"Grocery shopping: {grocery}")
```
<style>
.slidev-code {
  font-size: 1.4rem !important;
  line-height: 1.7 !important;
}
</style>

---
layout: center
---
 
# List Operations

## Getting Information from a List or Accessing Its Elements

---

# List Operations

Many list operations work like just string operations:

- indexing
- slicing
- concatenation
- multiplication
- `len()`, `count()`, `index()`



---

# Indexing Gets One Item

```python
my_list = ["Nice", "to", "meet", "you"]

my_list[0]

my_list[1]

my_list[-1]

```


---

# Slicing Gets a Sublist

```python
my_list = ["Nice", "to", "meet", "you"]

my_list[1:3]

my_list[1:]

my_list[0:2]

my_list[:5]
```


The ending index is **not included**.

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

# Concatenation Joins Two Lists
You can join two strings using `+`

```python
word1 = "book"
word2 = "case"
print(word1+word2)
# bookcase
```
You can do the same: join two lists using `+`
```python
my_list = ["Nice", "to", "meet", "you"]
my_list + ["!"]
?

["!"] + my_list 
?
```

---

# Multiplication Repeats a List

```python
my_list = ["one", "two"]
my_list * 2
```

<v-click>

```text
['one', 'two', 'one', 'two']
```

</v-click>

---

#  `len()`, `count()`, and `index()`

Just as you can use these methods in string operations, you can also use it to a list.

```python
my_list = ["How", "do", "you", "do"]
len(my_list)
# 4

my_list.count('do')
 
my_list.index('do')

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

# Nested Lists

Lists can also contain other lists.

A matrix is a common example. Here, each inner list represents a row:

```python
matrix = [              # a nested list open [
          [1, 2, 3],    # inner list 1 
          [4, 5, 6],    # inner list 2
          [7, 8, 9]     # inner list 3
          ]             # a nested list open ]
```


> How many elements does `matrix` contain?


---

# Your Turn:

```python
matrix = [[1, 2, 3],
          [4, 5, 6],
          [7, 8, 9]]
```

Write expressions that return:

1. A list containing `[1,2,3]`
2. A list containing `[[4,5,6] [7,8,9]]`
3. A list containing `[8,9]`
4. An interger `6`

---

# Your Turn:

```python
matrix = [[1, 2, 3],
          [4, 5, 6],
          [7, 8, 9]]

matrix[0]       # [1, 2, 3]
matrix[1:]      # [[4, 5, 6], [7, 8, 9]]
matrix[-1][1:]   # [8, 9]
matrix[1][2]    # 6          
matrix[1][-1]    # 6    
```
- The first [ ] selects an item from the outer list
- The second [ ] selects an item from the second outer list 
- ...

---
layout: center
---

# Type Conversion

## Moving between strings and lists

---

# Why Convert Between Strings and Lists?

A sentence can be represented as one string or 
a list of words

```python
# One string
sentence = "Call me Ishmael"

# A list of tokens
tokens = ["Call", "me", "Ishmael"]
```


- Converting a text into its smaller chunks is called **tokenization**

- Each individual unit is called a **token**.

- Tokens can be words such as ` ["Call", "me", "Ishmael"]`
- or characters` ["b", "o", "y"]`

- Representing text as a list of tokens makes it easier to access, count, add, remove, or modify individual units.

---
layout: center
---

# String to List

---

# From String to List: `.split()` 

`.split()` is a string method that splits a string at whitespace by default.

```python
sentence = "Call me Ishmael"
words = sentence.split()

print(words)

# ['Call', 'me', 'Ishmael']


```
`split()` treats consecutive whitespace as a single separator, but it does not separate punctuation from words.

```python
"Call.         me Ishmael.".split()
# ['Call.', 'me', 'Ishmael.']

```

---

# `.split()`

You can specify a different **separator** other than whitespace:

Try these yourself and report the output

```python
"2026-08-17".split("-")

"apple,banana,orange".split(",")

"apple and banana and orange".split()

"apple and banana and orange".split("and")
```

---

# `.split(maxsplit)`

You can use `maxsplit` to specify how many "cuts" to make.

Try these yourself and observe how maxsplit works


```python
"2026-08-17".split("-", maxsplit = 1)

"apple and banana and orange".split(",",maxsplit = 1)
```

---

# `list()` for smaller chunks

The function `list()` turn a string into a list of individual characters

Try these yourself and observe how maxsplit works

```python
sen = "Call me Ishmael"
list(sen)
```
<v-click>

<br>

```
['C', 'a', 'l', 'l', ' ', 'm', 'e', ' ', 'I', 's', 'h', 'm', 'a', 'e', 'l']
```

Each space counts as one character
</v-click>
---
layout: center
---

# List to String

---

# List to String: `join()`

We can convert a list into one string by using `join()`

```python
my_list = ["We", "are", "free"]
" ".join(my_list)
# 'We are free'
```
- this is different than `split()` which put the separator in the parenthesis

- the string before `.join()` serves as a separator
- choose your separator to your liking

```python
"-".join(my_list)     # 'We-are-free'
"".join(my_list)      # 'Wearefree'
"!".join(my_list)      # 'We!are!free'
```
---

# Mutability
  
Lists are **mutable**, meaning that their elements can be changed after the list is created.

```python
my_list = ["b", "o", "y"]

my_list[0] = "t"

print(my_list)
# ['t', 'o', 'y']
```

<v-click>

Strings are **immutable**, meaning that their characters cannot be changed directly.

```python
my_string = "boy"

my_string[0] = "t"
# TypeError: 'str' object does not support item assignment
```

</v-click>

---

# Mutability

- Becuase Lists are mutable
- they can change in place without having to create a new list
- Many list methods change the **existing list**.


--- 

# Adding new item to an existing list

Run the two blocks of codes, what differences do they have 

## Adds item with `+`
```python
my_list = [1, 2, 3, 4, 5]

my_list + [6]
print(my_list)
```

## Adds item with `.append()` 

```python
my_list = [1, 2, 3, 4, 5]

my_list.append(6)
print(my_list)
```

---

# Append or Concatenate?

What is the difference?

```python
my_list = [1, 2, 3, 4, 5]

my_list + [6]
print(my_list)
# [1, 2, 3, 4, 5]

my_list.append(6)
print(my_list)
# [1, 2, 3, 4, 5, 6]

```
<br>
<v-clicks>

- `+` creates and returns a **new list**.
- `.append()` changes the **existing list** and returns `None`.

</v-clicks>

---

# Common List Methods

| Operation | Example |
|---|---|
| Reverse the list | `my_list.reverse()` |
| Sort in ascending order | `my_list.sort()` |
| Sort in descending order | `my_list.sort(reverse=True)` |
| Insert an item at a position | `my_list.insert(index, item)` |
| Remove the first matching item | `my_list.remove(item)` |

All these methods modify the existing list **in place**.

---

# Your turn: modify a list

```python
tokens = ["linguists", "study", "language"]
```
<br> 

### Use string methods to:

1. Replace the first item to `"student"`


2. Insert `"spoken"` after `"study"`


3. Remove `"language"`:


4. Reverse the word order:

---

# Lists Help Us Process Text

Why do we need Lists in text processing?

Suppose we want to count the article `"a"`:

```python
text = """I do not know what I may appear to the world, but
I seem to have been only like a boy playing on the seashore"""
```

What will this expression output?

```python
text.count("a")
```

<v-click>

It counts every occurrence of the **character** `"a"`, including the `a` in words such as `"what"`, `"may"`, and `"appear"`. 

</v-click>

---

# Count the Token `"a"`

First, tokenize the text:

```python
tokens = text.split()
```

Now count the token `"a"`:

```python
tokens.count("a")
# 1
```

- `text.count("a")` counts the **character** `"a"`.
- `tokens.count("a")` counts the **token** `"a"`.

---

# Summary


- A **list** is an ordered sequence of elements.

- Indexing retrieves one element; slicing retrieves a sublist.

- Lists support operations such as `+`, `*`, and `len()`.

- `split()` converts a string into a list of tokens.

- `join()` combines a list of strings into one string.

- Lists are **mutable**: their elements can be changed in place. Strings are not mutable 

- `in`, `.index()`, and `.count()` help us search lists.

- Tokenization lets us count words instead of characters.

