# Python Data Structures: Dictionary, Set Operations & Dictionary Comprehension

**Class Date:** 18 October  
**Topics:** Python Dictionary, Dictionary Methods, Set Symmetric Difference, `zip()`, Dictionary Comprehension and Nested Dictionary.

Beginner-friendly notes covering Dictionary creation, accessing values, adding and updating elements, removing entries, iteration, built-in methods, merging dictionaries and practical examples.

---

# 1. Python Dictionary – Introduction

A **Dictionary** is a mutable collection that stores information in **key-value pairs**.

Each element consists of:
- **Key:** Identifies the information.
- **Value:** Stores the actual information.

### Dictionary Syntax

```python
dictionary_name = {
    "key1": "value1",
    "key2": "value2"
}
```

Example:

```python
student = {
    "name": "Aman",
    "age": 21,
    "marks": 85,
    "city": "Jaipur"
}

print(student)
```

**Output:**

```text
{'name': 'Aman', 'age': 21, 'marks': 85, 'city': 'Jaipur'}
```

### Dictionary Properties

| Property | Dictionary |
|---|---|
| Syntax | `{key: value}` |
| Ordered | Yes |
| Mutable | Yes |
| Duplicate keys | No |
| Duplicate values | Yes |
| Indexing | By key |
| Mixed data types | Yes |

**Important:**
- Dictionaries preserve insertion order.
- Dictionary keys must be unique.
- Values can be duplicated.
- Dictionaries are mutable, so we can add, update and delete elements.
- Keys must be hashable, such as strings, numbers or tuples containing hashable elements.

---

# 2. Python Dictionary: All Methods and Operations

## Example 1: Creating a Dictionary

```python
student = {
    "name": "Aman",
    "age": 21,
    "marks": 85,
    "city": "Jaipur"
}

print(student)
```

**Output:**

```text
{'name': 'Aman', 'age': 21, 'marks': 85, 'city': 'Jaipur'}
```

**Explanation:**

We created a Dictionary called `student`.

It contains four key-value pairs:

- `"name"` → `"Aman"`
- `"age"` → `21`
- `"marks"` → `85`
- `"city"` → `"Jaipur"`

Each key identifies its corresponding value.

## Example 2: Checking the Type

```python
print(type(student))
```

**Output:**

```text
<class 'dict'>
```

**Explanation:** `type()` returns the data type of a variable. Here, it confirms that `student` is a Dictionary.

## Example 3: Creating an Empty Dictionary

```python
empty_dict = {}

print(empty_dict)
```

**Output:**

```text
{}
```

**Explanation:** `{}` creates an empty Dictionary.

Alternatively:

```python
empty_dict = dict()

print(empty_dict)  # Output: {}
```

**Important:** An empty Set is created using `set()`, not `{}`.

## Example 4: Creating a Dictionary Using dict()

```python
student2 = dict(name="Priya", age=22, marks=92)

print(student2)
```

**Output:**

```text
{'name': 'Priya', 'age': 22, 'marks': 92}
```

**Explanation:**

The `dict()` constructor creates a Dictionary.

Instead of writing curly brackets and key-value pairs, we can pass keyword arguments directly.

Here:
- `name` is the key and `"Priya"` is the value.
- `age` is the key and `22` is the value.
- `marks` is the key and `92` is the value.

## Example 5: Creating a Dictionary Using zip()

```python
names = ["Aman", "Priya", "Rahul"]
marks = [85, 92, 78]

student_marks = dict(zip(names, marks))

print(student_marks)
```

**Output:**

```text
{'Aman': 85, 'Priya': 92, 'Rahul': 78}
```

**Explanation:**

The `zip()` function combines corresponding elements from two or more iterables.

Step by step:

1. `names` contains three names.
2. `marks` contains three marks.
3. `zip(names, marks)` combines corresponding elements.
4. `dict()` converts those pairs into a Dictionary.

The resulting pairs are:

| Key | Value |
|---|---:|
| Aman | 85 |
| Priya | 92 |
| Rahul | 78 |

**Remember:** If the iterables have different lengths, `zip()` stops when the shortest iterable is exhausted.

