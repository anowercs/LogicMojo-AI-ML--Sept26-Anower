# Python Exception Handling & File Handling

**Class Date:** 24 October  
**Topics:** Try-Except, Exception Handling, Raise, Else, File Handling, Reading and Writing Files, CSV Files and Pandas.

Beginner-friendly notes covering Python error handling and file operations with practical examples, explanations and exercises.

## 📌 Learning Objectives

By the end of this session, you should understand:

- What exceptions are and why they occur.
- How to use `try` and `except`.
- How to handle different types of exceptions.
- How to use `raise` to generate custom errors.
- How to use `else` and `finally`.
- How to create and manage files.
- How to read, write and append file content.
- How to handle file-related errors.
- How to read CSV files using Pandas.
- How to inspect and understand a dataset.

---

# PART 1: PYTHON EXCEPTION HANDLING

## 1. What is Exception Handling?

An **Exception** is an error that occurs while a Python program is running.

When an exception occurs, Python normally stops executing the remaining statements in that execution path.

Exception handling allows us to handle errors without unnecessarily terminating the program.

### Example 1: Division by Zero

```python
a = 10
b = 0

print(a / b)
```

**Output:**

```text
ZeroDivisionError: division by zero
```

**Explanation:**

- `a = 10` assigns 10 to variable `a`.
- `b = 0` assigns 0 to variable `b`.
- Python cannot divide a number by zero.
- Therefore, Python raises a `ZeroDivisionError`.

### Example 2: Handling an Exception Using try-except

```python
try:
    a = 10
    b = 0

    print(a / b)

except ZeroDivisionError:
    print("Can't divide by Zero")
```

**Output:**

```text
Can't divide by Zero
```

**Explanation:**

The `try` block contains code that might generate an exception.

The `except` block handles the exception if it occurs.

Execution:

1. Python enters the `try` block.
2. It attempts to calculate `10 / 0`.
3. A `ZeroDivisionError` occurs.
4. Python skips the remaining statements in the `try` block.
5. The matching `except` block executes.

The program does not display the original traceback.

### Example 3: try-except When No Exception Occurs

```python
try:
    a = 10
    b = 6

    print(a / b)

except ZeroDivisionError:
    print("Can't divide by Zero")
```

**Output:**

```text
1.6666666666666667
```

**Explanation:**

Here, the denominator is 6, not zero.

Therefore:

- The `try` block executes successfully.
- No exception occurs.
- The `except` block is skipped.
- The division result is displayed.

**Important:** An `except` block only executes when a matching exception occurs.

---

## 2. Common Types of Python Exceptions

Python provides different exception types for different errors.

| Exception | Meaning | Example |
|---|---|---|
| `ZeroDivisionError` | Dividing by zero | `10 / 0` |
| `ValueError` | Invalid value | `int("hello")` |
| `TypeError` | Incorrect operation between types | `"10" + 5` |
| `NameError` | Variable is not defined | `print(x)` |
| `IndexError` | Invalid List index | `[10, 20][5]` |
| `KeyError` | Dictionary key does not exist | `{"a": 1}["b"]` |
| `FileNotFoundError` | File does not exist | Opening a missing file |
| `FileExistsError` | File already exists | Creating an existing file using `x` |
| `NameError` | Referencing an undefined name | `print(username)` |

### Example 4: ValueError

```python
num = int("hello")

print(num)
```

**Output:**

```text
ValueError: invalid literal for int() with base 10: 'hello'
```

**Explanation:**

The `int()` function converts a valid numeric string into an integer.

For example:

```python
print(int("100"))  # Output: 100
```

But `"hello"` cannot be converted into an integer.

Therefore, Python raises a `ValueError`.

### Example 5: Handling ValueError

```python
try:
    number = int("hello")

except ValueError:
    print("Please enter a valid number")
```

**Output:**

```text
Please enter a valid number
```

**Explanation:**

The `except ValueError` block handles invalid integer conversion.

Instead of displaying a traceback, Python displays our custom message.

