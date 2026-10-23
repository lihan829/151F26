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

# Decision Structures

LCD 151

Han Li · Sep 29

---

# Problem to Solve: grade conversion

- When you see the title of a published work in English, you often find that **content words** (nouns, adjectives, verbs, adverbs) are capitalized but **function words** (of, with, the, a) are not.
  - Aspects of the Theory of Syntax<br>
  - Association with Focus<br>
  - Gone with the Wind


- How do we get the correct case for a random title?

---
layout: section
---

# Decision Structures

If ...

---

# Motivation

- Most lines in our programs are direct instructions for the computer. For example:
  - Assign a value to a variable (e.g. `x = "apple"`)
  - Calculate and assign (e.g. `f = c * 9/5 + 32`)
  - `input()`
  - `print()`
- Sometimes we want the computer to decide whether to follow the instruction depending on a certain condition.
- We can do this by using a **decision structure**.

---

# Simple Decision

- Example: conversation robot

```python
user_msg = input("Hi\n")
if user_msg == "Hi":
    print("Nice to meet you :)")
```

- What will be the result for the following input?
  - `Hi` → ?
  - `Bye` → ?

---

# Simple Decision

- Syntax:

```python
if <condition>:
    <statement>
    ...
    <statement>
```

- Interpretation:
  - if and only if the condition meets, execute the block of statements

---

# Simple Decision

- Example: numeric operation

```python
x = input("Enter a number: ")
if x.isnumeric():
    print(f"The next number:{int(x)+1}")
```

- What will be the result for the following input?
  - `3`
  - `three`
- What if you want to create a warning message for a wrong input format?

---

# Two-Way Decision

- Example: input validation

```python
x = input("Enter a number: ")
if x.isnumeric():
    print(f"The next number:{int(x)+1}")
else:
    print("Enter a numeric form")
```

- What will be the result for the following input?
  - `3`
  - `three`

---
layout: two-cols-header
---

# Thought Experiment

::left::

**Simple decision**

```python
if <condition>:
    <statements 1>
<statements 2>
```

::right::

**Two-way decision**

```python
if <condition>:
    <statements 1>
else:
    <statements 2>
```

::bottom::

- What's the difference?

---
layout: two-cols-header
---

# Thought Experiment

::left::

**Simple decision**

```python
if <condition>:
    <statements 1>
<statements 2>
```

::right::

**Two-way decision**

```python
if <condition>:
    <statements 1>
else:
    <statements 2>
```

::bottom::

- **Simple decision (if):** Statement 2 runs regardless of whether the condition is true or false, if it is outside the if block.
- **Two-way decision (if–else):** Statement 2 runs only if the condition is false.

---

# Code Block

- Pay attention to the **indentation**:

```python
user_msg = input("Hi\n")
if user_msg == "Hi":
    print("Nice to meet you :)")
print("Bye")
```

- What will be the result for the following input?
  - `Hi`
  - `Meh`

---

# Code Block

- Pay attention to the **flow**:

```python
user_msg = input("Hi\n")
if user_msg == "Hi":
    print("Nice to meet you :)")
else:
    print("Bye")
```

- What will be the result for the following input?
  - `Hi`
  - `Meh`

---

# Two-Way Decision

- Syntax:

```python
if <condition>:
    <statements 1>
else:
    <statements 2>
```

- Semantics:
  - if and only if the condition meets, execute the block of statements 1
  - otherwise execute the block of statements 2

---

# Thought Experiment

- Suppose that you want to write a program that tells if a given number is a positive number, a negative number, or zero.
- How many if-clauses do you need to implement this code?
- (Hint: How many if-clauses did you need to implement a two-way decision?)

---

# Three-Way Decision

- Solution 1: nesting if-else statements
- (suppose that `x` is already assigned a value)

```python
if x > 0:
    print("positive")
else:
    if x < 0:
        print("negative")
    else:
        print("zero")
```

---

# Three-Way Decision

- Solution 2: using `if-elif-else` statement
- `elif` allows a more concise way to express multi-way decision.

```python
if x > 0:
    print("positive")
elif x < 0:
    print("negative")
else:
    print("zero")
```

---

# Three-Way Decision

- Syntax:

```python
if <condition 1>:
    <statements 1>
elif <condition 2>:
    <statements 2>
else:
    <statements 3>
```

- `elif` allows a more concise way to express multi-way decision.

