# Python Programming – Live Practice Session

**Date:** 31 October 2026  
**Session Type:** Fully Live Practice & Coding Assessment  
**Total Questions:** 40  
**Time Allowed:** 3 minutes per question  
**Total Duration:** 120 minutes  
**Maximum Marks:** 40  

---

## 1. Session Overview

This session was dedicated to hands-on Python programming practice. All 40 questions were designed to help participants apply Python concepts through practical coding exercises, problem-solving, and industry-related scenarios.

The exercises covered fundamental Python programming, data structures, functions, exception handling, file processing, decorators, regular expressions, object-oriented programming, and real-world data-processing tasks.

The main objective was to strengthen coding skills, improve logical thinking, and develop the ability to solve practical programming problems independently.

## 2. General Instructions

1. Attempt all 40 questions.
2. Each question carries 1 mark.
3. You will get 3 minutes to solve each question.
4. Write clean, readable, and properly indented Python code.
5. Unless specified otherwise, use Python 3.
6. Do not use external libraries unless explicitly mentioned.
7. Explain your logic briefly wherever required.
8. Test your code mentally with the given examples before submitting.
9. Handle edge cases wherever applicable.

### Submission Instructions

- Submit your answers under the respective reply thread in the Slack channel named **Technical Discussion**.
- Include your full name and question numbers.
- Do not post answers as separate messages in the main channel.
- Reply within the designated assessment thread.

---

# 3. Python Programming Practice Questions

## Section A: Python Fundamentals

**Q1. Product Bill with GST**

Create a Python program that accepts the price of a product and the quantity purchased. Calculate and display the total bill amount, including 18% GST.

**Q2. Celsius to Fahrenheit**

Write a Python program that accepts a temperature in Celsius and converts it into Fahrenheit using the appropriate mathematical formula.

**Q3. Python Arithmetic Operators**

What will be the output of the following code? Explain why.

```python
a = 10
b = 3

print(a / b)
print(a // b)
print(a % b)
print(a ** b)
```

**Q4. Positive, Negative, or Zero**

Write a Python program that accepts a number from the user and checks whether it is positive, negative, or zero.

**Q5. Leap Year Checker**

Write a program to check whether a given year is a leap year or not. Consider all leap-year conditions correctly.

## Section B: Strings, Lists, and Functions

**Q6. List Comprehension**

Given a list of numbers:

```python
numbers = [10, 25, 30, 45, 50, 65, 70]
```

Create a new list containing only numbers divisible by both 5 and 10 using list comprehension.

**Q7. Count Vowels**

Write a Python program to count the number of vowels in a given string without using external libraries.

**Q8. Discount Calculator**

Create a function named `calculate_discount()` that accepts the original price and discount percentage and returns the final price after applying the discount.

**Q9. Mutable and Immutable Objects**

What will be the output of the following code? Explain the difference between mutable and immutable objects.

```python
a = [10, 20, 30]
b = a

b.append(40)

x = 100
y = x
y = 200

print(a)
print(b)
print(x)
print(y)
```

**Q10. Multiplication Table**

Write a Python program that accepts a number `N` and prints its multiplication table from 1 to 10 using a `for` loop.

**Q11. Palindrome Checker**

Write a Python program to check whether a given string is a palindrome without using the built-in reverse function.

Example:

```text
Input: madam
Output: Palindrome
```

**Q12. Modify a List In-Place**

Given the following list:

```python
numbers = [10, 20, 30, 40, 50, 60]
```

Remove all elements greater than 30 without creating a second list. Explain your approach.

**Q13. Second-Largest Unique Number**

Write a program to find the second-largest unique number in a list without using the `sort()` or `sorted()` functions.

Example:

```text
Input: [10, 20, 40, 40, 30, 50]
Output: 40
```

**Q14. Average Using *args**

Write a Python function that accepts any number of numeric arguments using `*args` and returns their average.

Example:

```python
calculate_average(10, 20, 30, 40)

# Output: 25.0
```

## Section C: Sets, Loops, Dictionaries, and Lambda

**Q15. Set Operations**

Given two lists:

```python
list1 = [1, 2, 3, 4, 5]
list2 = [4, 5, 6, 7, 8]
```

Find:

- Common elements.
- Elements present only in the first list.
- All unique elements from both lists.

Use sets.

**Q16. Star Pattern**

Write a Python program to generate the following pattern for `N = 5`.

```text
*
**
***
****
*****
```

Use nested loops.

**Q17. Employee Salary Analysis**

Create a dictionary containing employee names and their salaries.

Write a program to:

- Find the employee with the highest salary.
- Calculate the average salary.
- Display employees earning more than the average salary.

**Q18. Lambda Function and Sorting**

Write a lambda function to sort the following list of tuples based on the second element.

```python
students = [
    ("Amit", 85),
    ("Rahul", 72),
    ("Neha", 95),
    ("Priya", 88)
]
```

Expected output:

```python
[
    ('Rahul', 72),
    ('Amit', 85),
    ('Priya', 88),
    ('Neha', 95)
]
```

**Q19. Count Even, Odd, and Zero**

Write a Python function that accepts a list of numbers and returns a dictionary containing the count of even numbers, odd numbers, and zeros.

Example:

```python
Input: [0, 1, 2, 3, 4, 5, 0]

Output:
{
    'even': 2,
    'odd': 3,
    'zero': 2
}
```

**Q20. break, continue, and pass**

Explain the difference between `break`, `continue`, and `pass` with a practical Python example demonstrating all three statements.

## Section D: Exception Handling, Files, and Advanced Python

**Q21. Banking Application – Withdrawal**

You are developing a simple banking application.

Write a function `withdraw()` that:

- Accepts account balance and withdrawal amount.
- Raises an error if the withdrawal amount is negative.
- Raises an error if the withdrawal amount exceeds the available balance.
- Returns the updated balance if the transaction is successful.

Use appropriate exception handling.

**Q22. CSV File – Department Salary Analysis**

Write a Python program to read a CSV file named `employees.csv` containing the following columns:

```text
Employee_ID,Name,Department,Salary
```

Calculate the average salary department-wise and display the department with the highest average salary.

**Q23. JSON Configuration Parser**

You are building a configuration parser for an application.

Given the following JSON-style Python dictionary:

```python
config = {
    "database": {
        "host": "localhost",
        "port": 5432
    },
    "application": {
        "debug": True,
        "version": "1.0"
    }
}
```

Write Python code to safely retrieve the database port. If the port key is missing, return `3306` as the default value.

**Q24. Execution-Time Decorator**

Write a Python decorator named `execution_time` that measures how long a function takes to execute.

Apply this decorator to a function that calculates the sum of numbers from 1 to 1,000,000.

**Q25. Login Function Using **kwargs**

Create a function named `login()` that accepts any number of keyword arguments using `**kwargs`.

The function should:

- Accept username and password.
- Validate whether both are provided.
- Display the remaining optional parameters.
- Return a success or failure message.

**Q26. Group Employees by Department**

Given the following list of dictionaries:

```python
employees = [
    {"name": "Amit", "salary": 50000, "department": "IT"},
    {"name": "Neha", "salary": 70000, "department": "HR"},
    {"name": "Raj", "salary": 60000, "department": "IT"},
    {"name": "Priya", "salary": 80000, "department": "HR"}
]
```

Write a program to group employees department-wise and calculate the total salary for each department.

**Q27. Caching System**

You are developing a simple caching system.

Implement a function that stores previously calculated results in a dictionary. If the same input is received again, return the cached result instead of calculating it again.

Demonstrate your implementation using a function that calculates the square of a number.

**Q28. Transaction Analysis**

Write a Python program that accepts a list of transactions:

```python
transactions = [
    {"id": 1, "amount": 500, "status": "success"},
    {"id": 2, "amount": 300, "status": "failed"},
    {"id": 3, "amount": 700, "status": "success"},
    {"id": 4, "amount": 200, "status": "success"}
]
```

Calculate:

- Total successful transaction amount.
- Number of failed transactions.
- Average amount of successful transactions.

**Q29. Flatten a Nested List**

Write a program to flatten the following nested list into a single list.

