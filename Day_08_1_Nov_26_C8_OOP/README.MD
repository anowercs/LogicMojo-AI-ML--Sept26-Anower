# Python Object-Oriented Programming (OOP)

**Session:** Live Class – OOP Practice  
**Date:** November 2026  
**Topic:** Object-Oriented Programming in Python

---

## 1. Introduction to OOP

Object-Oriented Programming (OOP) is a programming approach where we organize code using **classes and objects**.

Instead of writing all the code separately, we create classes that contain data (attributes) and behaviour (methods).

### Main OOP Concepts

| Concept | Meaning |
|---|---|
| Class | Blueprint for creating objects |
| Object | Instance of a class |
| Constructor | Initializes an object |
| Attribute | Data stored inside an object |
| Method | Function defined inside a class |
| Inheritance | Reusing another class's attributes and methods |
| Multiple Inheritance | Inheriting from multiple parent classes |
| Polymorphism | Same method/interface, different behaviours |

## 2. Class and Object

A class is a blueprint. An object is an instance created from that class.

```python
class Student:
    pass

student1 = Student()
student2 = Student()
student3 = Student()

print(student1)
print(student2)
```

**Explanation:**

- `class Student:` creates a class.
- `pass` means the class has no implementation yet.
- `Student()` creates an object.
- `student1`, `student2`, and `student3` are separate objects.

**Output:**

```text
<__main__.Student object at ...>
<__main__.Student object at ...>
```

The memory addresses will vary each time the program runs.

**Remember:** Class = Blueprint; Object = Instance.

## 3. Constructor – `__init__()`

The `__init__()` method initializes an object's attributes. Python calls it automatically when an object is created.

```python
class Student:
    def __init__(self, name, age, course):
        self.name = name
        self.age = age
        self.course = course


student1 = Student("Rupali", 32, "AI/ML")
student2 = Student("Jamil", 42, "CSE")

print(student1.name)
print(student2.name)
print(student1.age)
print(student2.course)
```

**Output:**

```text
Rupali
Jamil
32
CSE
```

### Understanding `self`

- `self` refers to the current object.
- `self.name` stores the name inside that object.
- `self.age` stores the age inside that object.
- Each object maintains its own attribute values.

Example:

```python
student1.name  # Rupali
student2.name  # Jamil
```

**Remember:** `self` connects an object's data and methods.

## 4. Methods Inside a Class

A method is a function defined inside a class.

```python
class Student:
    def __init__(self, name, marks):
        self.name = name
        self.marks = marks

    def display_details(self):
        print("Student name:", self.name)
        print("Marks:", self.marks)

    def check_result(self):
        if self.marks >= 40:
            print("Result: Pass")
        else:
            print("Result: Fail")


student1 = Student("Shafi", 95)
student2 = Student("Jasim", 73)

student1.display_details()
student2.display_details()

student1.check_result()
student2.check_result()
```

**Output:**

```text
Student name: Shafi
Marks: 95
Student name: Jasim
Marks: 73
Result: Pass
Result: Pass
```

### Methods in this example

| Method | Responsibility |
|---|---|
| `__init__()` | Initializes student information |
| `display_details()` | Displays student details |
| `check_result()` | Checks pass/fail status |

**Remember:** Methods define what an object can do.

## 5. Single Inheritance

Inheritance allows a child class to reuse the attributes and methods of a parent class.

```python
class Employee:

    def __init__(self, name, salary):
        self.name = name
        self.salary = salary

    def show_details(self):
        print("Employee name:", self.name)
        print("Salary:", self.salary)


class DataScientist(Employee):

    def work(self):
        print("Working on machine learning models")


emp1 = DataScientist("Ruhul", 8000)

emp1.show_details()
emp1.work()
```

**Output:**

```text
Employee name: Ruhul
Salary: 8000
Working on machine learning models
```

### Understanding inheritance

- `Employee` is the parent class.
- `DataScientist` is the child class.
- `DataScientist(Employee)` means the child inherits from the parent.
- The child can use `show_details()` without defining it again.
- The child can also define its own methods, such as `work()`.

**Remember:** Inheritance = Code reusability.

## 6. Multiple Inheritance

A class can inherit from more than one parent class in Python.