---

# Multi-Way Decision

- Suppose that you want to write a program that takes a letter grade and displays the corresponding score:
  - 4 for A
  - 3 for B
  - 2 for C
  - 1 for D
  - 0 for F

---

# Multi-Way Decision

- Solution 1: multiple `elif` statements

```python
if grade == "A":
    print(4)
elif grade == "B":
    print(3)
elif grade == "C":
    print(2)
elif grade == "D":
    print(1)
else:
    print(0)
```

---

# Multi-Way Decision

- Solution 2: `match-case` (from Python 3.10 !)

```python
match grade:
    case "A":
        print(4)
    case "B":
        print(3)
    case "C":
        print(2)
    case "D":
        print(1)
    case _:
        print(0)
```

---

# Match-Case

- Syntax:

```python
match <variable>:
    case <value 1>:
        <statements 1>
    case <value 2>:
        <statements 2>
    ...
    case _:
        <statements>
```

- Semantics: The underscore `_` indicates the default case.

---

# Match-Case

- A match-case statement is useful when the choices can be expressed by several **discrete values**.
  - e.g. letter grades
- It cannot be used if the choices are continuous or complex.

---
layout: section
---

# Exercises

Open a Python file editor

---

# `is_even()`

- Write a function that takes an integer and returns:
  - `True` if it is an even number
  - `False` if it is an odd number

---

# `word_size()`

- Write a function that takes a word and returns:
  - `"long"` if the word has 10 or more characters
  - `"medium"` if the word has 5-9 characters
  - `"short"` if the word has 4 or fewer characters

---

# `score2grade()`

- Write a function that takes a score between 0 and 100 and returns:
  - `"A"` for 90 and above
  - `"B"` for 80‒89
  - `"C"` for 70‒79
  - `"D"` for 60‒69
  - `"F"` for below 60

---

# `grade2score()`

- Write a function that takes a letter grade and returns:
  - 4 for `"A"`
  - 3 for `"B"`
  - 2 for `"C"`
  - 1 for `"D"`
  - 0 for `"F"`

---
layout: section
---

# How to express conditions

Boolean expressions

---

# Boolean Expressions

- What can be used as a "condition" in an if statement?
- Conditions must be **Boolean expressions**, which have either `True` or `False` as a value.
  - The statements in the if-block are executed if the Boolean expression is `True`.
  - Python Interpreter skips the if-block if the Boolean expression is `False`.

---

# Boolean Expressions (1)

- Syntax

```python
<expr1> <relational operator> <expr2>
```

- Example

```python
x == "hi"
```

---

# Exercises

- Exercises: Boolean Expressions - Relational Operators

<https://forms.gle/WVhdGVpgjdHa3LUf6>

---

# Relational Operators

| Read | Mathematics | Python |
|---|:---:|:---:|
| Less than | < | `<` |
| Less than or equal to | ≤ | `<=` |
| Greater than | > | `>` |
| Greater than or equal to | ≥ | `>=` |
| Equal to | = | `==` |
| Not equal to | ≠ | `!=` |

---

# Boolean Expressions (2)

- You can create a larger Boolean expression by combining Boolean expressions.

```python
<boolean1> and <boolean2>
<boolean1> or <boolean2>
not <boolean1>
```

---

# Boolean Conjunction

- Syntax

```python
<boolean1> and <boolean2>
```

- Semantics
  - `True` if both b1 and b2 are true; otherwise `False`
- Example

```python
1 < 2 and round(2.5) < 3
```

  - `True`

---

# Boolean Disjunction

- Syntax

```python
<boolean1> or <boolean2>
```

- Semantics
  - `True` if b1 or (inclusively) b2 is true; otherwise `False`
- Example

```python
1 < 2 or 2 < 3
```

  - `True`

---

# Boolean Negation

- Syntax

```python
not <boolean1>
```

- Semantics
  - `True` if b1 is not true; otherwise `False`
- Example

```python
not "a" < "A"
```

  - `True`

---

# Boolean Expressions (3)

- Bool type objects: `True`, `False`
- A function might return a Boolean object.

```python
x.isnumeric()
```

- You can write your own function to return a Boolean object!

---

# Boolean Expressions (3)

- Every Python expression indicates a bool type object, either `True` or `False`.

```python
>>> print(1<2)
True
>>> type(1<2)
<class 'bool'>
>>> my_boolean_value = 1<2
>>> my_boolean_value
True
```