---

## 3. Handling Multiple Exceptions

Sometimes one program can generate different types of errors.

We can use multiple `except` blocks to handle them separately.

### Example 6: ZeroDivisionError and ValueError

```python
try:
    num = int(input("Enter a number: "))

    print(100 / num)

except ZeroDivisionError:
    print("Number cannot be Zero")

except ValueError:
    print("Please enter a valid number")
```

**Possible Output 1:**

```text
Enter a number: 0
Number cannot be Zero
```

**Possible Output 2:**

```text
Enter a number: hello
Please enter a valid number
```

**Possible Output 3:**

```text
Enter a number: 5
20.0
```

**Explanation:**

There are two possible exceptions:

1. `ValueError`: Happens when the user enters something that cannot be converted into an integer.
2. `ZeroDivisionError`: Happens when the user enters zero.

Each exception has its own handler.

---

## 4. The raise Keyword

The `raise` keyword allows us to generate an exception manually.

We use it when a value violates a condition or validation rule.

### Example 7: Raising a ValueError

```python
age = -5

if age < 0:
    raise ValueError("Age cannot be negative")
```

**Output:**

```text
ValueError: Age cannot be negative
```

**Explanation:**

- The age is `-5`.
- The condition `age < 0` is True.
- Python executes the `raise` statement.
- A `ValueError` is generated with our custom message.

### Example 8: Using raise with try-except

```python
age = -5

try:
    if age < 0:
        raise ValueError("Age cannot be negative")

except ValueError as e:
    print(e)
```

**Output:**

```text
Age cannot be negative
```

**Explanation:**

Here:

- `raise` generates the exception.
- `except ValueError` catches the exception.
- `as e` stores the exception object in variable `e`.
- `print(e)` displays the error message.

### Important: Understanding except ValueError(s)

The following code from the original class notes contains a mistake:

```python
except ValueError(s):
    print(s)
```

This is incorrect because `ValueError(s)` attempts to construct an exception rather than catch the exception and assign it to a variable.

**Correct syntax:**

```python
except ValueError as s:
    print(s)
```

Or:

```python
except ValueError as e:
    print(e)
```

Remember:

- `except ValueError:` catches the exception.
- `except ValueError as e:` catches it and stores the exception object in `e`.

### Example 9: Handling Multiple Custom Validations

```python
age = -5
name = ""

try:
    if age < 0:
        raise ValueError("Age cannot be negative")

    if name == "":
        raise ValueError("Username cannot be empty")

except ValueError as e:
    print(e)
```

**Output:**

```text
Age cannot be negative
```

**Explanation:**

The first condition is True, so Python raises the exception immediately.

The second condition is not reached.

To check both validations, we need to handle them separately or validate the inputs in sequence.

---

## 5. Real-World Example: Age Validation

### Example 10: Checking Voting Eligibility

```python
try:
    age = input("Please enter your age: ")

    if age.strip() == "":
        raise ValueError("Input cannot be empty")

    age = int(age)

    if age < 0:
        raise ValueError("Age cannot be negative")

    if age >= 18:
        print("Eligible to vote")

    else:
        print("Not Eligible to vote")

except ValueError as e:
    print(e)
```

**Possible Output 1:**

```text
Please enter your age: 25
Eligible to vote
```

**Possible Output 2:**

```text
Please enter your age: 15
Not Eligible to vote
```

**Possible Output 3:**

```text
Please enter your age:
Input cannot be empty
```

**Possible Output 4:**

```text
Please enter your age: -5
Age cannot be negative
```

**Possible Output 5:**

```text
Please enter your age: hello
invalid literal for int() with base 10: 'hello'
```

**Explanation:**

- `input()` accepts user input as a string.
- `strip()` removes whitespace from the beginning and end.
- If the input is empty, `raise ValueError` generates an exception.
- `int(age)` converts the age into an integer.
- Negative ages are rejected.
- Ages of 18 or above are eligible.
- Other valid ages are not eligible.