```python
class Python:

    def python_skill(self):
        print("Knows Python")


class SQL:

    def sql_skill(self):
        print("Knows SQL")


class DataScientist(Python, SQL):
    pass


person = DataScientist()

person.python_skill()
person.sql_skill()
```

**Output:**

```text
Knows Python
Knows SQL
```

### Understanding multiple inheritance

`DataScientist` inherits from both `Python` and `SQL`.

Therefore, its object can access methods from both parent classes.

**Remember:** Multiple inheritance = One child, multiple parents.

**Java comparison:** Java does not support multiple inheritance of classes, but it supports implementing multiple interfaces.

## 7. Polymorphism

Polymorphism means one interface can have different behaviours depending on the object.

```python
class Dog:
    def sound(self):
        print("Dog barks")


class Cat:
    def sound(self):
        print("Cat meows")


class Cow:
    def sound(self):
        print("Cow moos")


animals = [Dog(), Cat(), Cow()]

for animal in animals:
    animal.sound()
```

**Output:**

```text
Dog barks
Cat meows
Cow moos
```

### Understanding polymorphism

All three classes have a method called `sound()`.

However, each class implements it differently.

| Object | Method call | Behaviour |
|---|---|---|
| Dog | `sound()` | Dog barks |
| Cat | `sound()` | Cat meows |
| Cow | `sound()` | Cow moos |

The same method call produces different results depending on the object.

This example demonstrates duck typing in Python. The classes do not need a common parent class.

**Remember:** Polymorphism = Same method name, different behaviour.

---

# 8. Quick Revision – OOP at a Glance

| Concept | Quick meaning | Example |
|---|---|---|
| Class | Blueprint | `class Student:` |
| Object | Instance | `student1 = Student()` |
| Constructor | Initializes object | `def __init__(self):` |
| `self` | Current object | `self.name = name` |
| Attribute | Object data | `student1.name` |
| Method | Object behaviour | `student1.display()` |
| Inheritance | Child reuses parent | `class Child(Parent):` |
| Multiple inheritance | Multiple parents | `class Child(A, B):` |
| Polymorphism | Different behaviours | `animal.sound()` |

## 9. Five-Minute Revision Examples

### 1. Class and Object

```python
class Car:
    pass

my_car = Car()
```

**Remember:** Create a class, then create an object.

### 2. Constructor and Attributes

```python
class Car:
    def __init__(self, brand):
        self.brand = brand

my_car = Car("Toyota")
print(my_car.brand)

# Output: Toyota
```

**Remember:** Constructor initializes object data.

### 3. Methods

```python
class Car:
    def start(self):
        print("Car started")

my_car = Car()
my_car.start()

# Output: Car started
```

**Remember:** A method defines object behaviour.

### 4. Inheritance

```python
class Animal:
    def eat(self):
        print("Eating")


class Dog(Animal):
    pass


dog = Dog()
dog.eat()

# Output: Eating
```

**Remember:** A child can reuse a parent's methods.

### 5. Multiple Inheritance

```python
class Camera:
    def take_photo(self):
        print("Taking photo")


class Phone:
    def make_call(self):
        print("Making call")


class Smartphone(Camera, Phone):
    pass


mobile = Smartphone()
mobile.take_photo()
mobile.make_call()
```

**Output:**

```text
Taking photo
Making call
```

**Remember:** One child can inherit from multiple parents.

### 6. Polymorphism

```python
class Dog:
    def sound(self):
        print("Bark")


class Cat:
    def sound(self):
        print("Meow")


for animal in [Dog(), Cat()]:
    animal.sound()
```

**Output:**

```text
Bark
Meow
```

**Remember:** Same method call, different behaviour.

---

# 10. Important Python OOP vs Java OOP

| Topic | Python | Java |
|---|---|---|
| Class | `class Student:` | `class Student {}` |
| Object | `Student()` | `new Student()` |
| Constructor | `__init__()` | Constructor with class name |
| Current object | `self` | `this` |
| Inheritance | `class B(A):` | `class B extends A` |
| Multiple class inheritance | Supported | Not supported |
| Methods | Defined with `def` | Defined with return type and method name |
| Polymorphism | Supports duck typing and overriding | Supports overriding and overloading |