## Example 6: Accessing a Value Using Its Key

```python
student = {
    "name": "Aman",
    "age": 21,
    "marks": 85,
    "city": "Jaipur"
}

print(student["name"])
print(student["marks"])
```

**Output:**

```text
Aman
85
```

**Explanation:**

We can access a Dictionary value directly using its key inside square brackets.

- `student["name"]` returns `"Aman"`.
- `student["marks"]` returns `85`.

If the requested key does not exist, Python raises a `KeyError`.

## Example 7: Accessing a Value Using get()

```python
print(student.get("name"))
```

**Output:**

```text
Aman
```

**Explanation:**

The `get()` method retrieves a value using its key.

It works similarly to square-bracket access, but it does not raise a `KeyError` when a key is missing.

## Example 8: Getting a Missing Key with get()

```python
print(student.get("grade"))
```

**Output:**

```text
None
```

**Explanation:**

The Dictionary does not contain the key `"grade"`.

Therefore, `get()` returns `None` instead of raising an error.

## Example 9: Providing a Default Value Using get()

```python
print(student.get("grade", "Not Available"))
```

**Output:**

```text
Not Available
```

**Explanation:**

We can provide a default value as the second argument of `get()`.

If the key does not exist, Python returns `"Not Available"`.

**Difference:**

```python
print(student.get("grade"))                   # None
print(student.get("grade", "Not Available"))  # Not Available
```

## Example 10: Adding a New Key-Value Pair

```python
student["grade"] = "A"

print(student)
```

**Output:**

```text
{'name': 'Aman', 'age': 21, 'marks': 85, 'city': 'Jaipur', 'grade': 'A'}
```

**Explanation:**

We can add a new key-value pair by assigning a value to a new key.

Here, `"grade"` does not exist, so Python adds it to the Dictionary.

## Example 11: Updating an Existing Value

```python
student["marks"] = 95

print(student)
```

**Output:**

```text
{'name': 'Aman', 'age': 21, 'marks': 95, 'city': 'Jaipur', 'grade': 'A'}
```

**Explanation:**

The key `"marks"` already exists.

By assigning `95`, we replace its previous value, `85`.

This demonstrates that Dictionaries are mutable.

## Example 12: Updating Multiple Entries Using update()

```python
student.update({
    "age": 22,
    "city": "Delhi"
})

print(student)
```

**Output:**

```text
{'name': 'Aman', 'age': 22, 'marks': 95, 'city': 'Delhi', 'grade': 'A'}
```

**Explanation:**

The `update()` method can update multiple key-value pairs simultaneously.

- `"age"` changes from 21 to 22.
- `"city"` changes from Jaipur to Delhi.

If a key does not exist, `update()` adds it.

## Example 13: Using setdefault() for a Missing Key

```python
student.setdefault("country", "India")

print(student)
```

**Output:**

```text
{'name': 'Aman', 'age': 22, 'marks': 95, 'city': 'Delhi', 'grade': 'A', 'country': 'India'}
```

**Explanation:**

The `setdefault()` method checks whether a key exists.

If the key does not exist, it inserts the key with the specified default value.

Here, `"country"` does not exist, so Python adds `"country": "India"`.

## Example 14: Using setdefault() for an Existing Key

```python
student.setdefault("marks", 0)

print(student)
```

**Output:**

```text
{'name': 'Aman', 'age': 22, 'marks': 95, 'city': 'Delhi', 'grade': 'A', 'country': 'India'}
```

**Explanation:**

The `"marks"` key already exists with the value `95`.

Therefore, `setdefault()` does not replace it with `0`.

**Difference between update() and setdefault():**

| Method | Behaviour |
|---|---|
| `update()` | Adds new keys or replaces existing values |
| `setdefault()` | Adds a missing key but preserves an existing value |

## Example 15: Finding the Number of Key-Value Pairs

```python
print(len(student))
```

**Output:**

```text
6
```

**Explanation:**

The `len()` function returns the total number of key-value pairs in the Dictionary.

## Example 16: Checking Whether a Key Exists

```python
print("name" in student)
```

**Output:**

```text
True
```

