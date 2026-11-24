# Python Data Structures: List, Tuple, Set & Dictionary

Beginner-friendly notes covering Python's four fundamental collection data types, their properties, indexing, slicing, built-in methods, operations and practical examples.

## 📌 Learning Objectives

- Understand List, Tuple, Set and Dictionary.
- Differentiate between mutable and immutable data types.
- Understand positive and negative indexing.
- Perform slicing and modify collection elements.
- Use built-in methods to add, remove, search and sort data.
- Convert between different collection types.
- Apply data structures to real-world data manipulation.

---

# 1. Introduction to Python Data Structures

Python provides four important built-in collection data types:

1. **List** – Ordered, mutable collection that allows duplicates.
2. **Tuple** – Ordered, immutable collection that allows duplicates.
3. **Set** – Unordered collection of unique elements.
4. **Dictionary** – Collection of key-value pairs.

### Comparison of Python Data Structures

| Property | List | Tuple | Set | Dictionary |
|---|---|---|---|---|
| Syntax | `[]` | `()` | `{}` | `{key: value}` |
| Ordered | Yes | Yes | No | Yes |
| Mutable | Yes | No | Yes | Yes |
| Duplicates | Yes | Yes | No | Keys: No |
| Indexing | Yes | Yes | No | By key |
| Mixed data types | Yes | Yes | Yes | Yes |
| Common purpose | Collection | Fixed collection | Unique elements | Key-value mapping |

**Important notes:**

- List and Tuple support indexing and slicing.
- List is mutable, whereas Tuple is immutable.
- Set stores unique elements and does not support indexing.
- Dictionary stores information as key-value pairs.
- Dictionary keys must be unique and hashable.

---

# 2. Python List

A **List** is an ordered and mutable collection that allows duplicate elements and different data types.

### Example 1: Creating a List

```python
fruits = ["Apple", "Banana", "Cherry"]

print(fruits)       # Output: ['Apple', 'Banana', 'Cherry']
print(type(fruits)) # Output: <class 'list'>
```

### Example 2: List with Mixed Data Types

```python
fruits = ["Apple", 5, 8, 5, "Apple", 9.76, True]

print(fruits)
# Output: ['Apple', 5, 8, 5, 'Apple', 9.76, True]
```

A List can contain strings, integers, floats, booleans and other data types.

### Example 3: Modifying List Elements

Lists are mutable, which means we can modify existing elements.

```python
fruits = ["Apple", "Banana", "Cherry", "Mango"]

fruits[2] = "Orange"

print(fruits)
# Output: ['Apple', 'Banana', 'Orange', 'Mango']
```

Explanation: The element at index `2`, originally `"Cherry"`, has been replaced with `"Orange"`.

### Example 4: Creating Lists Using list()

```python
numbers = list((10, 20, 30))
print(numbers)  # Output: [10, 20, 30]

letters = list("Mahipal")
print(letters)  # Output: ['M', 'a', 'h', 'i', 'p', 'a', 'l']
```

Explanation:
- `list((10, 20, 30))` converts a Tuple into a List.
- `list("Mahipal")` converts a string into individual characters.

### Example 5: Positive and Negative Indexing

Python supports positive and negative indexing.

```python
fruits = ["Apple", "Banana", "Cherry"]

print(fruits[0])   # Output: Apple
print(fruits[1])   # Output: Banana
print(fruits[2])   # Output: Cherry

print(fruits[-1])  # Output: Cherry
print(fruits[-2])  # Output: Banana
print(fruits[-3])  # Output: Apple
```

**Indexing explanation**

| Element | Positive Index | Negative Index |
|---|---:|---:|
| Apple | 0 | -3 |
| Banana | 1 | -2 |
| Cherry | 2 | -1 |

Positive indexing starts from `0`, whereas negative indexing starts from `-1`.

### Example 6: List Slicing

**Syntax:**

```python
list_name[start:stop:step]
```

Example:

```python
fruit = ["Apple", "Banana", "Cherry", "Banana", "Mango"]

print(fruit[2:])     # Output: ['Cherry', 'Banana', 'Mango']
print(fruit[2:5])    # Output: ['Cherry', 'Banana', 'Mango']
print(fruit[0:5:3])  # Output: ['Apple', 'Banana']
print(fruit[::-1])   # Output: ['Mango', 'Banana', 'Cherry', 'Banana', 'Apple']
```

Explanation:

- `fruit[2:]` – Starts at index 2 and continues to the end.
- `fruit[2:5]` – Returns elements from index 2 to 4.
- `fruit[0:5:3]` – Selects elements at index 0 and 3.
- `fruit[::-1]` – Reverses the List.

### Example 7: Updating Multiple Elements Using Slicing

```python
num = [10, 20, 30, 40, 50, 60, 70]

num[1:4] = [200, 300, 400]

print(num)
# Output: [10, 200, 300, 400, 50, 60, 70]
```

Explanation: The elements at indexes 1, 2 and 3 are replaced with 200, 300 and 400.

### Example 8: Adding Elements to a List

**append() – Adds one element at the end.**

```python
num = [10, 20, 30]

num.append(40)

print(num)  # Output: [10, 20, 30, 40]
```

**extend() – Adds multiple elements individually.**

```python
num = [10, 20, 30]

num.extend([40, 50])

print(num)  # Output: [10, 20, 30, 40, 50]
```

**insert() – Inserts an element at a specific index.**

```python
num = [10, 20, 30, 40]

num.insert(2, 200)

print(num)  # Output: [10, 20, 200, 30, 40]
```

**Difference between append() and extend():**

```python
num = [10, 20, 30]

num.append([40, 50])
print(num)  # [10, 20, 30, [40, 50]]

num = [10, 20, 30]

num.extend([40, 50])
print(num)  # [10, 20, 30, 40, 50]
```

Explanation:
- `append()` adds the entire List as one element.
- `extend()` adds each element separately.

### Example 9: Removing Elements from a List

```python
num = [10, 20, 30, 40, 50]

num.remove(20)
print(num)  # [10, 30, 40, 50]

num.pop()
print(num)  # [10, 30, 40]

num.pop(1)
print(num)  # [10, 40]
```

Explanation:

- `remove(20)` removes the specified value.
- `pop()` removes and returns the last element.
- `pop(1)` removes and returns the element at index 1.

Other removal operations:

```python
num = [10, 20, 30, 40, 50]

del num[2]
print(num)  # [10, 20, 40, 50]

num.clear()
print(num)  # []
```

### Example 10: Membership Operators

```python
fruit = ["Apple", "Banana", "Cherry", "Mango"]

print("Mango" in fruit)      # Output: True
print("Mango" not in fruit)  # Output: False
print("MANGO" in fruit)      # Output: False
```

Python string comparisons are case-sensitive.

### Example 11: Sorting a List

**Ascending order:**

```python
numbers = [50, 10, 40, 20, 30]

numbers.sort()

print(numbers)
# Output: [10, 20, 30, 40, 50]
```

**Descending order:**

```python
numbers = [50, 10, 40, 20, 30]

numbers.sort(reverse=True)

print(numbers)
# Output: [50, 40, 30, 20, 10]
```

---

# 3. Python Tuple

A **Tuple** is an ordered and immutable collection. It allows duplicate elements and supports indexing.

### Example 1: Creating a Tuple

```python
numbers = (10, 20, 30, 20, 40, 50, 20)

print(numbers)
print(type(numbers))
print(len(numbers))
```

**Output:**

```text
(10, 20, 30, 20, 40, 50, 20)
<class 'tuple'>
7
```

### Example 2: Accessing Elements

```python
numbers = (10, 20, 30, 40, 50)

print(numbers[0])   # Output: 10
print(numbers[2])   # Output: 30

print(numbers[-1])  # Output: 50
print(numbers[-2])  # Output: 40
```

### Example 3: Tuple Slicing

```python
numbers = (10, 20, 30, 20, 40, 50, 20)

print(numbers[1:4])   # (20, 30, 20)
print(numbers[:4])    # (10, 20, 30, 20)
print(numbers[2:])    # (30, 20, 40, 50, 20)
print(numbers[::2])   # (10, 30, 40, 20)
print(numbers[::-1])  # (20, 50, 40, 20, 30, 20, 10)
```

### Example 4: Tuple Methods

Tuples have only two built-in methods: `count()` and `index()`.

**count() – Counts occurrences of a value.**

```python
numbers = (10, 20, 30, 20, 40, 50, 20)

print(numbers.count(20))  # Output: 3
print(numbers.count(50))  # Output: 1
```

**index() – Returns the first matching element's index.**

```python
print(numbers.index(30))     # Output: 2
print(numbers.index(20))     # Output: 1
print(numbers.index(20, 2))  # Output: 3
```

