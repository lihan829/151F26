---
theme: seriph
background: '#fff8e6'
themeConfig:
  primary: '#2ca4d3'
title: Dictionaries
info: false
# class: text-center
fonts:
  sans: Lexend
  serif: Roboto Slab
  mono: Fira Code
---

# Dictionaries

### LCD151 Lecture 
### Instructor: Han Li
<h3>{{ new Date().toLocaleDateString('en-US', {
  year: 'numeric',
  month: 'long',
  day: 'numeric'
}) }}</h3>


---

# Why Dictionaries?

A dictionary is like a list, but more general.

- In a **list**, indices have to be integers
- In a **dictionary**, keys can be (almost) any type

We'll use dictionaries to:

- Count unique words in a book and how often each appears
- Solve word puzzles (in the exercises)
- Write remarkably efficient algorithms

---

# A Dictionary is a Mapping

A list maps integer indices to values. What if we want to go the *other* direction — look up a word to get a number?

```python
lst = ['zero', 'one', 'two']
lst[1]
```
```
'one'
```

Lists can't do a reverse lookup. Dictionaries can.

```python
numbers = {}      # curly braces = empty dictionary
numbers['zero'] = 0
numbers
```
```
{'zero': 0}
```

---

# Building Up a Dictionary

```python
numbers['one'] = 1
numbers['two'] = 2
numbers
```
```
{'zero': 0, 'one': 1, 'two': 2}
```

Each assignment adds an **item**: a **key** (`'zero'`) paired with a **value** (`0`).

```python
numbers['two']    # look up with the bracket operator
```
```
2
```

```python
numbers['three']  # missing key →
```
```
KeyError: 'three'
```

`len(numbers)` returns the number of **items** — here, `3`.

---
layout: two-cols
---

# The State Diagram

A dictionary maps keys to values — mathematically, a **mapping**.

Each number word "maps to" the corresponding integer.

The box is labeled `dict`; each item is a key with an arrow pointing to its value. Quotation marks show the keys are strings, not variable names.

::right::

<div class="pl-8 pt-16">

```
 dict
┌─────────────────────┐
│ 'zero' ───────▶ 0    │
│ 'one'  ───────▶ 1    │
│ 'two'  ───────▶ 2    │
└─────────────────────┘
```

</div>

---

# 10.2 Creating Dictionaries

Build one all at once, instead of item by item:

```python
numbers = {'zero': 0, 'one': 1, 'two': 2}
```

Key : value, separated by commas, wrapped in `{ }`.

Or use the `dict` function:

```python
empty = dict()
empty
```
```
{}
```

```python
numbers_copy = dict(numbers)   # make a copy
numbers_copy
```
```
{'zero': 0, 'one': 1, 'two': 2}
```

It's often useful to copy a dictionary before an operation that modifies it.

---

# 10.3 The `in` Operator

`in` tells you whether something is a **key**:

```python
'one' in numbers
```
```
True
```

It does **not** check values:

```python
1 in numbers
```
```
False
```

To check values, use `.values()`:

```python
1 in numbers.values()
```
```
True
```

---

# Why `in` is Fast on Dictionaries

Dictionaries are stored in a **hash table** — `in` takes about the same time no matter how many items there are.

Goal: find pairs of words that are reverses of each other (`stressed` / `desserts`).

```python
word_list = open('words.txt').read().split()
len(word_list)          # 113,783 words
```

```python
def too_slow():
    count = 0
    for word in word_list:
        if reverse_word(word) in word_list:  # in on a LIST
            count += 1
    return count
```

Checking `in` on a list scans from the start every time — roughly
`len(word_list) ** 2` ≈ **13 billion** comparisons. This takes over a minute.

---

# The Dictionary Version

```python
word_dict = {}
for word in word_list:
    word_dict[word] = 1     # values don't matter — only the keys
```

```python
def much_faster():
    count = 0
    for word in word_dict:
        if reverse_word(word) in word_dict:  # in on a DICT
            count += 1
    return count
```

<v-click>

**Result:** less than 1/100th of a second — about **10,000× faster**.

Finding an element in a list takes time proportional to the list's length.
Finding a key in a dictionary is almost **constant time**.

</v-click>

---

# 10.4 A Collection of Counters

Count how many times each letter appears in a string.

```python
counter = {}
counter['a'] = 1        # first time we see 'a'
counter['a'] += 1       # seen it again → increment
counter
```
```
{'a': 2}
```

```python
def value_counts(string):
    counter = {}
    for letter in string:
        if letter not in counter:
            counter[letter] = 1
        else:
            counter[letter] += 1
    return counter
```

```python
value_counts('brontosaurus')
```
```
{'b': 1, 'r': 2, 'o': 2, 'n': 1, 't': 1, 's': 2, 'a': 1, 'u': 2}
```

---

# 10.5 Looping and Dictionaries

A `for` loop over a dictionary traverses its **keys**.

```python
counter = value_counts('banana')
# {'b': 1, 'a': 3, 'n': 2}

for key in counter:
    print(key)
```
```
b
a
n
```

Loop over `.values()` to get values; loop over keys and look each one up to get both:

```python
for key in counter:
    value = counter[key]
    print(key, value)
```
```
b 1
a 3
n 2
```

---

# 10.6 Lists and Dictionaries

A dictionary **value** can be a list:

```python
d = {4: ['r', 'o', 'u', 's']}
```

But a list can **not** be a dictionary **key**:

```python
letters = list('abcd')
d[letters] = 4
```
```
TypeError: unhashable type: 'list'
```

<v-click>

### Why? Hashability

A **hash function** turns a value into an integer (a *hash value*) used to store and find keys.

This only works if the key is **immutable** — its hash value must never change.
Lists (and dictionaries) are mutable, so they can't be keys. They *can* be values.

</v-click>

---

# 10.7 Accumulating a List

Loop through one collection while building another — here, filtering `word_dict` for **palindromes**.

```python
def is_palindrome(word):
    return reverse_word(word) == word

palindromes = []
for word in word_dict:
    if is_palindrome(word):
        palindromes.append(word)
```

`palindromes` is an **accumulator** — a variable that collects results during a computation.

```python
palindromes[:10]
```
```
['aa', 'aba', 'aga', 'aha', 'ala', 'alula', 'ama', 'ana', 'anna', 'ava']
```

---

# Filtering Further

Keep only palindromes with 7+ letters:

```python
long_palindromes = []
for word in palindromes:
    if len(word) >= 7:
        long_palindromes.append(word)
```
```
['deified', 'halalah', 'reifier', 'repaper',
 'reviver', 'rotator', 'sememes']
```

Selecting some elements and omitting others like this is called **filtering**.

---

# 10.8 Memos

`fibonacci(n)` gets dramatically slower as `n` grows — because it recomputes the same values over and over.

```python
def fibonacci(n):
    if n == 0:
        return 0
    if n == 1:
        return 1
    return fibonacci(n-1) + fibonacci(n-2)
```

The call graph for `fibonacci(4)` re-invokes `fibonacci(0)` and `fibonacci(1)`
many times — and it only gets worse as `n` grows.

**Fix:** store results we've already computed in a dictionary — a **memo**.

---

# Memoized Fibonacci

```python
known = {0: 0, 1: 1}

def fibonacci_memo(n):
    if n in known:
        return known[n]

    res = fibonacci_memo(n-1) + fibonacci_memo(n-2)
    known[n] = res
    return res
```

`known` remembers every Fibonacci number already computed.
If `n` is already known, return it immediately — otherwise compute, **store**, and return.

<v-click>

| Version | Time for n = 40 |
|---|---|
| `fibonacci(40)` | ~30 seconds |
| `fibonacci_memo(40)` | ~30 microseconds |

**≈ 1,000,000× faster**

</v-click>

---

# 10.9 Debugging Large Datasets

- **Scale down the input** — test with the first 10 lines, or the smallest example that reproduces the bug, then grow it back
- **Check summaries and types** — print a dict's length or a list's total instead of the whole dataset; a wrong *type* is a common bug source
- **Write self-checks**
  - *Sanity check*: does the result fall in a plausible range?
  - *Consistency check*: do two different computations agree?
- **Format the output** — e.g. the `pprint` module ("pretty print") for readable structured output

Time spent building scaffolding saves time spent debugging.

---

# 10.10 Glossary

<div class="text-sm grid grid-cols-2 gap-x-8">
<div>

**dictionary** — an object containing key-value pairs (items)

**item** — a key-value pair in a dictionary

**key** — the first part of an item

**value** — the second part of an item

**mapping** — a relationship where each element of one set corresponds to an element of another

**hash table** — a structure for efficient key lookup

</div>
<div>

**hashable** — immutable types (int, float, str) are hashable; mutable types (list, dict) are not

**hash function** — computes an integer used to locate a key

**accumulator** — a loop variable that builds up a result

**filtering** — looping through a sequence, keeping some elements and dropping others

**call graph** — shows every frame created during execution, with caller → callee arrows

**memo** — a computed value stored to avoid recomputing it

</div>
</div>

---

# 10.11 Exercises

1. **Ask a virtual assistant** — why must dictionary keys be hashable? How do you build a `set` from a list and check membership?
2. **Concise `value_counts`** — rewrite it using `dict.get(key, default)` to eliminate the `if` statement
3. **`has_duplicates(sequence)`** — return `True` if any element appears more than once
4. **`find_repeats(counter)`** — return the keys whose count is greater than 1
5. **`add_counters(counter1, counter2)`** — merge two count-dictionaries, summing shared keys
6. **`is_interlocking(word)`** — can the word be split into two words using `word[0::2]` and `word[1::2]`? (e.g. `"schooled"` → `"shoe"` + `"cold"`)

---
class: text-center
---

# Key Takeaways

<div class="text-left inline-block">

- A dictionary maps **keys → values**, and keys can be almost any hashable type
- `in` on a dictionary is **fast** (hash table) — `in` on a list is **slow** (linear scan)
- Dictionaries are perfect for **counting**, **accumulating**, and **memoizing**
- Keys must be **hashable** (immutable); values can be anything, including lists

</div>

<div class="pt-12 opacity-70">
Think Python, 3rd Edition — Chapter 10 — Allen B. Downey
</div>