---

## 6. Positive and Negative Number Validation

### Example 11: Checking Even or Odd Numbers

```python
try:
    num = int(input("Please enter the number: "))

    if num <= 0:
        raise ValueError("The number is Negative or ZERO")

    if num % 2 == 0:
        print(f"{num} is an even number.")

    else:
        print(f"{num} is an odd number.")

except ValueError as e:
    print(e)
```

**Possible Output 1:**

```text
Please enter the number: 8
8 is an even number.
```

**Possible Output 2:**

```text
Please enter the number: 7
7 is an odd number.
```

**Possible Output 3:**

```text
Please enter the number: -5
The number is Negative or ZERO
```

**Possible Output 4:**

```text
Please enter the number: hello
invalid literal for int() with base 10: 'hello'
```

**Explanation:**

- `int()` converts user input into an integer.
- `num <= 0` checks whether the number is zero or negative.
- `raise ValueError` generates an exception for invalid numbers.
- `%` is the modulus operator.
- If `num % 2 == 0`, the number is even.
- Otherwise, it is odd.
- `f"{num}"` inserts the variable's value into the string.

**Important correction:** In the original class example, the output strings were written as `" {num} is a even number."`. Without an `f` prefix, Python prints `{num}` literally. Use an f-string to display the actual number.

---

# 7. Understanding try, except, else and finally

Python supports four important components of exception handling.

| Keyword | Purpose |
|---|---|
| `try` | Contains code that might generate an exception |
| `except` | Handles an exception |
| `else` | Executes when no exception occurs |
| `finally` | Executes whether an exception occurs or not |

### General Syntax

```python
try:
    # Code that might generate an exception

except ExceptionType:
    # Handle the exception

else:
    # Executes if no exception occurs

finally:
    # Executes in both cases
```

### Example 12: Using else

```python
try:
    num = int(input("Enter a number: "))

except ValueError:
    print("Invalid input")

else:
    print("You entered:", num)
```

**Output:**

```text
Enter a number: 25
You entered: 25
```

**Explanation:**

The `else` block executes only when the `try` block completes without an exception.

### Example 13: Using finally

```python
try:
    num = 10 / 2
    print(num)

except ZeroDivisionError:
    print("Cannot divide by zero")

finally:
    print("Program execution completed")
```

**Output:**

```text
5.0
Program execution completed
```

**Explanation:**

The `finally` block executes whether an exception occurs or not.

It is commonly used for cleanup operations.

---

# PART 2: PYTHON FILE HANDLING

## 8. What is File Handling?

File handling means creating, reading, writing, updating and managing files using Python.

We can use file handling to store information permanently instead of keeping everything only in program memory.

For example:
- Saving student information.
- Storing marks and results.
- Reading datasets.
- Saving application logs.
- Managing user records.

## 9. File Handling Modes

Python provides four commonly used file modes.

| Mode | Name | Description |
|---|---|---|
| `r` | Read | Opens an existing file for reading |
| `w` | Write | Creates a file or overwrites existing content |
| `a` | Append | Adds content at the end of a file |
| `x` | Exclusive creation | Creates a new file; raises FileExistsError if it already exists |

### Important Differences

**1. Read mode (`r`)**

- Reads existing file content.
- Raises `FileNotFoundError` if the file does not exist.
- Does not modify the file.

**2. Write mode (`w`)**

- Creates a file if it does not exist.
- Overwrites existing content if the file already exists.
- Be careful: previous content is lost.

**3. Append mode (`a`)**

- Adds new content at the end of the file.
- Creates the file if it does not exist.
- Preserves existing content.

**4. Exclusive creation mode (`x`)**

- Creates a new file.
- Raises `FileExistsError` if the file already exists.
- Does not overwrite an existing file.

---

## 10. Creating and Opening a File

### Example 14: Opening a File

```python
file = open("file.txt", "r")

content = file.read()

print(content)

file.close()
```

**Possible Output:**

```text
File handling:
    r - read an existing file
    w - write content
    a - append content
    x - create a new file
```