---

## Final Revision Formula

```text
CLASS       = Blueprint
OBJECT      = Instance
__init__()  = Initialize object
self        = Current object
ATTRIBUTE   = Object data
METHOD      = Object behaviour
INHERITANCE = Reuse parent class
POLYMORPHISM= Same interface, different behaviour
```

**Learning objective:** Understand how to organize Python programs using classes and objects, reuse code through inheritance, and implement different behaviours through polymorphism.

*LogicMojo – Python OOP Live Practice Session*


# Python OOP — 20 Practice Assignments

**Object-Oriented Programming | Beginner to Advanced | Python + Machine Learning**

## 📚 Overview

These 20 practical assignments are designed to build a strong foundation in Python Object-Oriented Programming (OOP).

**Topics covered:**
- Classes and Objects
- Constructors (`__init__`)
- Attributes and Methods
- Instance and Class Variables
- Encapsulation
- Inheritance
- Polymorphism
- Abstraction
- Exception Handling
- Composition
- Machine Learning with OOP

**Total Questions:** 20  
**Difficulty Levels:** 4  
**Primary Language:** Python

---

# Level 1 — Beginner (Questions 1–5)

**Focus:** Class, Object, Attributes, Methods and Constructor.

### 1. Student Class

Create a class called `Student`.

Requirements:
- Store student name.
- Store student age.
- Store university name.
- Create an object and print all information.

### 2. Employee Information

Create a class called `Employee`.

Requirements:
- Employee name
- Employee ID
- Monthly salary

Create three employee objects with different information.

### 3. Calculator

Create a class called `Calculator`.

Create four methods:
- `add(a, b)`
- `subtract(a, b)`
- `multiply(a, b)`
- `divide(a, b)`

Create an object and perform all four operations. Handle division by zero.

### 4. Rectangle Area

Create a class called `Rectangle`.

Requirements:
- Store length and width.
- Create a method `calculate_area()`.
- Create another method `calculate_perimeter()`.

Formula:

Area = length × width

Perimeter = 2 × (length + width)

### 5. Car Information

Create a class called `Car`.

Attributes:
- Brand
- Model
- Year
- Speed

Methods:
- `start()`
- `accelerate()`
- `brake()`
- `show_info()`

Create two different car objects.

---

# Level 2 — Intermediate (Questions 6–10)

**Focus:** Instance variables, Class variables, Encapsulation and Methods.

### 6. Bank Account System

Create a class called `BankAccount`.

Attributes:
- Account holder
- Account number
- Balance

Methods:
- `deposit(amount)`
- `withdraw(amount)`
- `check_balance()`

Requirements:
- Do not allow negative deposits.
- Do not allow withdrawals greater than the balance.
- Use encapsulation for the balance.

### 7. University Student Management

Create a class called `University`.

Class variable:
- University name = "Sapienza University"

Instance variables:
- Student name
- Student ID
- Department

Create five student objects.

Print the university name and each student's information.

### 8. Product Inventory

Create a class called `Product`.

Attributes:
- Product name
- Price
- Quantity

Methods:
- `calculate_total_value()`
- `update_quantity()`
- `apply_discount()`

Example:

```python
product = Product("Laptop", 1000, 5)
```

Calculate the total inventory value.

### 9. Library Management System

Create two classes:

**Book:**
- Title
- Author
- ISBN
- Availability

**Library:**
- Store multiple books.
- Add a book.
- Borrow a book.
- Return a book.
- Display available books.

### 10. Employee Salary Management

Create a class called `Employee`.

Attributes:
- Name
- Basic salary
- Bonus

Methods:
- `calculate_total_salary()`
- `display_salary()`

Use a class variable to count how many employee objects have been created.

---

# Level 3 — Advanced OOP (Questions 11–15)

**Focus:** Inheritance, Polymorphism, Abstraction and Method Overriding.

### 11. Animal Inheritance

Create a parent class called `Animal`.

Methods:
- `eat()`
- `sleep()`
- `sound()`

Create three child classes:
- Dog
- Cat
- Cow

Override the `sound()` method in each child class.

### 12. Vehicle Management System

Create a parent class called `Vehicle`.

Attributes:
- Brand
- Model
- Speed