**Explanation:**

The `in` operator checks whether a particular key exists in the Dictionary.

## Example 17: Checking Whether a Key Does Not Exist

```python
print("salary" not in student)
```

**Output:**

```text
True
```

**Explanation:**

The `not in` operator checks whether a particular key is absent.

Since `"salary"` does not exist, the result is `True`.

## Example 18: Checking Whether a Value Exists

```python
print("Aman" in student.values())
```

**Output:**

```text
True
```

**Explanation:**

By default, `in` checks Dictionary keys, not values.

To check whether a particular value exists, we use `values()`.

Here, `"Aman"` exists among the Dictionary values.

## Example 19: Getting All Keys Using keys()

```python
print(student.keys())
```

**Output:**

```text
dict_keys(['name', 'age', 'marks', 'city', 'grade', 'country'])
```

**Explanation:**

The `keys()` method returns a view containing all Dictionary keys.

## Example 20: Getting All Values Using values()

```python
print(student.values())
```

**Output:**

```text
dict_values(['Aman', 22, 95, 'Delhi', 'A', 'India'])
```

**Explanation:**

The `values()` method returns a view containing all Dictionary values.

## Example 21: Getting All Key-Value Pairs Using items()

```python
print(student.items())
```

**Output:**

```text
dict_items([('name', 'Aman'), ('age', 22), ('marks', 95), ('city', 'Delhi'), ('grade', 'A'), ('country', 'India')])
```

**Explanation:**

The `items()` method returns all key-value pairs as tuples.

Each pair contains one key and its corresponding value.

## Example 22: Converting Keys into a List

```python
print(list(student.keys()))
```

**Output:**

```text
['name', 'age', 'marks', 'city', 'grade', 'country']
```

**Explanation:**

`keys()` returns a Dictionary view.

Using `list()` converts that view into a normal List.

## Example 23: Converting Values into a List

```python
print(list(student.values()))
```

**Output:**

```text
['Aman', 22, 95, 'Delhi', 'A', 'India']
```

**Explanation:**

`values()` returns all values. We use `list()` to convert them into a List.

## Example 24: Converting Items into a List

```python
print(list(student.items()))
```

**Output:**

```text
[('name', 'Aman'), ('age', 22), ('marks', 95), ('city', 'Delhi'), ('grade', 'A'), ('country', 'India')]
```

**Explanation:**

`items()` returns key-value pairs.

Converting it into a List gives a List of Tuples.

## Example 25: Iterating Through Dictionary Keys

```python
for key in student:
    print(key)
```

**Output:**

```text
name
age
marks
city
grade
country
```

**Explanation:**

When we directly iterate through a Dictionary, Python returns its keys.

We do not need to write `student.keys()` explicitly.

## Example 26: Iterating Through Dictionary Values

```python
for value in student.values():
    print(value)
```

**Output:**

```text
Aman
22
95
Delhi
A
India
```

**Explanation:**

The `values()` method allows us to iterate through the values without accessing the keys.

## Example 27: Iterating Through Key-Value Pairs

```python
for key, value in student.items():
    print(key, ":", value)
```

**Output:**

```text
name : Aman
age : 22
marks : 95
city : Delhi
grade : A
country : India
```

**Explanation:**

The `items()` method returns each key-value pair.

Using two variables, `key` and `value`, we can unpack each pair during iteration.

This is especially useful when processing structured data.

## Example 28: Removing an Entry Using pop()

```python
removed_value = student.pop("age")

print(removed_value)
print(student)
```

**Output:**

```text
22
{'name': 'Aman', 'marks': 95, 'city': 'Delhi', 'grade': 'A', 'country': 'India'}
```

**Explanation:**

The `pop()` method removes a specified key and returns its associated value.

Here:
- `"age"` is removed.
- Its value `22` is stored in `removed_value`.
- The remaining Dictionary no longer contains `"age"`.

## Example 29: Using pop() with a Default Value

```python
print(student.pop("salary", "Not Found"))
```

**Output:**

```text
Not Found
```

**Explanation:**

The key `"salary"` does not exist.