**Explanation:**

- `open()` opens a file.
- `"file.txt"` is the filename.
- `"r"` specifies read mode.
- `read()` reads the entire file content.
- `close()` closes the file.

**Important:** The file must already exist when using `r` mode.

### Example 15: Writing Content into a File

```python
file = open("file.txt", "w")

file.write("Python Basics")

file.close()
```

**Output:**

```text
No output displayed in the terminal.
```

**Content inside file.txt:**

```text
Python Basics
```

**Explanation:**

- `"w"` opens the file in write mode.
- `write()` writes content into the file.
- `close()` closes the file and ensures buffered content is flushed.

If `file.txt` already contains information, the previous content will be overwritten.

### Example 16: Appending Content to a File

```python
file = open("file.txt", "a")

file.write("\nThis is new line added through coding")

file.close()
```

**Content inside file.txt:**

```text
Python Basics
This is new line added through coding
```

**Explanation:**

- `"a"` opens the file in append mode.
- `write()` adds new content at the end.
- `\n` creates a new line.
- Existing content remains unchanged.

### Example 17: Creating a New File Using x Mode

```python
file = open("student.txt", "x")

file.write("Student Name: Aman")

file.close()
```

**Output:**

```text
No output displayed in the terminal.
```

**Content inside student.txt:**

```text
Student Name: Aman
```

If we run the same code again:

```python
file = open("student.txt", "x")
```

**Output:**

```text
FileExistsError: [Errno 17] File exists: 'student.txt'
```

**Explanation:**

The `x` mode only creates a new file.

It does not allow overwriting an existing file.

---

## 11. Understanding File read() and write()

Python provides different methods for working with file content.

| Method | Purpose |
|---|---|
| `read()` | Reads the entire file or a specified number of characters |
| `readline()` | Reads one line |
| `readlines()` | Returns all lines as a List |
| `write()` | Writes a string into a file |
| `writelines()` | Writes multiple strings into a file |
| `close()` | Closes the file |

### Example 18: Using read()

Assume `student.txt` contains:

```text
Name: Aman
Age: 21
Course: Python
```

Code:

```python
file = open("student.txt", "r")

content = file.read()

print(content)

file.close()
```

**Output:**

```text
Name: Aman
Age: 21
Course: Python
```

**Explanation:** `read()` reads all available content from the current file position.

### Example 19: Using readline()

```python
file = open("student.txt", "r")

print(file.readline())

file.close()
```

**Output:**

```text
Name: Aman
```

**Explanation:** `readline()` reads one line at a time.

### Example 20: Using readlines()

```python
file = open("student.txt", "r")

content = file.readlines()

print(content)

file.close()
```

**Output:**

```text
['Name: Aman\n', 'Age: 21\n', 'Course: Python\n']
```

**Explanation:**

`readlines()` returns all lines as a List.

The `\n` character represents the newline character.

### Example 21: Reading a File Line by Line

```python
file = open("student.txt", "r")

for line in file:
    print(line.strip())

file.close()
```

**Output:**

```text
Name: Aman
Age: 21
Course: Python
```

**Explanation:**

- The `for` loop iterates through each line.
- `strip()` removes surrounding whitespace, including the newline character.
- This is useful when processing large text files line by line.

---

## 12. Using with open() – Recommended Method

Instead of manually opening and closing files, Python provides a better approach.

### Example 22: Reading Using with open()

```python
with open("student.txt", "r") as file:
    content = file.read()
    print(content)
```

**Output:**

```text
Name: Aman
Age: 21
Course: Python
```

**Explanation:**

The `with open()` statement automatically closes the file when the block finishes.

We do not need to call `file.close()` manually.

### Example 23: Writing Using with open()

```python
with open("student.txt", "w") as file:
    file.write("Name: Priya\n")
    file.write("Age: 22\n")
    file.write("Course: Data Science\n")
```

**Content inside student.txt:**

```text
Name: Priya
Age: 22
Course: Data Science
```