The second argument specifies where the search starts.

### Example 5: Membership Operations

```python
numbers = (10, 20, 30, 40, 50)

print(30 in numbers)      # Output: True
print(100 in numbers)     # Output: False
print(100 not in numbers) # Output: True
```

### Example 6: Built-in Functions

```python
numbers = (10, 20, 30, 40, 50)

print(min(numbers))  # Output: 10
print(max(numbers))  # Output: 50
print(sum(numbers))  # Output: 150
print(len(numbers))  # Output: 5
```

### Example 7: Concatenation and Repetition

```python
tuple1 = (1, 2, 3)
tuple2 = (4, 5, 6)

print(tuple1 + tuple2)
# Output: (1, 2, 3, 4, 5, 6)

print(tuple1 * 3)
# Output: (1, 2, 3, 1, 2, 3, 1, 2, 3)
```

### Example 8: Converting Between List and Tuple

```python
numbers = (10, 20, 30)

numbers_list = list(numbers)
print(numbers_list)  # [10, 20, 30]

new_tuple = tuple([100, 200, 300])
print(new_tuple)     # (100, 200, 300)
```

### Example 9: Tuple Unpacking

```python
student = ("Aman", 21, 85)

name, age, marks = student

print(name)   # Output: Aman
print(age)    # Output: 21
print(marks)  # Output: 85
```

Explanation: Each Tuple element is assigned to its corresponding variable.

### Example 10: Extended Tuple Unpacking

```python
values = (10, 20, 30, 40, 50)

first, *middle, last = values

print(first)   # Output: 10
print(middle)  # Output: [20, 30, 40]
print(last)    # Output: 50
```

Explanation:
- `first` receives the first element.
- `*middle` collects the middle elements into a List.
- `last` receives the final element.

### Example 11: Single-Element Tuple

```python
single_element = (100,)

print(single_element)       # Output: (100,)
print(type(single_element)) # Output: <class 'tuple'>
```

**Important:** The comma is necessary to create a single-element Tuple.

### Example 12: Sorting a Tuple

```python
unsorted_tuple = (50, 10, 40, 20, 30)

print(sorted(unsorted_tuple))
# Output: [10, 20, 30, 40, 50]

print(tuple(sorted(unsorted_tuple)))
# Output: (10, 20, 30, 40, 50)
```

Note: `sorted()` returns a List, not a Tuple. We can convert it back using `tuple()`.

### Example 13: Iterating Through a Tuple

```python
tuple1 = (1, 2, 3)

for item in tuple1:
    print(item)
```

**Output:**

```text
1
2
3
```

Using `enumerate()`:

```python
for index, value in enumerate(tuple1):
    print(index, value)
```

**Output:**

```text
0 1
1 2
2 3
```

### Example 14: Finding Unique Elements

```python
numbers = (10, 20, 30, 20, 40, 50, 20)

print(len(set(numbers)))  # Output: 5
```

Explanation: The Set removes duplicate values. The unique elements are 10, 20, 30, 40 and 50.

### Example 15: Tuple Comparison

```python
print((1, 2, 3) == (1, 2, 3))  # Output: True
print((1, 2, 3) < (1, 2, 4))   # Output: True
```

### Example 16: Tuple Immutability

```python
numbers = (10, 20, 30)

# numbers[0] = 100
# TypeError: 'tuple' object does not support item assignment
```

The assignment is commented out because it produces an error.

However, a Tuple can contain mutable objects:

```python
data = (10, 20, [30, 40])

data[2].append(50)

print(data)
# Output: (10, 20, [30, 40, 50])
```

Explanation: We cannot replace a Tuple element, but we can modify a mutable object stored inside it.

---

# 4. Python Set

A **Set** is an unordered, mutable collection that stores unique elements. It does not support indexing.

### Example 1: Creating a Set

```python
numbers = {10, 20, 30, 40, 50}

print(numbers)
print(type(numbers))
```

**Output:**

```text
{10, 20, 30, 40, 50}
<class 'set'>
```

Note: Set display order is not guaranteed.

### Example 2: Creating an Empty Set

```python
empty_set = set()

print(empty_set)       # Output: set()
print(type(empty_set)) # Output: <class 'set'>
```

**Important:** `{}` creates an empty Dictionary, not an empty Set.

### Example 3: Removing Duplicate Elements