By providing `"Not Found"` as the second argument, Python returns that default value instead of raising a `KeyError`.

## Example 30: Removing the Last Inserted Pair Using popitem()

```python
removed_item = student.popitem()

print(removed_item)
print(student)
```

**Output:**

```text
('country', 'India')
{'name': 'Aman', 'marks': 95, 'city': 'Delhi', 'grade': 'A'}
```

**Explanation:**

The `popitem()` method removes and returns the last inserted key-value pair.

Here, `"country": "India"` is the last remaining inserted pair.

## Example 31: Deleting an Entry Using del

```python
del student["city"]

print(student)
```

**Output:**

```text
{'name': 'Aman', 'marks': 95, 'grade': 'A'}
```

**Explanation:**

The `del` keyword removes a specified key and its associated value.

Unlike `pop()`, `del` does not return the removed value.

## Example 32: Copying a Dictionary Using copy()

```python
original = {"name": "Aman", "marks": 85}

copied = original.copy()

copied["marks"] = 95

print(original)
print(copied)
```

**Output:**

```text
{'name': 'Aman', 'marks': 85}
{'name': 'Aman', 'marks': 95}
```

**Explanation:**

The `copy()` method creates a shallow copy of the Dictionary.

When we change the copied Dictionary's top-level `"marks"` value, the original Dictionary remains unchanged.

## Example 33: Creating a Dictionary Using fromkeys()

```python
subjects = ["Python", "SQL", "Excel"]

subject_status = dict.fromkeys(subjects, "Pending")

print(subject_status)
```

**Output:**

```text
{'Python': 'Pending', 'SQL': 'Pending', 'Excel': 'Pending'}
```

**Explanation:**

The `fromkeys()` method creates a new Dictionary using elements from an iterable as keys.

The second argument specifies a common value for all keys.

Here, every subject receives the value `"Pending"`.

## Example 34: Creating a Dictionary Using Dictionary Comprehension

```python
squares = {x: x**2 for x in range(1, 6)}

print(squares)
```

**Output:**

```text
{1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
```

**Explanation:**

Dictionary comprehension allows us to create a Dictionary in a single line.

Syntax:

```python
{key: value for item in iterable}
```

Here:

- `range(1, 6)` generates numbers from 1 to 5.
- `x` becomes the Dictionary key.
- `x**2` calculates the square of each number.

The resulting Dictionary contains each number as a key and its square as a value.

## Example 35: Dictionary Comprehension with a Condition

```python
marks = {
    "Aman": 85,
    "Priya": 92,
    "Rahul": 65,
    "Neha": 78
}

high_scorers = {
    name: score
    for name, score in marks.items()
    if score >= 80
}

print(high_scorers)
```

**Output:**

```text
{'Aman': 85, 'Priya': 92}
```

**Explanation:**

We want to select students who scored at least 80 marks.

Step by step:

1. `marks.items()` returns the name and marks of each student.
2. `name, score` extracts the key and value.
3. `if score >= 80` checks the condition.
4. Only matching students are included in `high_scorers`.

Result:

| Student | Marks | Selected? |
|---|---:|---|
| Aman | 85 | Yes |
| Priya | 92 | Yes |
| Rahul | 65 | No |
| Neha | 78 | No |

This is an example of filtering data using Dictionary comprehension.

## Example 36: Nested Dictionary

A **Nested Dictionary** means a Dictionary inside another Dictionary.

```python
students = {
    "S101": {"name": "Aman", "marks": 85},
    "S102": {"name": "Priya", "marks": 92}
}

print(students)
```

**Output:**

```text
{
    'S101': {'name': 'Aman', 'marks': 85},
    'S102': {'name': 'Priya', 'marks': 92}
}
```

**Explanation:**

The main Dictionary contains two student IDs.

Each student ID has another Dictionary containing:
- Student name.
- Student marks.

This structure is useful when storing multiple records with related information.

## Example 37: Accessing a Nested Dictionary Value

```python
print(students["S102"]["marks"])
```

**Output:**

```text
92
```

**Explanation:**

We use two keys to access a nested value.

- `students["S102"]` accesses Priya's Dictionary.
- `["marks"]` accesses her marks.