---

# Boolean Expressions (4)

- Recursive application of (1)-(3)
- How to evaluate a complex expression?
  - E.g. when `a = 1`, `b = 2`, `c = 3`, what's the value of the following expression?

```python
a < 3 or not b < 4 and c > 5
```

---

# Operator Precedence

- Relational operators precede Boolean operators.
- Precedence among Boolean operators:
  - `not` < `and` < `or`
- You can use parentheses to prevent confusion

```python
(1 < 3 or ((not 2 < 4) and 3 > 5))
```

---

# Order of operations

1. Parentheses
2. Function call
3. Numeric operators (`+`, `*`, ...)
4. Relational operators (`<`, `==`, `!=`, ...)
5. Boolean operators (`and`, `or`, `not`)
6. Assignment (`=`)
7. Left to right

---

# Boolean Expressions (5)

- In fact, all objects have an inherent Boolean true or false value.
  - Any nonzero number or nonempty object is true.
  - Zero numbers, empty objects, and the `None` object are considered false.

---

# Boolean Expressions (5)

- What will be the result?

```python
s = "abc"
if s:
    print("not a null string")
```

---

# Empty Objects

- number: `0`
- str: `""`
- list: `[]`
- tuple: `()`

---

# Boolean Expressions (5)

- The inherent Boolean value of the object is useful to check if it has meaningful content or not.

```python
s = input("Say something: ")
if s:
    print("You're not empty")
else:
    print("You're empty")
```

---

# Quiz

- Value of the Boolean expression?
  - `3 * 2 > 4`
  - `"a" > "b"`
  - `"a" < "B"`
  - `"Alice" < "Alison"`
  - `0 == 0.0`
  - `int(3.5) == 3`

---
layout: section
---

# Exception Handling

try ... except

---

# Reading

- [CS] Ch 7.4 Exception Handling
- [LP] Part VII (Ch 33 - 36) Exceptions

---

# Errors in Python

- When Python detects an error in the program, it stops the program and prints an error message.
  - e.g. if the user enters `"three"`, Python shows `ValueError` when it calls `int()` and the rest of the program is never executed.

```python
x = input("enter a number: ")
print(f"the next number:{int(x)+1}")
print("bye")
```

---

# Types of Standard Errors

- <https://docs.python.org/3/library/exceptions.html#bltin-exceptions>
  - `SyntaxError`
  - `NameError`
  - `IndexError`
  - `TypeError`
  - `ValueError`
  - `ZeroDivisionError`
  - ...

---

# Exercises

- Start an interactive session of Python (the "shell") and write codes that generate various standard errors.

---

# Design Principle

- The standard Python error messages are to help the programmer detect the problems of the program during the development process.
- **Never let the user see those Python error messages!**

---

# Exception Handling

- But how are we supposed to deal with the errors?

---

# Exception Handling (1)

- You can use `if (... else)` statements to detect errors and handle them.

```python
x = input("enter a number: ")
if x.isnumeric():
    print(f"the next number:{int(x)+1}")
else:
    print("enter a numeric form")
```

---

# Exception Handling (2)

- Python provides an exception-handling mechanism through `try ... except` statements.

```python
x = input("enter a number: ")
try:
    print(f"the next number:{int(x)+1}")
except ValueError:
    print("enter a numeric form")
```

---

# Try ... Except

- Syntax

```python
try:
    <statements 1>
except <error type>:
    <statements 2>
<statements 3>
```

- Semantics
  - Try to execute `<statements 1>`, and if an error occurs, execute `<statements 2>`.
  - The program won't stop even if an error is detected, so `<statements 3>` will be executed.

---

# Try ... Except

- You can catch different types of errors with one try statement.

```python
try:
    <statements 1>
except ValueError:
    <statements 2>
except TypeError:
    <statements 3>
except NameError:
    <statements 4>
...
```

---

# Try ... Except

- If you don't specify the type of errors in the `except` statement, it will catch any type of error.

```python
try:
    <statements 1>
except:
    <statements 2>
...
```

---

# If vs. Try

- You can use `if...elif...else` statements to get the same effect of `try...except`.
- What are their pros and cons to handle errors?

---

# If vs. Try

- For specific errors: `if`
- For general errors: `try`

---

# Take-home