```python
numbers = set([10, 20, 20, 30, 30, 40])

print(numbers)  # Output: {10, 20, 30, 40}
```

Explanation: Duplicate elements are automatically removed. The order may vary.

### Example 4: Adding Elements

**add() – Adds one element.**

```python
numbers = {10, 20, 30}

numbers.add(60)

print(numbers)  # Output: {10, 20, 30, 60}
```

**update() – Adds multiple elements.**

```python
numbers = {10, 20, 30}

numbers.update([70, 80, 90])

print(numbers)  # Output: {10, 20, 30, 70, 80, 90}
```

### Example 5: Removing Elements

```python
numbers = {10, 20, 30, 40, 50}

numbers.remove(20)
print(numbers)  # {10, 30, 40, 50}

numbers.discard(30)
print(numbers)  # {10, 40, 50}
```

Difference:

| Method | Behaviour |
|---|---|
| `remove()` | Raises KeyError if element does not exist |
| `discard()` | Does not raise an error if element does not exist |
| `pop()` | Removes and returns an arbitrary element |
| `clear()` | Removes all elements |

Example:

```python
numbers = {10, 20, 30, 40}

numbers.discard(999)
print(numbers)  # {10, 20, 30, 40}

removed_value = numbers.pop()
print("Removed:", removed_value)

print(numbers)
```

The exact popped element is not guaranteed. For example:

```text
{10, 20, 30, 40}
Removed: 10
{20, 30, 40}
```

### Example 6: Membership Operations

```python
numbers = {10, 20, 30, 40}

print(40 in numbers)      # Output: True
print(999 not in numbers) # Output: True
```

### Example 7: Set Operations

Let's create two Sets:

```python
A = {1, 2, 3, 4, 5}
B = {4, 5, 6, 7, 8}
```

**Union – Combines all unique elements.**

```python
print(A | B)
print(A.union(B))
```

Output:

```text
{1, 2, 3, 4, 5, 6, 7, 8}
{1, 2, 3, 4, 5, 6, 7, 8}
```

**Intersection – Returns common elements.**

```python
print(A & B)
print(A.intersection(B))
```

Output:

```text
{4, 5}
{4, 5}
```

**Difference – Returns elements present in A but not B.**

```python
print(A - B)
print(A.difference(B))
```

Output:

```text
{1, 2, 3}
{1, 2, 3}
```

**Reverse Difference**

```python
print(B - A)  # Output: {6, 7, 8}
```

**Symmetric Difference – Returns elements that are not common to both Sets.**

```python
print(A ^ B)
print(A.symmetric_difference(B))
```

Output:

```text
{1, 2, 3, 6, 7, 8}
{1, 2, 3, 6, 7, 8}
```

### Example 8: Subset, Superset and Disjoint

```python
A = {1, 2, 3, 4, 5}

print({1, 2}.issubset(A))          # True
print(A.issuperset({1, 2}))        # True
print({1, 2}.isdisjoint({3, 4}))   # True
```

| Method | Meaning |
|---|---|
| `issubset()` | Checks whether all elements exist in another Set |
| `issuperset()` | Checks whether another Set's elements exist in this Set |
| `isdisjoint()` | Checks whether two Sets have no common elements |

### Example 9: Updating Set Operations

**intersection_update()**

```python
C = {1, 2, 3, 4}
D = {3, 4, 5, 6}

C.intersection_update(D)

print(C)  # Output: {3, 4}
```

Only common elements remain in `C`.

**difference_update()**

```python
C = {1, 2, 3, 4}
D = {3, 4, 5, 6}

C.difference_update(D)

print(C)  # Output: {1, 2}
```

Elements from `D` are removed from `C`.

**symmetric_difference_update()**

```python
C = {1, 2, 3, 4}
D = {3, 4, 5, 6}

C.symmetric_difference_update(D)

print(C)  # Output: {1, 2, 5, 6}
```

Only elements that are not common to both Sets remain.

### Example 10: Set Operators for Updating

```python
C = {1, 2}

C |= {3, 4}
print(C)  # {1, 2, 3, 4}

C = {1, 2, 3}
C &= {2, 3, 4}
print(C)  # {2, 3}

C = {1, 2, 3}
C -= {2}
print(C)  # {1, 3}

C = {1, 2, 3}
C ^= {3, 4}
print(C)  # {1, 2, 4}
```

### Example 11: Copying a Set