```python
nested_list = [
    [1, 2, 3],
    [4, 5],
    [6, 7, 8, 9]
]
```

Expected output:

```python
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

Solve this using list comprehension.

**Q30. File Processing Application**

You are building a file-processing application.

Write a Python program that:

- Opens a text file.
- Counts the total number of lines, words, and characters.
- Handles the situation where the file does not exist.
- Ensures the file is properly closed even if an exception occurs.

## Section E: Industry-Based Practical Scenarios

**Q31. API Response Processing**

You receive the following API response:

```python
api_response = {
    "status": "success",
    "data": [
        {"user_id": 101, "name": "Amit", "age": 25, "active": True},
        {"user_id": 102, "name": "Neha", "age": 17, "active": True},
        {"user_id": 103, "name": "Raj", "age": 32, "active": False},
        {"user_id": 104, "name": "Priya", "age": 28, "active": True}
    ]
}
```

Write a reusable function that extracts only active users whose age is greater than or equal to 18.

Your function should also handle missing keys safely.

**Q32. Data Quality Validation**

You are working with a customer dataset:

```python
customers = [
    {"id": 1, "name": "Amit", "email": "amit@gmail.com", "age": 25},
    {"id": 2, "name": "", "email": "invalid_email", "age": -5},
    {"id": 3, "name": "Neha", "email": "neha@gmail.com", "age": 30},
    {"id": 4, "name": None, "email": "raj@gmail.com", "age": 150}
]
```

Write a validation function that identifies invalid records based on these rules:

- Customer name cannot be empty or `None`.
- Email must contain `@` and a valid-looking domain.
- Age must be between 18 and 100.

Return two separate lists: valid records and invalid records.

**Q33. Inventory Management**

You are developing an inventory management system.

Given:

```python
inventory = {
    "Laptop": {"price": 50000, "stock": 10},
    "Mobile": {"price": 20000, "stock": 5},
    "Tablet": {"price": 15000, "stock": 0}
}
```

Implement a function `purchase_product()` that accepts product name and quantity.

The function should:

- Check whether the product exists.
- Check whether sufficient stock is available.
- Update the stock after a successful purchase.
- Calculate and return the total purchase amount.
- Handle invalid quantities appropriately.

**Q34. Log File Analysis**

You are working as a Python developer responsible for monitoring application logs.

A log file contains entries in this format:

```text
2026-10-31 09:00:00 INFO Application started
2026-10-31 09:01:00 ERROR Database connection failed
2026-10-31 09:02:00 WARNING High memory usage
2026-10-31 09:03:00 ERROR API timeout
2026-10-31 09:04:00 INFO Application stopped
```

Write a Python program to:

- Read the log file.
- Count INFO, WARNING, and ERROR messages.
- Extract and display only ERROR messages.
- Handle missing files gracefully.

**Q35. Regular Expressions and Data Extraction**

You receive customer information in an unstructured text format:

```python
text = """
Contact Amit at amit@gmail.com or call 9876543210.
Contact Neha at neha@yahoo.com or call 9123456780.
Invalid contact: abc@com
"""
```

Using Python regular expressions:

- Extract all valid-looking email addresses.
- Extract all 10-digit mobile numbers.
- Count the total number of email addresses found.

**Q36. Retry Mechanism for API Calls**

You are developing an application that communicates with an external API.

Write a decorator named `retry()` that:

- Accepts the maximum number of retry attempts.
- Executes the decorated function.
- Retries execution when an exception occurs.
- Returns the result when successful.
- Raises the last exception if all attempts fail.

Demonstrate the decorator using a sample function that fails twice and succeeds on the third attempt.

**Q37. Transaction Processing and Error Handling**

You receive the following transaction data:

```python
transactions = [
    {"id": 1, "amount": 1000, "type": "credit"},
    {"id": 2, "amount": 500, "type": "debit"},
    {"id": 3, "amount": -200, "type": "credit"},
    {"id": 4, "amount": 300, "type": "debit"},
    {"id": 5, "amount": 700, "type": "credit"}
]
```

Write a reusable function to calculate the final account balance.

Requirements:

- Start with an initial balance of 5000.
- Add credit transactions.
- Subtract debit transactions.
- Ignore transactions with negative amounts.
- Handle invalid transaction types.
- Return the final balance and the number of invalid transactions.

**Q38. Object-Oriented Design – Employee Payroll**

You are developing an employee payroll management system.

Create a base class `Employee` with:

- Employee ID.
- Employee name.
- Basic salary.
- A method `calculate_salary()`.

Create two child classes:

- `FullTimeEmployee`: Receives a 20% bonus on basic salary.
- `ContractEmployee`: Receives a 10% deduction from basic salary.

Override the `calculate_salary()` method in both child classes.

Create objects of both classes and demonstrate inheritance and polymorphism.

**Q39. Data Loader and File Processing**

You are building a reusable data-loading utility for an analytics application.

Create a function `load_data()` that:

- Accepts a file path.
- Supports both CSV and JSON formats.
- Uses the appropriate Python module to read the file.
- Handles unsupported file extensions.
- Handles missing files and malformed JSON.
- Returns the loaded data in a consistent Python data structure wherever possible.

Demonstrate the function using sample CSV and JSON files.

**Q40. End-to-End Data Processing Pipeline**

You are working as a Python developer in a data analytics team.

You receive the following sales records:

```python
sales = [
    {"order_id": 1, "customer": "Amit", "amount": 1500, "status": "completed"},
    {"order_id": 2, "customer": "Neha", "amount": 2000, "status": "pending"},
    {"order_id": 3, "customer": "Raj", "amount": 3000, "status": "completed"},
    {"order_id": 4, "customer": "Priya", "amount": -500, "status": "completed"},
    {"order_id": 5, "customer": "Amit", "amount": 2500, "status": "completed"},
    {"order_id": 6, "customer": "Neha", "amount": 1000, "status": "completed"}
]
```

Develop a reusable Python data-processing pipeline that:

1. Validates each sales record.
2. Rejects records with missing customer names or non-positive amounts.
3. Processes only completed transactions.
4. Calculates total completed sales.
5. Calculates total sales per customer.
6. Identifies the highest revenue-generating customer.
7. Returns valid processed records and rejected records separately.
8. Uses appropriate functions, dictionaries, loops, and exception handling.

Your solution should be modular, reusable, and easy to extend for a real-world analytics application.

---

# 4. Concepts Practised

The live session covered practical applications of the following Python concepts:

| Area | Topics |
|---|---|
| Fundamentals | Variables, input, output, operators |
| Conditional logic | `if`, `elif`, `else`, leap-year conditions |
| Loops | `for`, nested loops, multiplication tables |
| Strings | Vowels, palindrome, regular expressions |
| Lists | List comprehension, filtering, flattening |
| Tuples | Tuple sorting |
| Sets | Union, intersection, difference |
| Dictionaries | Grouping, counting, caching, nested data |
| Functions | Reusable functions, return values |
| Arguments | `*args`, `**kwargs` |
| Functional programming | Lambda functions, decorators |
| Exception handling | `try`, `except`, raising errors |
| File handling | Text files, CSV, JSON, log files |
| Data processing | Validation, aggregation, filtering |
| OOP | Classes, inheritance, polymorphism |

# 5. Final Submission Reminder

Submit all 40 answers under the assessment thread in the Slack channel: **Technical Discussion**.

Ensure that your submission contains:

- Your full name.
- Question numbers (Q1–Q40).
- Python code for each question.
- Brief explanations wherever necessary.

**Time Management:** 3 minutes per question. Total assessment duration: 120 minutes.

---

## 6. Learning Objective

The purpose of this fully live practice session was to move beyond theoretical understanding and apply Python programming concepts to practical problems.

The exercises encourage participants to:

- Write code independently.
- Improve problem-solving and logical thinking.
- Understand how Python concepts work together.
- Handle errors and edge cases.
- Build reusable functions and modular solutions.
- Develop confidence in solving industry-oriented programming tasks.

**All the best! Happy Coding!**

*LogicMojo – Python Programming Practice | 31 October 2026*
