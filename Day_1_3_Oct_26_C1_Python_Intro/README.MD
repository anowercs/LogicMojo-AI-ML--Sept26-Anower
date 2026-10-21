# Python Basics — Learning Notes

Beginner-friendly notes covering variables, data types, arithmetic operators, string indexing, string methods, and common string checks.

## 1. Variables

A **variable** is a name used to store a value.

```python
customer_name = "Mahipal"
customer_age = 16
monthly_spending = 1000000000000000

print(customer_name)
print(customer_age)
print(monthly_spending)
```

- `"Mahipal"` is a string (`str`).
- `16` is an integer (`int`).
- `1000000000000000` is also an integer (`int`).

## 2. Assigning Multiple Variables

Python lets you assign values to multiple variables in one line.

```python
a, b = 10, 15

print(a)  # 10
print(b)  # 15
```

Here, `a` receives `10` and `b` receives `15`.

## 3. Checking a Variable's Type

Use the built-in `type()` function to check the data type of a value.

```python
a = 16
b = 16.5
c = "abc"
d = True

print(type(a))  # <class 'int'>
print(type(b))  # <class 'float'>
print(type(c))  # <class 'str'>
print(type(d))  # <class 'bool'>
```

| Example value | Data type | Meaning |
|---|---|---|
| `16` | `int` | Integer / whole number |
| `16.5` | `float` | Number with a decimal part |
| `"abc"` | `str` | Text / string |
| `True` | `bool` | Boolean value: `True` or `False` |

## 4. Arithmetic Operators

Python provides operators for common mathematical calculations.

```python
a = 20
b = 6

print(a + b)   # Addition:        26
print(a - b)   # Subtraction:    14
print(a * b)   # Multiplication: 120
print(a / b)   # Division:       3.3333333333333335
print(a // b)  # Floor division: 3
print(a % b)   # Remainder:      2
print(a ** b)  # Exponentiation: 64000000
```

| Operator | Name | Example | Result |
|---|---|---|---:|
| `+` | Addition | `20 + 6` | `26` |
| `-` | Subtraction | `20 - 6` | `14` |
| `*` | Multiplication | `20 * 6` | `120` |
| `/` | Division | `20 / 6` | `3.3333333333333335` |
| `//` | Floor division | `20 // 6` | `3` |
| `%` | Modulo / remainder | `20 % 6` | `2` |
| `**` | Exponentiation | `2 ** 3` | `8` |

### Floor division: `//`

Floor division divides and rounds the result **down to the nearest whole number**.

```python
print(7 / 2)   # 3.5
print(7 // 2)  # 3
```

For negative values, “down” means toward negative infinity:

```python
print(-7 // 2)  # -4
```

### Exponentiation: `**`

The `**` operator raises a number to a power.

```python
print(2 ** 3)     # 8  (2 × 2 × 2)
print(5 ** 2)     # 25 (5 squared)
print(pow(2, 3))  # 8
```

`pow(base, exponent)` is a built-in alternative to `base ** exponent`.

## 5. String Indexing and Slicing

A **string** is a sequence of characters. Python indexing starts at `0` from the left. Negative indexes count backward from the end, with `-1` representing the last character.

```python
a = "welcome to logicmojo"

print(a[-2])     # j
print(a[5])      # m
print(a[0:4])    # welc
print(a[1:4])    # elc
print(a[-10:-4]) #  logic
print(a[-5:-1])  # cmoj
```

### Indexing

```text
String:  w e l c o m e   t o   l o g i c m o j o
Index:   0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19
```

- `a[5]` returns the character at index `5`: `m`.
- `a[-2]` returns the second character from the end: `j`.

### Slicing: `string[start:stop]`

A slice includes the `start` index but **excludes** the `stop` index.

```python
a = "welcome to logicmojo"

print(a[0:4])    # welc
print(a[1:4])    # elc
print(a[-5:-1])  # icmo
```

For `a[0:4]`, Python returns indexes `0`, `1`, `2`, and `3` — not index `4`.

## 6. String Manipulation

Python strings have built-in methods for changing letter case, trimming whitespace, and replacing text.

```python
name = "   mahipal sINgh  "

print(name.upper())                   # "   MAHIPAL SINGH  "
print(name.lower())                   # "   mahipal singh  "
print(name.title())                   # "   Mahipal Singh  "
print(name.strip())                   # "mahipal sINgh"
print(name.replace("sINgh", "singh")) # "   mahipal singh  "
```

| Method | What it does |
|---|---|
| `.upper()` | Converts letters to uppercase |
| `.lower()` | Converts letters to lowercase |
| `.title()` | Makes the first letter of each word uppercase |
| `.strip()` | Removes whitespace from the beginning and end |
| `.replace(old, new)` | Replaces occurrences of `old` with `new` |

**Important:** These methods return a new string; they do not modify the original string in place.

To remove outer spaces and standardize the name:

```python
name = "   mahipal sINgh  "
clean_name = name.strip().title()

print(clean_name)  # Mahipal Singh
```

## 7. Useful String Checks and Search Methods

```python
email = "mahipal.singh@shaktimaan.com"

print(email.find("."))           # 7
print(email.count("m"))          # 3
print(email.startswith("mahi"))  # True
print(email.endswith(".com"))    # True
print("mahipal" in email)        # True
```

| Method / expression | Meaning | Example result |
|---|---|---|
| `.find(".")` | Returns the index of the first matching substring, or `-1` if not found | `7` |
| `.count("m")` | Counts non-overlapping occurrences of `"m"` | `3` |
| `.startswith("mahi")` | Checks whether the string begins with the given text | `True` |
| `.endswith(".com")` | Checks whether the string ends with the given text | `True` |
| `"mahipal" in email` | Checks whether the substring exists in the string | `True` |

## 🧠 Quick Revision

- Variables store values.
- Use `type(value)` to inspect a value's data type.
- `//` is floor division; `%` gives the remainder.
- `**` performs exponentiation; `pow()` is an alternative.
- String indexing starts at `0`; negative indexing starts from the end.
- Slicing `text[start:stop]` includes `start` but excludes `stop`.
- `.strip()` removes whitespace only from the beginning and end.
- String methods return new strings.
- `.find()` returns `-1` if the text is not found.
- `in`, `.startswith()`, and `.endswith()` are useful for string checks.

## ✍️ Practice Exercises

1. Create variables for your name, age, and favorite programming language. Print each value.
2. Assign `25` and `4` to two variables. Print their sum, product, floor division, remainder, and exponentiation.
3. Create a string `"Python Programming"` and print its first character, last character, first six characters, and last three characters.
4. Given `name = "   aLICE johnson  "`, print the trimmed name, uppercase version, lowercase version, and title-case version.
5. Given `email = "student@example.com"`, check whether it starts with `"student"`, ends with `".com"`, and contains `"@"`.