```python
original = {10, 20, 30}

copied = original.copy()

copied.add(40)

print(original)  # {10, 20, 30}
print(copied)    # {10, 20, 30, 40}
```

Changing the copied Set does not change the original Set.

### Example 12: Converting Set into List and Tuple

```python
A = {1, 2, 3, 4, 5}

numbers_list = list(A)
numbers_tuple = tuple(A)

print(numbers_list)
print(numbers_tuple)
```

Possible output:

```text
[1, 2, 3, 4, 5]
(1, 2, 3, 4, 5)
```

Note: The order is not guaranteed because the original collection is a Set.

### Example 13: Iterating Through a Set

```python
A = {1, 2, 3, 4, 5}

for item in A:
    print(item)
```

Possible output:

```text
1
2
3
4
5
```

The iteration order may vary.

### Example 14: Finding Minimum, Maximum and Sum

```python
A = {1, 2, 3, 4, 5}

print(min(A))  # Output: 1
print(max(A))  # Output: 5
print(sum(A))  # Output: 15
print(len(A))  # Output: 5
```

### Example 15: Comparing Sets

```python
print({1, 2, 3} == {3, 2, 1})  # Output: True
```

Explanation: Sets are compared by their elements, not their order.

---

# 5. Python Dictionary

A **Dictionary** is a mutable collection that stores data in key-value pairs. It preserves insertion order and does not allow duplicate keys.

### Example 1: Creating a Dictionary

```python
student = {
    "name": "Aman",
    "age": 21,
    "marks": 85,
    "city": "Jaipur"
}

print(student)
print(type(student))
```

**Output:**

```text
{'name': 'Aman', 'age': 21, 'marks': 85, 'city': 'Jaipur'}
<class 'dict'>
```

### Example 2: Creating an Empty Dictionary

```python
empty_dict = {}

print(empty_dict)       # Output: {}
print(type(empty_dict)) # Output: <class 'dict'>
```

### Example 3: Creating a Dictionary Using dict()

```python
student2 = dict(name="Priya", age=22, marks=92)

print(student2)
# Output: {'name': 'Priya', 'age': 22, 'marks': 92}
```

### Example 4: Creating a Dictionary Using zip()

```python
names = ["Aman", "Priya", "Rahul"]
marks = [85, 92, 78]

student_marks = dict(zip(names, marks))

print(student_marks)
# Output: {'Aman': 85, 'Priya': 92, 'Rahul': 78}
```

Explanation: `zip()` combines corresponding elements from two Lists.

### Example 5: Accessing Values Using Keys

```python
student = {
    "name": "Aman",
    "age": 21,
    "marks": 85
}

print(student["name"])   # Output: Aman
print(student["marks"])  # Output: 85
```

### Example 6: Accessing Values Using get()

```python
print(student.get("name"))                     # Aman
print(student.get("grade"))                    # None
print(student.get("grade", "Not Available"))   # Not Available
```

Difference:

- `student["grade"]` raises KeyError if the key does not exist.
- `student.get("grade")` returns None if the key does not exist.
- `student.get("grade", "Not Available")` returns the specified default.

### Example 7: Adding and Updating Values

```python
student["grade"] = "A"

student["marks"] = 95

student.update({
    "age": 22,
    "city": "Delhi"
})

print(student)
```

**Output:**

```text
{'name': 'Aman', 'age': 22, 'marks': 95, 'grade': 'A', 'city': 'Delhi'}
```

Explanation:
- `student["grade"] = "A"` adds a new key.
- `student["marks"] = 95` updates an existing value.
- `update()` adds or updates multiple key-value pairs.

### Example 8: Using setdefault()

```python
student = {
    "name": "Aman",
    "age": 21
}

student.setdefault("country", "India")
print(student)

student.setdefault("age", 30)
print(student)
```

**Output:**

```text
{'name': 'Aman', 'age': 21, 'country': 'India'}
{'name': 'Aman', 'age': 21, 'country': 'India'}
```

Explanation: `setdefault()` inserts a new key only if it does not already exist.

### Example 9: Finding Dictionary Length

```python
student = {
    "name": "Aman",
    "age": 21,
    "marks": 85
}

print(len(student))  # Output: 3
```

### Example 10: Checking Whether a Key Exists

```python
print("name" in student)       # Output: True
print("salary" not in student) # Output: True
```

Note: The `in` operator checks keys by default.

To check values:

```python
print("Aman" in student.values())  # Output: True
print(100 in student.values())     # Output: False
```