**Explanation:**

Each `write()` statement adds a line to the file.

Because we use `w` mode, previous content is overwritten.

### Example 24: Appending Using with open()

```python
with open("student.txt", "a") as file:
    file.write("University: Sapienza\n")
```

**Content inside student.txt:**

```text
Name: Priya
Age: 22
Course: Data Science
University: Sapienza
```

**Explanation:** The append mode adds the new line without deleting previous content.

---

# PART 3: FILE HANDLING WITH EXCEPTION HANDLING

File operations can also generate exceptions.

For example:
- File does not exist.
- File already exists.
- Permission is denied.
- Invalid filename is provided.

We can use `try-except` to handle these situations.

## 13. Handling FileNotFoundError

### Example 25: Reading a Missing File

```python
try:
    with open("unknown.txt", "r") as file:
        content = file.read()
        print(content)

except FileNotFoundError:
    print("File not found")
```

**Output:**

```text
File not found
```

**Explanation:**

The file `"unknown.txt"` does not exist.

Python raises `FileNotFoundError`, which is handled by the `except` block.

## 14. Handling FileExistsError

### Example 26: Creating an Existing File

```python
try:
    with open("student.txt", "x") as file:
        file.write("New Student")

except FileExistsError:
    print("File already exists")
```

**Output:**

```text
File already exists
```

**Explanation:**

The file already exists, so Python raises `FileExistsError`.

The exception is caught and a friendly message is displayed.

## 15. Handling Multiple File Exceptions

### Example 27: Reading a File Safely

```python
try:
    with open("student.txt", "r") as file:
        content = file.read()

        if content.strip() == "":
            print("File is empty")

        else:
            print(content)

except FileNotFoundError:
    print("File does not exist")
```

**Possible Output 1:**

```text
Name: Aman
Age: 21
```

**Possible Output 2:**

```text
File is empty
```

**Possible Output 3:**

```text
File does not exist
```

**Explanation:**

- The program attempts to open the file.
- If the file is missing, `FileNotFoundError` is handled.
- If the file exists, its content is read.
- `strip()` checks whether the file contains only whitespace.
- An empty file produces the message `"File is empty"`.

---

# PART 4: PANDAS AND CSV FILE HANDLING

## 16. Introduction to Pandas

**Pandas** is a Python library used for data manipulation and analysis.

It is especially useful for working with structured data such as:
- CSV files.
- Excel files.
- Tabular datasets.
- Data analysis.
- Data cleaning.

### Installing Pandas

```bash
pip install pandas
```

### Importing Pandas

```python
import pandas as pd
```

**Explanation:**

- `import` loads the Pandas library.
- `as pd` creates an alias.
- We use `pd` instead of writing `pandas` repeatedly.

## 17. Reading a CSV File

### Example 28: Using read_csv()

```python
import pandas as pd

df = pd.read_csv("CUST_AZ12.csv")

print(df)
```

**Explanation:**

- `read_csv()` reads a CSV file.
- `"CUST_AZ12.csv"` is the filename.
- `df` stores the data as a Pandas DataFrame.

A **DataFrame** is a two-dimensional tabular data structure containing rows and columns.

## 18. Viewing the First Five Rows Using head()

```python
df.head()
```

**Explanation:**

`head()` displays the first five rows by default.

We can also specify how many rows we want:

```python
df.head(10)
```

This displays the first 10 rows.

## 19. Viewing the Last Five Rows Using tail()

```python
df.tail()
```

**Explanation:**

`tail()` displays the last five rows by default.

We can specify the number of rows:

```python
df.tail(10)
```

This displays the last 10 rows.

### Example Output from the Class Dataset

```text
             CID       BDATE   GEN
18479  AW00029479  1969-06-30   NaN
18480  AW00029480  1977-05-06   NaN
18481  AW00029481  1965-07-04   NaN
18482  AW00029482  1964-09-01   NaN
18483  AW00029483  1965-06-06   NaN
```

