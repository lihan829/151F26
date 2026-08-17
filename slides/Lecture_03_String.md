--- #1
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
 # Today's Goal



## Review


- Computational Linguistics
- Variable, literals
- `print` and `input()`
- Basic datatypes: `str` ,`int`, `float`
 

## Today

- More on data type: string
- Function processing string

---
layout: default
---

# String

## A string is a <span class="orange">sequence</span> of <span class="orange">characters</span>

1. A string can be enclosed in single or double quotes: `"Hello"` or `'Hello'`
2. Each character in a string has an index.
   - Unlike humans, computers start indexing from `0`
   - The index represents the **distance** from the beginning.
  
| Python code | Inside the computer |
|:---:|:---:|
| `"Hello"` | <table><tr><td>char</td><td>H</td><td>e</td><td>l</td><td>l</td><td>o</td></tr><tr><td>index</td><td>0</td><td>1</td><td>2</td><td>3</td><td>4</td></tr></table> |
 
But how to print quotes in a string?


---
layout: default
---

# Quotes inside Strings

- Quotation marks that delimit a string are **not** part of the string.
- How can we include quotation marks inside the string?
- Put a backslash (`\`) before each quotation mark.
- This is called an **escape sequence**.

| Python code | Inside the computer |
|:---:|:---:|
| `"\"Hello\""` |<table><tr><td>char</td><td>"</td><td>H</td><td>e</td><td>l</td><td>l</td><td>o</td><td>"</td></tr><tr><td>index</td><td>0</td><td>1</td><td>2</td><td>3</td><td>4</td><td>5</td><td>6</td></tr></table> |

---
layout: default
---

# Escape Sequences

Escape sequences begin with a **backslash** (`\`) and represent special characters.

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

The `len()` function counts the number of characters in a string.

```python
>>> word = "linguistics"
>>> len(word)
11

>>> len("Hello!")
6

# Guess what the outputs would be?
>>> course1 = "LCD 151"
>>> len(course1)

>>> course2 = "LCD\t151"
>>> len(course2 )
```


---
layout: default
---

# Quick Practice

Each line contains a mistake. Fix it so that it produces the expected output.

```python
# Expected: My favorite word is "linguistics".

# Expected: syntax
#           phonology

# Expected: vowel    25

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

# Quick Practice

```python
print("My favorite word is \"linguistics\".")
>>> My favorite word is "linguistics".

print("syntax\nphonology")
>>> syntax
    phonology

print("vowel\t25")
>>> vowel   25

print("data\\corpus.txt")
>>> data\corpus.txt
```

---
layout: default
---
# Print Multiple variables

In the previous class, we talked about you can throw in multiple variables in
one `print` function

```python
>>> movie = "Star Wars"
>>> year = 2005
>>> print(movie, "was released in", year)
```

The output will be a joined string with spaces connected 

```text
Star Wars was released in 2005.
```

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

**Exerise** Create four variables: `first_name`, `last_name`, `major`, and `grade`. Print all four variables as a formatted string:
```text
My first name is Han. 
My Last name is Li.
My major is Psychology.
My grade is Junior.
```

---
layout: center
---

# String Operation
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
i
>>> print(f"the No.{2} char in "{my_string}" is {my_string[2]}")
```
---
layout: default
---
# Accessing Characters in Strings


| Character | s | m | i | l | e |
|:---:|:---:|:---:|:---:|:---:|:---:|
| Index | 0 | 1 | 2 | 3 | 4 |


Try the following "irregular" expression
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
The final index is always `len(string) - 1`.
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

- When will this operation come handy?
- what if `print(my_string[-6])`
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
| `-` | Not supported | `"books" - "s"` | `TypeError` |
| `/` | Not supported | `"hello" / 2` | `TypeError` |

Note: `+` joins strings; it does not insert a space automatically.

```python
>>> first = "computational"
>>> second = "linguistics"
>>> first + " " + second
computational linguistics  
```




---
layout: default
---
 
# String Slicing

- Slicing extracts part of a string using `[start:stop]`  
  - The `start` index is included;  `stop` index is not included.
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

How can we produce each version of the title?

```text
"ASSOCIATION WITH FOCUS" # all caps
"association with focus" # all lower case
"Association with focus" # cap initial 
```

```python
s = "Association with Focus"
```

<!--
case
-->

---
layout: default
---

# Changing Case

| Python code | Result |
|---|---|
| `s.upper()` | `"ASSOCIATION WITH FOCUS"` |
| `s.lower()` | `"association with focus"` |
| `s.swapcase()` | `"aSSOCIATION WITH fOCUS"` |
| `s.capitalize()` | `"Association with focus"` | 
| `s.title()` | `"Association With Focus"` |
What is the difference between `capitalize()` and `title()`?

---
layout: default
---

# Strings: Review
- String is a sequence of characters
- Indexing and slicing are two basic functions to access strings
- Index starts from 0, the max index is `len(my_string)-1`
  
| Task | Tool | Code|
|---|---|---|
| Get one character | indexing | `my_string[0]`|
| Get part of a string | slicing |`my_string[:3]`,`my_string[-2:]`,`my_string[2:4]`||
| Join strings | `+` |`str1 + str2`|
| Count characters | `len()` |`len(string)`|
| Change letter case | `.upper()`, `.lower()`, etc. | `my_string.lower()`|


---
layout: two-cols-header
---

# Functions and Methods

You might wonder why these two expressions look different:
```python
my_string = 'Hi'
print(my_string)  # you need to pass an argument
my_string.lower() # there's nothing in the parethesis

```
The answer is `print` is a **fucntion** while `.lower()` is a **method**
---
layout: default
---
# Functions and Methods

- A **function** takes an object as an argument.  `<function>(<object>)`

```python
>>> len("abc")
3
```
- A **method** is a function attached to a particular type of object. `<object>.<method>()`
- The `.upper()` method works only with strings.

```python
>>> "abc".upper()
'ABC'
```
- Try to call .upper() on another type of object:
```
>>> age = 32
>>> age.upper()

>>> 10.upper()
```


---
layout: center
class: text-center
---

# Extra Slides: **More String Methods**

Useful tools for cleaning and searching text

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
True

>>> "'Hm...'".startswith("'")
True

>>> "Yes.".endswith((".", "?", "!"))
True
```

- `startswith()` checks the beginning of a string.
- `endswith()` checks the end of a string.
- A tuple lets us check several possibilities.

---

# Checking String Content

```python
>>> "151".isnumeric()
True

>>> "LCD151".isnumeric()
False

>>> "linguistics".isalpha()
True

>>> "LCD151".isalnum()
True
```

These methods return either `True` or `False`.

---
layout: center
class: text-center
---

# Searching Substring

How can we find a string inside a larger string?

---

# Is the Substring Present?

Use the `in` operator:

```python
>>> "He" in "Hello"
True

>>> "he" in "Hello"
False
```

Note that the string matching is case-sensitive.

---

# Finding a Substring: `index()`

```python
>>> "Hello".index("el")
1

>>> "Hello".index("l")
2

>>> "Hello".index("he")
ValueError: substring not found
```

`index()` returns the **starting** index of the first match. It raises an error when there is no match.

---


# Finding a Substring: `find()`

```python
>>> "Hello".find("el")
1

>>> "Hello".find("l")
2

>>> "Hello".find("he")
-1
```

`find()` returns `-1` when there is no match.

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
Byeee


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