Methods:
- `start()`
- `stop()`

Create child classes:
- Car
- Motorcycle
- Truck

Each child class should have its own additional method.

### 13. Shape Polymorphism

Create a parent class called `Shape`.

Create three child classes:
- Circle
- Rectangle
- Triangle

Each class should have a method called:

```python
calculate_area()
```

Use polymorphism to calculate the area of all three shapes.

### 14. Payment System — Abstraction

Use Python's `abc` module.

Create an abstract class called `Payment`.

Abstract method:

```python
process_payment()
```

Create three child classes:
- CreditCardPayment
- PayPalPayment
- BankTransferPayment

Each child class must implement its own payment method.

### 15. Online Shopping System

Create three classes:

**Customer:**
- Name
- Email

**Product:**
- Name
- Price
- Stock

**ShoppingCart:**
- Add product.
- Remove product.
- Calculate total price.
- Display cart items.

Requirements:
- Prevent adding products with zero stock.
- Support multiple products.
- Calculate the final amount.

---

# Level 4 — Real-world Python and ML OOP (Questions 16–20)

**Focus:** Reusable classes, composition, exception handling and ML integration.

### 16. Student Grade Prediction

Create a class called `Student`.

Attributes:
- Name
- Study hours
- Previous exam score

Methods:
- `calculate_average()`
- `predict_score()`
- `display_result()`

For this exercise, use a simple formula to estimate the score. This is not actual machine learning.

### 17. Dataset Management System

Create a class called `DatasetManager`.

Requirements:
- Load a CSV file using pandas.
- Display the first five rows.
- Display dataset shape.
- Check missing values.
- Remove duplicate rows.

Use exception handling for:
- `FileNotFoundError`
- `pd.errors.ParserError`
- Invalid dataset conditions.

### 18. Machine Learning Model Class

Create a class called `MLModel`.

Requirements:
- Initialize a `LinearRegression` model.
- Create a `train()` method.
- Create a `predict()` method.
- Create an `evaluate()` method.

Use:

```python
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error
```

Train your model using sample data.

### 19. Multiple ML Models

Create a parent class called `BaseModel`.

Methods:
- `train(X, y)`
- `predict(X)`

Create two child classes:

- `LinearRegressionModel`
- `RandomForestModel`

Each child class should use its own Scikit-learn algorithm.

Requirements:
- Override training and prediction methods if necessary.
- Use polymorphism to call the models.
- Compare their predictions.

### 20. Mini Project — Student Performance Prediction System

Build a complete student performance prediction system using OOP.

Your system should contain at least four classes:

| Class | Responsibility |
|---|---|
| `Student` | Store student information |
| `DatasetManager` | Load and preprocess data |
| `MLModel` | Train and predict |
| `PerformanceAnalyzer` | Analyze model results |

Requirements:

1. Load a student dataset using pandas.
2. Handle missing values.
3. Separate features and target.
4. Split training and testing data.
5. Train a Linear Regression model.
6. Predict exam scores.
7. Calculate Mean Squared Error.
8. Handle exceptions.
9. Organize everything using OOP.
10. Display the final results.

---

# Recommended Learning Order

| Level | Questions | Main Topics |
|---|---|---|
| Beginner | 1–5 | Classes, Objects, Constructors |
| Intermediate | 6–10 | Encapsulation, Variables, Methods |
| Advanced | 11–15 | Inheritance, Polymorphism, Abstraction |
| ML Projects | 16–20 | Pandas, Scikit-learn, Exception Handling |

# Important Instructions

1. Write the code yourself without looking at solutions.
2. Test each class by creating multiple objects.
3. Try invalid inputs and handle exceptions.
4. Explain what `self`, `__init__()` and each method does.
5. For questions 11–20, try implementing the same concept in Java too.

## Learning Goal

By completing these 20 assignments, you should be able to:

- Understand and implement Python OOP concepts.
- Design reusable classes and objects.
- Apply the four pillars of OOP.
- Build small real-world applications.
- Organize Machine Learning projects using OOP.
- Understand similarities and differences between Python and Java OOP.

**Challenge:** Complete all 20 assignments independently. Focus on understanding the logic rather than memorizing the code.

**Practice makes programming stronger!** 🚀