**Explanation:**

- `CID` represents customer ID.
- `BDATE` represents birth date.
- `GEN` represents gender.
- `NaN` indicates a missing value.

## 20. Understanding describe()

```python
df.describe()
```

**Explanation:**

The `describe()` method generates descriptive statistics for a DataFrame.

For numeric columns, it normally provides:

- Count
- Mean
- Standard deviation
- Minimum
- 25th percentile
- 50th percentile
- 75th percentile
- Maximum

For object or string columns, it provides:

- Count
- Unique
- Top
- Frequency

### Output from the Class Dataset

| Statistic | CID | BDATE | GEN |
|---|---:|---:|---|
| count | 18484 | 18484 | 17012 |
| unique | 18484 | 6152 | 8 |
| top | NASAW00011000 | 1980-10-14 | Male |
| freq | 1 | 18 | 8608 |

**Explanation:**

| Term | Meaning |
|---|---|
| count | Number of non-missing values |
| unique | Number of distinct values |
| top | Most frequently occurring value |
| freq | Frequency of the top value |

For example:

- `CID` has 18,484 unique values.
- `BDATE` has 6,152 unique values.
- `GEN` has 17,012 non-missing values.
- `Male` appears 8,608 times.

**Important:** `describe()` output depends on the data types and the Pandas version. The output above represents the object/string summary from the class dataset.

## 21. Understanding info()

```python
df.info()
```

**Output from the Class Dataset:**

```text
<class 'pandas.DataFrame'>
RangeIndex: 18484 entries, 0 to 18483

Data columns (total 3 columns):

#   Column  Non-Null Count  Dtype
--- ------  --------------  -----
0   CID     18484 non-null  str
1   BDATE   18484 non-null  str
2   GEN     17012 non-null  str

dtypes: str(3)
memory usage: 911.8 KB
```

**Explanation:**

The `info()` method provides a summary of the DataFrame.

| Information | Meaning |
|---|---|
| RangeIndex | Total rows and index range |
| Data columns | Total number of columns |
| Non-Null Count | Number of non-missing values |
| Dtype | Data type of each column |
| Memory usage | Approximate memory used by the DataFrame |

**Important observation:**

The `GEN` column contains:

- Total rows: 18,484
- Non-null values: 17,012

Missing values:

```python
print(18484 - 17012)  # Output: 1472
```

Therefore, the `GEN` column contains 1,472 missing values.

## 22. Important Pandas Methods: Quick Reference

| Method | Purpose |
|---|---|
| `pd.read_csv()` | Reads a CSV file |
| `df.head()` | Displays the first five rows |
| `df.tail()` | Displays the last five rows |
| `df.describe()` | Provides descriptive statistics |
| `df.info()` | Displays DataFrame information |
| `df.shape` | Returns rows and columns |
| `df.columns` | Returns column names |
| `df.isnull().sum()` | Counts missing values |
| `df.dtypes` | Displays column data types |

### Additional Examples

```python
print(df.shape)
# Output: (18484, 3)

print(df.columns)
# Output: Index(['CID', 'BDATE', 'GEN'], dtype='object')

print(df.isnull().sum())
```

**Possible output:**

```text
CID         0
BDATE       0
GEN      1472
```

---

# PART 5: PRACTICE ASSIGNMENTS

The following 20 questions are designed to strengthen your understanding of Exception Handling and File Handling.

Try to solve them independently before checking other resources.

## LEVEL 1 – Exception Handling Basics

### Q1. Age Validation

Take age as input from the user.

Requirements:

1. If the input is empty, raise a `ValueError`.
2. If the age is negative, raise another `ValueError`.
3. Use `try-except` to handle the errors.
4. If the age is 18 or above, print `"Eligible to vote"`.
5. Otherwise, print `"Not eligible to vote"`.

### Q2. Positive Number Checker

Ask the user to enter a number.

Requirements:

1. Handle invalid numeric input using `try-except`.
2. If the number is zero or negative, raise a `ValueError`.
3. If it is positive, check whether it is even or odd.
4. Display the result.

