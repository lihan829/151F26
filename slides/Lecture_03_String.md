---
theme: seriph
background: '#fff8e6'
themeConfig:
  primary: '#2ca4d3'
title: Data Type - 1
info: false
# class: text-center
fonts:
  sans: Lexend
  serif: Roboto Slab
  mono: Fira Code
---

# Strings

### LCD151 Lecture 
### Instructor: Han Li
<h3>{{ new Date().toLocaleDateString('en-US', {
  year: 'numeric',
  month: 'long',
  day: 'numeric'
}) }}</h3>

---
layout: default
---
# Today's Goals



## Review
- Variable, literals
- `print` and `input()`
- Basic data types: `str`, `int`, and `float`
 

## Today

- Strings as sequences of characters
- String operations and methods

---
layout: default
---

# String

## A string is a <span class="orange">sequence</span> of <span class="orange">characters/symbols</span>

1. A string can be enclosed in single or double quotation marks: `"Hello"` or `'Hello'`.
2. Each character in a string has an index.
   - Python starts indexing from `0`.
   - An index represents the **distance** from the beginning.
  
| Python code | Inside the computer |
|:---:|:---:|
| `"Hello"` | <table><tr><td>char</td><td>H</td><td>e</td><td>l</td><td>l</td><td>o</td></tr><tr><td>index</td><td>0</td><td>1</td><td>2</td><td>3</td><td>4</td></tr></table> |
 



---
layout: default
---

# Quotation Marks inside Strings
If quotation marks delimit a string and are not part of it, how can we print quotation marks?

<v-click>

1. Use the other type of quotation mark when possible. 
```python
'She said, "Hi!"'
```
   