### Example 11: Accessing Keys, Values and Items

```python
student = {
    "name": "Aman",
    "age": 21,
    "marks": 85
}

print(student.keys())
print(student.values())
print(student.items())
```

**Output:**

```text
dict_keys(['name', 'age', 'marks'])
dict_values(['Aman', 21, 85])
dict_items([('name', 'Aman'), ('age', 21), ('marks', 85)])
```

Converting them into Lists:

```python
print(list(student.keys()))
print(list(student.values()))
print(list(student.items()))
```

**Output:**

```text
['name', 'age', 'marks']
['Aman', 21, 85]
[('name', 'Aman'), ('age', 21), ('marks', 85)]
```

### Example 12: Iterating Through a Dictionary

**Loop through keys:**

```python
for key in student:
    print(key)
```

Output:

```text
name
age
marks
```

**Loop through values:**

```python
for value in student.values():
    print(value)
```

Output:

```text
Aman
21
85
```

**Loop through key-value pairs:**

```python
for key, value in student.items():
    print(key, ":", value)
```

Output:

```text
name : Aman
age : 21
marks : 85
```

### Example 13: Removing Dictionary Elements

**pop() – Removes a specified key and returns its value.**

```python
student = {
    "name": "Aman",
    "age": 21,
    "marks": 85
}

removed_value = student.pop("age")

print(removed_value)  # Output: 21
print(student)        # Output: {'name': 'Aman', 'marks': 85}
```

Using a default value:

```python
print(student.pop("salary", "Not Found"))
# Output: Not Found
```

**popitem() – Removes and returns the last inserted pair.**

```python
student = {
    "name": "Aman",
    "age": 21,
    "marks": 85
}

removed_item = student.popitem()

print(removed_item)  # Output: ('marks', 85)
print(student)       # Output: {'name': 'Aman', 'age': 21}
```

Using `del`:

```python
student = {
    "name": "Aman",
    "age": 21,
    "marks": 85
}

del student["age"]

print(student)  # Output: {'name': 'Aman', 'marks': 85}
```

Clearing everything:

```python
student.clear()

print(student)  # Output: {}
```

### Example 14: Copying a Dictionary

```python
original = {
    "name": "Aman",
    "marks": 85
}

copied = original.copy()

copied["marks"] = 95

print(original)  # {'name': 'Aman', 'marks': 85}
print(copied)    # {'name': 'Aman', 'marks': 95}
```

Explanation: The copied Dictionary can be modified independently of the original at the top level.

### Example 15: Creating a Dictionary Using fromkeys()

```python
subjects = ["Python", "SQL", "Excel"]

subject_status = dict.fromkeys(subjects, "Pending")

print(subject_status)
```

**Output:**

```text
{'Python': 'Pending', 'SQL': 'Pending', 'Excel': 'Pending'}
```

### Example 16: Dictionary Comprehension

```python
squares = {x: x**2 for x in range(1, 6)}

print(squares)
# Output: {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
```

Explanation: Each number becomes a key, and its square becomes the corresponding value.

With a condition:

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
# Output: {'Aman': 85, 'Priya': 92}
```

### Example 17: Nested Dictionary

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

Accessing nested values:

```python
print(students["S102"]["marks"])  # Output: 92
```

Updating nested values:

```python
students["S101"]["marks"] = 90

print(students["S101"])
# Output: {'name': 'Aman', 'marks': 90}
```

### Example 18: Merging Dictionaries

Using `update()`:

```python
dict1 = {"a": 1, "b": 2}
dict2 = {"b": 20, "c": 3}

dict1.update(dict2)

print(dict1)
# Output: {'a': 1, 'b': 20, 'c': 3}
```

Using the `|` operator (Python 3.9+):

```python
dict1 = {"a": 1, "b": 2}
dict2 = {"b": 20, "c": 3}

merged = dict1 | dict2

print(merged)
# Output: {'a': 1, 'b': 20, 'c': 3}
```

When keys overlap, the value from the right-hand Dictionary takes precedence.

### Example 19: Creating Dictionary from a List of Tuples

```python
pairs = [
    ("a", 1),
    ("b", 2),
    ("c", 3)
]

result = dict(pairs)

print(result)
# Output: {'a': 1, 'b': 2, 'c': 3}
```

### Example 20: Dictionary Insertion Order

```python
student = {
    "name": "Aman",
    "age": 21,
    "marks": 85
}