Therefore, the result is `92`.

## Example 38: Updating a Nested Dictionary Value

```python
students["S101"]["marks"] = 90

print(students)
```

**Output:**

```text
{
    'S101': {'name': 'Aman', 'marks': 90},
    'S102': {'name': 'Priya', 'marks': 92}
}
```

**Explanation:**

We access the nested Dictionary using the student ID and update the `"marks"` value.

Aman's marks change from 85 to 90.

## Example 39: Merging Two Dictionaries Using update()

```python
dict1 = {"a": 1, "b": 2}
dict2 = {"b": 20, "c": 3}

dict1.update(dict2)

print(dict1)
```

**Output:**

```text
{'a': 1, 'b': 20, 'c': 3}
```

**Explanation:**

The `update()` method merges the second Dictionary into the first Dictionary.

- `"a": 1` remains unchanged.
- `"b": 2` becomes `"b": 20`.
- `"c": 3` is added.

When keys overlap, the value from the second Dictionary replaces the existing value.

## Example 40: Merging Dictionaries Using the | Operator (Python 3.9+)

```python
dict1 = {"a": 1, "b": 2}
dict2 = {"b": 20, "c": 3}

merged = dict1 | dict2

print(merged)
```

**Output:**

```text
{'a': 1, 'b': 20, 'c': 3}
```

**Explanation:**

The `|` operator combines two Dictionaries and creates a new Dictionary.

Unlike `update()`, this operation does not modify the original Dictionaries.

When keys overlap, the right-hand Dictionary takes precedence.

## Example 41: Creating a Dictionary from a List of Tuples

```python
pairs = [("a", 1), ("b", 2), ("c", 3)]

result = dict(pairs)

print(result)
```

**Output:**

```text
{'a': 1, 'b': 2, 'c': 3}
```

**Explanation:**

Each Tuple contains two elements:

- First element becomes the key.
- Second element becomes the value.

The `dict()` constructor converts the List of Tuples into a Dictionary.

## Example 42: Getting Keys in Insertion Order

```python
print(list(student.keys()))
```

**Output:**

```text
['name', 'marks', 'grade']
```

**Explanation:**

Python Dictionaries preserve insertion order.

The `keys()` method returns keys in their insertion order, and `list()` converts them into a List.

## Example 43: Clearing All Entries Using clear()

```python
student.clear()

print(student)
```

**Output:**

```text
{}
```

**Explanation:**

The `clear()` method removes all key-value pairs from the Dictionary.

The Dictionary variable still exists, but it becomes empty.

## Example 44: Viewing Available Dictionary Methods

```python
example = {"a": 1, "b": 2}

print(dir(example))
```

**Output:**

```text
['__class__', '__class_getitem__', '__contains__', '__delattr__',
 '__delitem__', '__dir__', '__doc__', '__eq__', '__format__',
 '__ge__', '__getattribute__', '__getitem__', '__getstate__',
 '__gt__', '__hash__', '__init__', '__init_subclass__',
 '__ior__', '__iter__', '__le__', '__len__', '__lt__',
 '__ne__', '__new__', '__or__', '__reduce__', '__reduce_ex__',
 '__repr__', '__reversed__', '__ror__', '__setattr__',
 '__setitem__', '__sizeof__', '__str__', '__subclasshook__',
 'clear', 'copy', 'fromkeys', 'get', 'items', 'keys',
 'pop', 'popitem', 'setdefault', 'update', 'values']
```

**Explanation:**

The `dir()` function returns the available attributes and methods of an object.

For Dictionaries, it shows methods such as:

- `clear()`
- `copy()`
- `fromkeys()`
- `get()`
- `items()`
- `keys()`
- `pop()`
- `popitem()`
- `setdefault()`
- `update()`
- `values()`

Methods beginning and ending with double underscores are special or internal Python methods.

---

# 3. Python Set: Symmetric Difference

A **Set** stores unique elements and supports mathematical operations.

### Example: Symmetric Difference Using ^

```python
A = {1, 2, 3, 4, 5}
B = {4, 5, 6, 7, 8}

print(A ^ B)
```