2. Use a backslash (`\`) when the inner and outer quotation marks match.

```python
"She said, \"Hi!\""
```


| Python code | Inside the computer |
|:---:|:---:|
|`'"Hello"'`<br> <br>  `"\"Hello\""` |<table><tr><td>char</td><td>"</td><td>H</td><td>e</td><td>l</td><td>l</td><td>o</td><td>"</td></tr><tr><td>index</td><td>0</td><td>1</td><td>2</td><td>3</td><td>4</td><td>5</td><td>6</td></tr></table> |

</v-click>

---
layout: default
---

# Escape Sequences

- An **escape sequence** is a backslash (`\`) followed by another character. 
- It resolves the issue where a character may be difficult to type directly.


| Escape sequence | Meaning | Example | Output |
|:---:|---|---|---|
| `\n` | New line | `"Hello\nWorld"` | Hello<br>World |
| `\t` | Tab | `"Name\tGrade\tID"` | Name&emsp;Grade&emsp;ID |
| `\"` | Double quotation mark | `"She said, \"Hi!\""` | She said, "Hi!" |
| `\\` | Backslash | `"C:\\Users\\Han"` | C:\Users\Han |
---
layout: default
---

# String Length: `len()`

- The `len(...)` function counts the number of characters in a string.

```python
>>> word = "linguistics"
>>> len(word)
11

# Guess what the outputs would be?
>>> course1 = "LCD 151"
>>> len(course1)

>>> course2 = "LCD\t151"
>>> len(course2)
```

You can try them yourself!

---
layout: default
---

# Quick Practice

Each line contains a mistake. Fix it so that it produces the expected output.

```python
print("My favorite word is "linguistics".")
# Expected: My favorite word is "linguistics".

print("syntax phonology")
# Expected: syntax
#           phonology

print("data\corpus.txt")
# Expected: data\corpus.txt
```

<style>
.slidev-code {
  font-size: 1.4rem !important;
  line-height: 1.7 !important;
}
</style>
---
layout: default
---

# Quick Practice - Answer

```python
print("My favorite word is \"linguistics\".")
# My favorite word is "linguistics".

print("syntax\nphonology")
# syntax
# phonology

print("data\\corpus.txt")
# data\corpus.txt
```
<style>
.slidev-code {
  font-size: 1.4rem !important;
  line-height: 1.7 !important;
}
</style>
---
layout: default
---
# Printing Multiple Variables

In the previous class, we used one `print()` function to display several values:

```python
>>> movie = "Star Wars III – Revenge of the Sith"
>>> year = 2005
>>> print(movie, "was released in", year)
```

By default, `print()` places a space between the values:

```text
Star Wars III – Revenge of the Sith was released in 2005.
```
<style>
.slidev-code {
  font-size: 1.4rem !important;
  line-height: 1.7 !important;
}
</style>
---
layout: default
---

# Formatted Strings (f-strings)

An **f-string** inserts variable values directly into a string.
  - `print(f"...{var1}...{var2}...")`
  - Add `f` before the opening quotation mark
  - Put variables or expressions inside `{ }`

```python
print(f"{movie} was released in {year}.")
```
<br>
<style>
.slidev-code {
  font-size: 1.4rem !important;
  line-height: 1.7 !important;
}
</style>
---

# Notebook Practice 

Create variables for your name, major, and grade. 
Use an f-string and `\n` to print each value on a separate line.
```
first_name = "Han"    # replace with your firstname
last_name = "Li"      # replace with your lastname
major = "Psychology"  # replace with your major
grade = "Junior"      # replace with your grade

# Expected output:
#  My name is Han Li.
#  My major is Psychology.
#  My grade is Junior.
```

Answer 
```
print(f"My name is {first_name} {last_name}.\nMy major is {major}.\nMy grade is {grade}.")
```


---
layout: center
---

# String Operations
## Basics of text-based computing

---
layout: default
---
# Accessing Characters in Strings

We can access a **character** in a string using its index inside square brackets (`[]`).

| Character | s | m | i | l | e |
|:---:|:---:|:---:|:---:|:---:|:---:|
| Index | 0 | 1 | 2 | 3 | 4 |

<br>


```python
>>> my_string = "smile"
>>> print(my_string[0])
s
>>> print(my_string[3])
?
```
<style>
.slidev-code {
  font-size: 1.4rem !important;
  line-height: 1.7 !important;
}
</style>
---
layout: default
---

# Accessing Characters in Strings


| Character | s | m | i | l | e |
|:---:|:---:|:---:|:---:|:---:|:---:|
| Index | 0 | 1 | 2 | 3 | 4 |


What if:
```python
>>> my_string = "smile"
>>> print(my_string[10])
>>> print(my_string[5])
```
<v-click>

You will get an error message:
```text
IndexError: 
string index out of range
```

</v-click>
<style>
.slidev-code {
  font-size: 1.2rem !important;
  line-height: 1.7 !important;
}
</style>
<v-click>

**The final index is always `len(string) - 1`.**

</v-click>

---
layout: default
---
# Accessing Characters in Strings

Try the following "negative" expression

```python
>>> my_string = "smile"
>>> print(my_string[-1])
>>> print(my_string[-5])
```


<v-click>

Python allows indexing from the right end of a string using negative indexes.

| Character | s | m | i | l | e |
|:---:|:---:|:---:|:---:|:---:|:---:|
| Index | 0 | 1 | 2 | 3 | 4 |
| Reverse Index | -5 | -4 | -3 | -2 | -1 |

- When might negative indexing be useful?
- What happens if we run `print(my_string[-6])`?  --> `IndexError`
</v-click>

---
layout: default
---

# String Operations

Strings support `+` and `*`, but not `-` or `/`.

| Operator | Meaning | Example | Result |
|:---:|---|---|---|
| `+` | Join strings | `"book" + "case"` | `"bookcase"` |
| `*` | Repeat a string | `"ha" * 3` | `"hahaha"` |
| `-` or `/`| Not supported | `"books" - "s"` or `"hello" / 2`| `TypeError` |

Note: `+` joins strings; it does not insert a space automatically.

```python
>>> first = "computational"
>>> second = "linguistics"
>>> full_name = first + " " + second
>>> print(full_name)
>>> print(first, second)
```




---
layout: default
---
 
# String Slicing

- Slicing extracts part of a string (a substring) using `[start:stop]`  
  - The `start` index is included;  `stop` index is not included.
  - `stop` - `start` will always be the len of the substring.
  - Leave out `start` to begin at the start: `word[:4]`
  - Leave out `stop` to continue to the end: `word[4:]`
```python
>>> word = "linguistics"
>>> word[0:4]
'ling'
>>> word[4:6]
'ui'

# Try the following yourself
>>> word[:4]    
>>> word[7:]    
>>> word[-3:]
```
---
layout: default
---

# Operations Regarding Case
Now given a string

```python
s = "Association with Focus"
```

How can we easily produce each version of the title?

```text
"ASSOCIATION WITH FOCUS" # all caps
"association with focus" # all lower case
"Association with focus" # cap initial 
```


---
layout: default
---

# Changing Case

There are a set of built-in methods for converting cases of strings.

| Python code | Result |
|---|---|
| `s.upper()` | `"ASSOCIATION WITH FOCUS"` |
| `s.lower()` | `"association with focus"` |
| `s.capitalize()` | `"Association with focus"` | 
| `s.title()` | `"Association With Focus"` |
<!-- | `s.swapcase()` | `"aSSOCIATION WITH fOCUS"` | -->
<!-- What is the difference between `capitalize()` and `title()`? -->


---
layout: default
---

# Functions and Methods

You might wonder why these two expressions look different:
```python
my_string = 'Hi'
print(my_string)  # you need to pass an argument
my_string.lower() # the object comes before the dot

```
`print()` is a **function**, while `.lower()` is a **method**.
---
layout: default
---
# Functions and Methods

- A **function** receives an object as an argument: `<function>(<object>)`.

```python
>>> len("abc")
3
```
- A **method** belongs to a particular type of object: `<object>.<method>()`.
- The `.upper()` method works only with strings.

```python
>>> "abc".upper()
'ABC'
```
- Try to call .upper() on another type of object:
```
>>> age = 32
>>> age.upper()

AttributeError: 'int' object has no attribute 'upper'

```
---
layout: default
---

# Strings: Review
- String is a sequence of characters
- Indexing and slicing are two basic operations for accessing strings
- Indexing starts from `0`; the final valid index is `len(my_string) - 1`
  
| Task | Tool | Code|
|---|---|---|
| Get one character | indexing | `my_string[0]`|
| Get part of a string | slicing | `my_string[:3]`, `my_string[-2:]`, `my_string[2:4]` |
| Join strings | `+` |`str1 + str2`|
| Count characters | `len()` |`len(string)`|
| Change case (methods) | `.upper()`, `.lower()`, etc. | `my_string.lower()`|

--- 

# Explain the Code

Explain what each line does

```python
word = input("please give me a word: ")
index = int(input("please give me an index: "))
print(f"the No. {index} letter in the word {word} is {word[index]})
```

---
# layout: center
# class: text-center
---

# Next Class

## Reading:
- Think Python Chap 8. Strings and Regular Expressions (Up to 8.5)
  
## Reminder:
- Your Lab 1 is due Thursday before class. 
- 20% late penalty per 24-hour
> If you feel struggling, please talk to me ASAP. Later topics will build on this material and become more challenging.

---

# Quick Review:

## Last time we've discussed:
1. String is a sequence of indexed symbols or characters
2. We can use (reverse) indexing and slicing to access one or more characters 

| Topic | Example | Result |
|---|---|---|
| String length | `len("Hello")` | `5` |
| F-string | `f"Hello, {name}!"` | Inserts the value of `name` |
| First character | `"hello"[0]` | `h` |
| Last character | `"hello"[-1]` | `o` |
| Slice `[start(included):end(excluded)]` | `"hello"[1:4]` | `ell` |
| Slice from edges| `"hello"[2:]` | `llo`| 


---
layout: center
class: text-center
---

# More String Methods

Useful tools for cleaning and searching text


---

# Case Converting

| Python code | Result |
|---|---|
| `s.upper()` | `"ASSOCIATION WITH FOCUS"` |
| `s.lower()` | `"association with focus"` |
| `s.capitalize()` | `"Association with focus"` | 
| `s.title()` | `"Association With Focus"` |
| `s.swapcase()` | `"aSSOCIATION WITH fOCUS"` |
<!-- What is the difference between `capitalize()` and `title()`? -->

---

# String Methods
These methods return a new string. They do not change the original variable:

```python
>>> word = "hello"

>>> word.upper()
HELLO

>>> word
hello
```

To save the changed string, assign it to a variable:

```python
>>> word_updated = word.upper()
>>> word_updated
HELLO
```
---

# Trimming a String

| Python code | Result |
|---|---|
| `"  Hello!  ".strip()` | `"Hello!"` |
| `"  Hello!  ".lstrip()` | `"Hello!  "` |
| `"  Hello!  ".rstrip()` | `"  Hello!"` |

- `lstrip()` removes whitespace from the left.
- `rstrip()` removes whitespace from the right.
- `strip()` removes whitespace from both sides.

> These methods also remove leading or trailing tabs and newlines.

---

# Checking the Edges

```python
>>> "Hello!".endswith("!")

>>> "'Hm...'".startswith("'")

>>> "Yes.".endswith((".", "?", "!")) 

```
<br>

- `startswith()` checks the beginning of a string.
- `endswith()` checks the end of a string.
- A bracket set of symbols lets us check several possibilities.

---

# Checking String Content
String methods can check what kinds of characters a string contains. 

These methods below only return either `True` or `False`.

Predict the output

```python
>>> "151".isnumeric()   # iDoes the string contain only numeric characters?

>>> "LCD151".isnumeric() 

>>> "linguistics".isalpha() # Does the string contain only alphabetic characters

>>> "LCD151".isalnum() # What do you think alnum means? What does this method check? 


```



---
layout: center
class: text-center
---

# Searching Substring

How can we find a string inside a larger string?

---

# Is the Substring Present?

Use the in operator to check whether one string appears inside another string.

```python
>>> "He" in "Hello"
True

>>> "he" in "Hello"
?
```

Note that the string matching is case-sensitive.

---

# Finding a Substring: `index()`

#### The index() method finds where a substring **first** begins.

```python
>>> "Hello".index("el")
1

>>> "Hello".index("l") 
?

>>> "Hello".index("he")
?
```

---

# Finding a Substring: `index()`

#### The index() method finds where a substring **first** begins.

```python
>>> "Hello".index("el")
1

>>> "Hello".index("l") 
2 # only return the first match

>>> "Hello".index("he")
ValueError: substring not found
```


---


# Finding a Substring: `find()`

 The `find()` method does pretty much the same as the `index()` method, except that it returns -1 when the substring is not found instead of raising an error.

```python
>>> "Hello".find("el")
1

>>> "Hello".find("l")
2

>>> "Hello".find("he")
-1
```


---


# Counting and Replacing

```python
>>> "Hello".count("l")
2

>>> "Hello".count("he")
0

>>> "Hello, World!".replace("World", "class")
'Hello, class!'
```

- `count()` counts occurrences of a substring.
- `replace()` returns a new string with substitutions.

---
layout: center
---



<style>
:root {
  --knicks-blue: #006bb6;
  --knicks-blue-dark: #004f87;
  --knicks-orange: #f58426;
  --knicks-orange-dark: #a84300;
  --knicks-navy: #13293d;
  --knicks-blue-light: #eaf5fc;
}

.slidev-layout { color: var(--knicks-navy); }
.slidev-layout h1 { color: var(--knicks-blue-dark); font-size: 2.4rem; font-weight: 750; text-align: center; }
.slidev-layout h2 { color: var(--knicks-orange-dark); font-weight: 700; }
.slidev-layout h3 { color: var(--knicks-blue); font-weight: 700; }
.slidev-layout strong { color: var(--knicks-orange-dark); }
.slidev-layout li::marker { color: var(--knicks-orange-dark); }
.slidev-layout :not(pre) > code { color: var(--knicks-blue-dark); background: #fff0e3; padding: 0.12em 0.35em; border-radius: 0.25em; }
.slidev-layout pre { border-left: 6px solid var(--knicks-orange); border-radius: 0.4rem; }
.slidev-code { font-size: 1.22rem !important; line-height: 1.4 !important; }
.slidev-layout blockquote { color: var(--knicks-navy); background: var(--knicks-blue-light); border-left: 6px solid var(--knicks-blue); padding: 0.65rem 1rem; }
.slidev-layout table { width: 100%; font-size: 1.05rem; }
.slidev-layout th { color: white; background: var(--knicks-blue-dark); font-weight: 750; }
.slidev-layout tbody tr:nth-child(even) { background: var(--knicks-blue-light); }
</style>
