# Python Functions: `*args`, `**kwargs`, and Lambda

Beginner-friendly notes on passing multiple arguments to functions and writing short anonymous functions with `lambda`.

## 1. `*args` — Pass Multiple Positional Arguments

Use `*args` when a function should accept any number of positional arguments. The name `args` is a convention; the `*` is what matters.

```python
def abc(*num):
    return sum(num)

print(abc(5, 10, 7, 20))  # 42
```

### How it works

- `*num` collects the positional arguments into a **tuple**.
- `sum(num)` adds the numbers together.
- You can pass zero, one, or many numbers.

```python
print(abc(4, 6))          # 10
print(abc(1, 2, 3, 4, 5)) # 15
print(abc())              # 0
```

Although the parameter is named `num` here, it can be called `*args` to follow the common Python convention:

```python
def add_all(*args):
    return sum(args)
```

## 2. `**kwargs` — Pass Multiple Keyword Arguments

Use `**kwargs` when a function should accept any number of named arguments.

```python
def introduce(**details):
    print(details)

introduce(name="Mahipal", age=16, language="Python")
```

**Output**
```text
{'name': 'Mahipal', 'age': 16, 'language': 'Python'}
```

### How it works

- `**details` collects keyword arguments into a **dictionary**.
- Each argument has a key and a value, such as `"name": "Mahipal"`.
- The name `details` is a variable name; `**kwargs` is the common convention.

A common mistake is writing `print(deatils)` instead of `print(details)`. Variable names must match exactly.

You can access individual values like this:

```python
def introduce(**details):
    print("Name:", details.get("name"))
    print("Age:", details.get("age"))

introduce(name="Mahipal", age=16)
```

## 3. Use `*args` and `**kwargs` Together

A function can accept positional arguments and keyword arguments at the same time.

```python
def order_food(*items, **details):
    print("Food items:", items)
    print("Extra details:", details)

order_food(
    "Pizza",
    "Burger",
    "French Fries",
    drink="Coca-Cola",
    payment="Cash"
)
```

**Output**
```text
Food items: ('Pizza', 'Burger', 'French Fries')
Extra details: {'drink': 'Coca-Cola', 'payment': 'Cash'}
```

In this example:

- `"Pizza"`, `"Burger"`, and `"French Fries"` are collected in the `items` tuple.
- `drink="Coca-Cola"` and `payment="Cash"` are collected in the `details` dictionary.

## 4. Lambda Functions

A **lambda function** is a small anonymous function written in one expression. It is useful when a short function is needed without defining it with `def`.

```python
add_lambda = lambda a, b: a + b

print(add_lambda(2, 3))  # 5
```

Equivalent function using `def`:

```python
def add(a, b):
    return a + b

print(add(2, 3))  # 5
```

### Lambda syntax

```python
lambda parameters: expression
```

- `lambda` starts the function.
- `parameters` are the input values.
- The expression is evaluated and returned automatically.
- A lambda expression contains one expression, not a block of statements.

## 5. More Lambda Examples

### Example 1: Square a number

```python
square = lambda n: n ** 2

print(square(5))  # 25
print(square(9))  # 81
```

### Example 2: Multiply two numbers

```python
multiply = lambda a, b: a * b

print(multiply(4, 3))  # 12
```

### Example 3: Check whether a number is even

```python
is_even = lambda n: n % 2 == 0

print(is_even(8))  # True
print(is_even(7))  # False
```

### Example 4: Find the larger number

```python
maximum = lambda a, b: a if a > b else b

print(maximum(10, 6))  # 10
print(maximum(3, 9))   # 9
```

### Example 5: Convert a name to uppercase

```python
to_upper = lambda name: name.upper()

print(to_upper("mahipal"))  # MAHIPAL
```

### Example 6: Calculate a price after tax

```python
price_with_tax = lambda price, tax_rate: price * (1 + tax_rate)

print(price_with_tax(100, 0.22))  # 122.0
```

Here, `0.22` represents a 22% tax rate.

### Example 7: Sort words by length

```python
words = ["python", "AI", "machine", "code"]

words.sort(key=lambda word: len(word))

print(words)  # ['AI', 'code', 'python', 'machine']
```

The `key` function tells `sort()` to compare each word by its length.

### Example 8: Use `map()` to transform values

```python
numbers = [1, 2, 3, 4]

squares = list(map(lambda n: n ** 2, numbers))

print(squares)  # [1, 4, 9, 16]
```

`map()` applies the lambda function to each item. A list comprehension is often easier to read:

```python
squares = [n ** 2 for n in numbers]
```

### Example 9: Use `filter()` to select values

```python
numbers = [1, 2, 3, 4, 5, 6]

evens = list(filter(lambda n: n % 2 == 0, numbers))

print(evens)  # [2, 4, 6]
```

This keeps only the numbers for which the lambda returns `True`.

## 6. Quick Comparison

| Feature | `*args` | `**kwargs` | `lambda` |
|---|---|---|---|
| Purpose | Accept many positional arguments | Accept many named arguments | Create a short anonymous function |
| Collected / written as | Tuple | Dictionary | One expression |
| Example | `def f(*args): ...` | `def f(**kwargs): ...` | `lambda x: x * 2` |

## 🧠 Quick Revision

- `*args` collects extra positional arguments into a tuple.
- `**kwargs` collects extra keyword arguments into a dictionary.
- The names `args`, `kwargs`, `num`, and `details` are variable names; the `*` and `**` symbols provide the special behavior.
- A lambda function is a short anonymous function with one expression.
- Use `lambda` for small, simple operations; use `def` for more complex logic or when a descriptive function name improves readability.

## ✍️ Practice Exercises

1. Write `sum_numbers(*args)` that returns the sum of any number of numbers.
2. Write `show_profile(**details)` that prints a person's name, age, and country.
3. Write `order_food(*items, **details)` and call it with three foods, a drink, and a payment method.
4. Create a lambda that converts Celsius to Fahrenheit: `F = C * 9 / 5 + 32`.
5. Create a lambda that returns `True` if a number is positive.
6. Sort a list of names by length using `sort(key=lambda name: len(name))`.