### Q3. Username Validation

Take a username as input.

Requirements:

1. If the username is empty, raise a `ValueError`.
2. If the username contains fewer than five characters, raise a `ValueError`.
3. Handle the exception using `try-except`.
4. If the username is valid, print `"Username accepted"`.

### Q4. Division Calculator

Take two numbers as input.

Requirements:

1. Handle invalid numeric input using `try-except`.
2. If the second number is zero, raise a `ZeroDivisionError`.
3. Otherwise, divide the first number by the second.
4. Use `else` to display the result only when no exception occurs.

### Q5. Student Marks Validation

Take marks as input.

Requirements:

1. Convert the input into an integer.
2. Handle invalid integer input.
3. If marks are below 0 or above 100, raise a `ValueError`.
4. If marks are at least 40, print `"Pass"`.
5. Otherwise, print `"Fail"`.

---

## LEVEL 2 – File Creation and Writing

### Q6. Create a Student File

Use `"x"` mode to create a file named `student.txt`.

Requirements:

1. Take the student's name, age and course as input.
2. Write these details into the file.
3. Handle `FileExistsError` if the file already exists.

Expected file content:

```text
Name: Aman
Age: 21
Course: Python
```

### Q7. Write Student Records

Use `"w"` mode to create or overwrite `students.txt`.

Requirements:

1. Take details of three students.
2. Collect each student's name and marks.
3. Write each student's information on a separate line.
4. Handle appropriate input errors using `try-except`.

Expected file content:

```text
Aman - 85
Priya - 92
Rahul - 78
```

### Q8. Append Student Records

Use `"a"` mode to add a new student's information to the existing `students.txt` file.

Requirements:

1. Take the student's name and marks.
2. If marks are below 0 or above 100, raise a `ValueError`.
3. Append valid student information to the file.
4. Do not add invalid records.

### Q9. Read a File Safely

Ask the user to enter a filename.

Requirements:

1. Open the file using `"r"` mode.
2. Display the file contents.
3. Handle `FileNotFoundError`.
4. If the file is empty, print `"File is empty"`.

### Q10. Number Storage in a File

Take five numbers from the user and write them to `numbers.txt` using `"w"` mode.

Requirements:

1. Accept five numbers.
2. Handle invalid numeric input.
3. If a number is negative, raise a `ValueError`.
4. Store only valid, non-negative numbers in the file.

Expected file content for valid inputs:

```text
10
20
30
40
50
```

---

## LEVEL 3 – File Handling and Exception Handling Together

### Q11. Search for a Student

Read `students.txt` using `"r"` mode.

Requirements:

1. Ask the user to enter a student name.
2. Search for the name in the file.
3. If the name exists, print `"Student found"`.
4. Otherwise, print `"Student not found"`.
5. Handle `FileNotFoundError`.

### Q12. File Creation with Validation

Ask the user to enter a filename.

Requirements:

1. If the filename is empty, raise a `ValueError`.
2. Otherwise, use `"x"` mode to create the file.
3. Handle both `ValueError` and `FileExistsError`.

### Q13. Append Only Passing Students

Take a student's name and marks as input.

Requirements:

1. If marks are outside the range 0–100, raise a `ValueError`.
2. If marks are 40 or above, append the student's details to `passed_students.txt` using `"a"` mode.
3. Otherwise, print `"Student failed; record not added"`.

### Q14. Count Lines in a File

Ask the user for a filename and read it using `"r"` mode.

Requirements:

1. Count the number of non-empty lines in the file.
2. Handle `FileNotFoundError`.
3. If the file contains no non-empty lines, print `"No records found"`.

### Q15. File Copy Program

Create a Python program to copy the contents of one file into another.

Requirements:

1. Read the content from `source.txt`.
2. Write the content into `destination.txt`.
3. Handle `FileNotFoundError` if the source file does not exist.
4. Display `"File copied successfully"` after successful completion.

---