print(list(student.keys()))
# Output: ['name', 'age', 'marks']
```

Python dictionaries preserve insertion order.

---

# 6. Important Built-in Functions

| Function | Purpose |
|---|---|
| `len()` | Returns the number of elements |
| `type()` | Returns the data type |
| `min()` | Returns the minimum value |
| `max()` | Returns the maximum value |
| `sum()` | Calculates the sum |
| `sorted()` | Returns a sorted List |
| `list()` | Converts to a List |
| `tuple()` | Converts to a Tuple |
| `set()` | Converts to a Set |
| `dict()` | Creates a Dictionary |
| `enumerate()` | Returns index and value |
| `zip()` | Combines multiple iterables |

### Example: Using Multiple Built-in Functions

```python
numbers = [50, 10, 40, 20, 30]

print(len(numbers))      # Output: 5
print(min(numbers))      # Output: 10
print(max(numbers))      # Output: 50
print(sum(numbers))      # Output: 150
print(sorted(numbers))   # Output: [10, 20, 30, 40, 50]
print(type(numbers))     # Output: <class 'list'>
```

---

# 7. Quick Comparison of Important Methods

| Operation | List | Tuple | Set | Dictionary |
|---|---|---|---|---|
| Add one | `append()` | Not supported | `add()` | `dict[key] = value` |
| Add multiple | `extend()` | Not supported | `update()` | `update()` |
| Remove | `remove()` | Not supported | `remove()` | `pop()` |
| Clear | `clear()` | Not supported | `clear()` | `clear()` |
| Copy | `copy()` | No built-in copy method | `copy()` | `copy()` |
| Count | `count()` | `count()` | No | No |
| Find index | `index()` | `index()` | No | Access by key |
| Sort | `sort()` | `sorted()` | `sorted()` | `sorted()` |

---

# 8. Practice Exercises

## Beginner Level

1. Create a List of five fruits and print each element.
2. Find the length of a List using `len()`.
3. Access the first and last elements using indexing.
4. Use negative indexing to access the second-last element.
5. Reverse a List using slicing.
6. Add elements using `append()`, `extend()` and `insert()`.
7. Remove elements using `remove()` and `pop()`.
8. Create a Tuple containing five numbers.
9. Find the maximum and minimum values of a Tuple.

## Intermediate Level

1. Count how many times a particular number appears in a Tuple.
2. Convert a Tuple into a List and modify it.
3. Create a Set from a List containing duplicate values.
4. Find the union and intersection of two Sets.
5. Find the difference and symmetric difference of two Sets.
6. Create a Dictionary containing student information.
7. Add, update and delete Dictionary values.
8. Iterate through a Dictionary using `items()`.
9. Create a Dictionary using two Lists and `zip()`.

## Advanced Level

1. Find students who scored at least 80 marks using dictionary comprehension.
2. Create a nested Dictionary containing multiple students.
3. Remove duplicate elements from a List using Set.
4. Write a program to count the frequency of each element in a List using Dictionary.
5. Build a simple student management system using a Dictionary.

---

# 9. Real-World Applications

| Data Structure | Real-world application |
|---|---|
| List | Storing datasets, customer records and transactions |
| Tuple | Fixed coordinates, configuration values and database records |
| Set | Removing duplicate records and finding unique users |
| Dictionary | JSON data, API responses, configuration and frequency counting |

**Connection to Data Science and Machine Learning:**

- Lists help organize and process collections of data.
- Tuples are useful for fixed records and structured values.
- Sets help identify unique values and remove duplicates.
- Dictionaries are useful for representing structured records, feature mappings and frequency counts.

---

# 10. Quick Revision

- **List:** Ordered, mutable and allows duplicates.
- **Tuple:** Ordered, immutable and allows duplicates.
- **Set:** Unordered, mutable and stores unique elements.
- **Dictionary:** Ordered, mutable and stores unique keys with associated values.
- `append()` adds one element to a List.
- `extend()` adds multiple elements to a List.
- `insert()` adds an element at a specific index.
- `count()` counts occurrences in a List or Tuple.
- `index()` finds the position of an element in a List or Tuple.
- `add()` inserts one element into a Set.
- `update()` adds multiple elements to a Set.
- `union()` combines Sets.
- `intersection()` finds common elements.
- `difference()` finds elements present in one Set but not another.
- `get()` safely accesses Dictionary values.
- `items()` returns Dictionary key-value pairs.

---