**Output:**

```text
{1, 2, 3, 6, 7, 8}
```

**Explanation:**

The `^` operator performs symmetric difference.

It returns elements that exist in either Set, but not in both.

Let's understand:

| Set A | Set B | Result |
|---|---|---|
| 1 | No | Yes |
| 2 | No | Yes |
| 3 | No | Yes |
| 4 | 4 | No |
| 5 | 5 | No |
| No | 6 | Yes |
| No | 7 | Yes |
| No | 8 | Yes |

Therefore:

```python
A ^ B
```

Returns:

```text
{1, 2, 3, 6, 7, 8}
```

**Equivalent method:**

```python
print(A.symmetric_difference(B))
# Output: {1, 2, 3, 6, 7, 8}
```

---

# 4. Important Dictionary Methods: Quick Reference

| Method | Description |
|---|---|
| `dict()` | Creates a Dictionary |
| `get()` | Safely accesses a value |
| `keys()` | Returns all keys |
| `values()` | Returns all values |
| `items()` | Returns key-value pairs |
| `update()` | Adds or updates entries |
| `setdefault()` | Inserts a missing key |
| `pop()` | Removes a specified key |
| `popitem()` | Removes the last inserted pair |
| `clear()` | Removes all entries |
| `copy()` | Creates a shallow copy |
| `fromkeys()` | Creates a Dictionary from keys |

### Important Difference Between Similar Methods

| Method | Main purpose |
|---|---|
| `get()` | Retrieve a value safely |
| `setdefault()` | Retrieve a value or insert a missing key |
| `update()` | Add or replace entries |
| `pop()` | Remove a key and return its value |
| `popitem()` | Remove the last inserted pair |
| `clear()` | Empty the entire Dictionary |

---

# 5. Practice Exercises

## Beginner Level

1. Create a Dictionary containing your name, age, country and programming language.
2. Print the Dictionary and check its type.
3. Access your name using its key.
4. Access a missing key using `get()`.
5. Add a new key called `"university"`.
6. Update your age.
7. Check whether `"name"` exists in the Dictionary.
8. Print all keys using `keys()`.
9. Print all values using `values()`.
10. Find the total number of key-value pairs using `len()`.

## Intermediate Level

1. Create a Dictionary using `dict()`.
2. Create a Dictionary using `zip()` with two Lists.
3. Add multiple key-value pairs using `update()`.
4. Remove an element using `pop()`.
5. Remove the last inserted pair using `popitem()`.
6. Create a Dictionary using `fromkeys()`.
7. Convert Dictionary keys and values into Lists.
8. Iterate through a Dictionary using `items()`.
9. Merge two Dictionaries using `update()`.
10. Merge two Dictionaries using the `|` operator.

## Advanced Level

1. Create a Dictionary using comprehension to store the squares of numbers from 1 to 10.
2. Filter students who scored at least 80 marks using Dictionary comprehension.
3. Create a nested Dictionary containing five students.
4. Access and update nested Dictionary values.
5. Write a program to count the frequency of each element in a List using Dictionary.
6. Create a student management system using Dictionary.
7. Find the student with the highest marks using Dictionary.
8. Group students according to their marks using Dictionary comprehension.

---

# 6. Quick Revision

- A Dictionary stores information using key-value pairs.
- Dictionaries are ordered and mutable.
- Dictionary keys must be unique.
- `dict()` creates a Dictionary.
- `zip()` combines corresponding elements from multiple iterables.
- `get()` retrieves values safely.
- `update()` adds or updates multiple entries.
- `setdefault()` inserts a key only when it is missing.
- `keys()` returns all keys.
- `values()` returns all values.
- `items()` returns key-value pairs.
- `pop()` removes a specified entry.
- `popitem()` removes the last inserted pair.
- `copy()` creates a shallow copy.
- `fromkeys()` creates a Dictionary from an iterable of keys.
- Dictionary comprehension creates Dictionaries in a concise way.
- Nested Dictionaries allow us to store structured information.
- The `|` operator merges Dictionaries in Python 3.9+.
- The `^` operator performs symmetric difference between Sets.

---