- **Always add exception handling to your software!**
- Test your program with all kinds of bad input and add appropriate `except` statements to catch errors.
- If you're not sure about what kind of errors would occur, at least add a bare `except` statement.

---

# Exercises

- Add appropriate `try .. except` statements to the programs that you made previously.

---

# Next Class

- Loop Structures
- Reading: [CL] Ch. 8 Loop Structures and Booleans

---
layout: section
---

# Extra Slides

---

# Conversation Agent

- Turing test (by Alan Turing, 1950)
  - if a human evaluator can tell the machine from the human through conversation
- Successful applications
  - ELIZA (by Joseph Weizenbaum, 1966)
  - ALICE (by Richard Wallace, 1995)

---

# Conversation Example

<div class="text-sm">

- **Human:** Men are all alike.
- **ELIZA:** IN WHAT WAY
- **Human:** They're always bugging us about something or other.
- **ELIZA:** CAN YOU THINK OF A SPECIFIC EXAMPLE
- **Human:** Well, my boyfriend made me come here.
- **ELIZA:** YOUR BOYFRIEND MADE YOU COME HERE
- **Human:** He say's I'm depressed much of the time.
- **ELIZA:** I AM SORRY TO HEAR YOU ARE DEPRESSED.
- **Human:** It's true. I'm unhappy.
- **ELIZA:** DO YOU THINK COMING HERE WILL HELP YOU NOT TO BE UNHAPPY

</div>

---

# `kr_case(word)`

- Define a function that returns the grammatical case of a given Korean word.
- E.g.
  - `kr_case("Hyunahka")` → `"nom"`
  - `kr_case("mikuki")` → `"nom"`

---

# Flowchart

- A flowchart is a diagram that represents a workflow.
- It shows the steps as boxes, and their order as arrows.
- Type of boxes
  - Oval: Start and End
  - Rectangle: Instruction
  - Diamond: Decision

---

# Mini Homework #2

- define a function `journal_title`
  - Input (string)
  - Iterate all words in the input
    - if the word is a function word,
      - lower the case
    - otherwise,
      - capitalize the word
    - add the word to output
  - Output (string)

---

# Announcement

- Thank you for the feedback about the course!
  - More programming during the class
  - A little more programming homework
- Even more exercises:
  - End of each chapter in the textbook

---

# Why "if-elif-else"?

- Why not just a series of simple decisions?
- (Try the code and see what happens)

```python
if x > 0:
    print("positive")
if x < 0:
    print("negative")
if x == 0:
    print("zero")
```

---

# Score to Letter Grade

- Suppose that you want to write a program that takes a score (up to 100) and turn that into a letter grade, following this scheme:
  - from 90 to 100: A
  - from 80 and less than 90: B
  - from 70 and less than 80: C
  - from 60 and less than 70: D
  - less than 60: F

---

# Boolean Expressions (5)

- The inherent Boolean value of the object is useful to check if it has meaningful content or not.

```python
x = input("enter a number: ")
if int(x):
    print("not zero")
else:
    print("zero")
```

---

# Multi-Way Decision

- Solution 1: multiple `elif` statements

```python
if <condition 1>:
    <statements 1>
elif <condition 2>:
    <statements 2>
elif <condition 3>:
    <statements 3>
...
else:
    <statements>
```

---

# Quiz

- Value of the Boolean expression?
  - `3 * 2 > 4`
  - `"a" > "b"`
  - `"a" < "B"`
  - `"Alice" < "Alison"`
  - `0 == 0.0`
  - `int(3.5) == 3`

---

# HW 5 - Functions

- Functions for modularizing programs
- `return` vs. `print()`
- `split()` vs. slicing
- Naming intermediate variables
- Docstrings for each function
  - parameters and returns must be specified!

---

# Exercises

<https://docs.google.com/forms/d/e/1FAIpQLScnlF68fvr80YnMUdO5X2zGebTXx-RRVoerPlGlGz2kZrw39Q/viewform?usp=sf_link>

---

# `sign()`

- Write a function that returns:
  - `"positive"` if the input number is a positive number
  - `"negative"` if the input number is a negative number
  - `"zero"` if the input number is 0

---

# Directions of Operators

- You can express the same Boolean expression using different relational operators:
  - `x < y`
  - `y > x`
- Recommendation: Use the same direction throughout your program
  - `<` and `<=` are more commonly used than `>` and `>=`