## LEVEL 4 – Advanced Practice

### Q16. Student Result Management

Create a program that accepts five students' names and marks.

Requirements:

1. Validate that marks are between 0 and 100.
2. Raise a `ValueError` for invalid marks.
3. Use `try-except` to handle invalid input.
4. If marks are at least 40, classify the student as Pass.
5. Otherwise, classify the student as Fail.
6. Save the results in `results.txt`.

Expected file content:

```text
Aman - 85 - Pass
Priya - 92 - Pass
Rahul - 35 - Fail
```

### Q17. Word Counter in a File

Read a file named `paragraph.txt`.

Requirements:

1. Read all the text.
2. Count the total number of words.
3. Count the total number of characters.
4. Handle `FileNotFoundError`.
5. Display the results.

Hint:

```python
words = content.split()
```

### Q18. Login System Using File Handling

Create a simple login system using `users.txt`.

Requirements:

1. Store usernames and passwords in a file.
2. Ask the user to enter a username and password.
3. Read the file and check whether the credentials match.
4. Print `"Login successful"` if they match.
5. Otherwise, print `"Invalid username or password"`.
6. Handle `FileNotFoundError`.

Note: This is a learning exercise. Real applications should never store passwords in plain text.

### Q19. Number Analysis Using File Handling

Create a program that:

1. Takes five numbers from the user.
2. Handles invalid numeric input.
3. Rejects negative numbers using `ValueError`.
4. Stores valid numbers in `numbers.txt`.
5. Reads the numbers from the file.
6. Calculates the total, average, maximum and minimum.

Example output for numbers 10, 20, 30, 40 and 50:

```text
Total: 150
Average: 30.0
Maximum: 50
Minimum: 10
```

### Q20. Complete Student Management System

Build a simple student management program using Python File Handling and Exception Handling.

Requirements:

1. Create a file named `students.txt`.
2. Add student records using append mode.
3. Read and display all student records.
4. Search for a student by name.
5. Validate student marks between 0 and 100.
6. Handle invalid numeric input.
7. Handle `FileNotFoundError`.
8. Handle `FileExistsError` where appropriate.
9. Allow multiple students to be added.
10. Display a message when no records are available.

**Suggested menu:**

```text
===== STUDENT MANAGEMENT SYSTEM =====

1. Add Student
2. View All Students
3. Search Student
4. Exit

Enter your choice:
```

This exercise combines the main concepts from the entire session.

---

# PART 6: QUICK REVISION

## Exception Handling

| Concept | Purpose |
|---|---|
| `try` | Executes potentially risky code |
| `except` | Handles exceptions |
| `else` | Runs when no exception occurs |
| `finally` | Runs whether an exception occurs or not |
| `raise` | Manually generates an exception |
| `as e` | Stores the caught exception object |

## File Handling

| Mode | Purpose | Existing file |
|---|---|---|
| `r` | Read | Reads existing content |
| `w` | Write | Overwrites content |
| `a` | Append | Preserves and adds content |
| `x` | Create | Raises FileExistsError |

## Important File Methods

| Method | Purpose |
|---|---|
| `open()` | Opens a file |
| `read()` | Reads entire content |
| `readline()` | Reads one line |
| `readlines()` | Reads all lines into a List |
| `write()` | Writes content |
| `writelines()` | Writes multiple strings |
| `close()` | Closes a file |
| `with open()` | Manages file opening and closing automatically |

## Important Pandas Methods

| Method | Purpose |
|---|---|
| `pd.read_csv()` | Reads CSV files |
| `head()` | First five rows |
| `tail()` | Last five rows |
| `describe()` | Statistical summary |
| `info()` | Dataset information |
| `shape` | Number of rows and columns |
| `columns` | Column names |
| `isnull().sum()` | Missing-value count |

---


---

**Next Learning Direction:** Python modules, libraries, CSV data processing and practical data manipulation for Data Science and Machine Learning.

*Maintained as part of my Data Science, Machine Learning & AI learning journey.*
