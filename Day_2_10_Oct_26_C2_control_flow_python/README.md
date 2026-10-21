# Python Basics: Conditions and Loops

Beginner-friendly notes on `if`, `elif`, `else`, `range()`, and the loop-control statements `pass`, `continue`, and `break`.

## 1. `if`, `elif`, and `else`

Conditional statements let a program make decisions based on whether a condition is `True` or `False`.

```python
marks = 70

if marks >= 90:
    print("Grade A")
elif marks >= 70:
    print("Grade B")
elif marks >= 50:
    print("Grade C")
else:
    print("Learn more")
```

**Output**
```text
Grade B
```

### How it works

- `if` checks the first condition.
- `elif` means “else if”. Python checks it only if the previous conditions were false.
- `else` runs if none of the earlier conditions were true.
- The first matching branch runs; Python skips the remaining branches.

For `marks = 70`, `marks >= 90` is false, but `marks >= 70` is true, so the output is `Grade B`.

**Remember:** Indentation matters in Python. The statements belonging to a condition must be indented.

## 2. Loops and `range()`

A `for` loop repeats a block of code for each value in a sequence. `range()` generates a sequence of integers.

### `range(stop)`

Starts at `0` and stops **before** `stop`.

```python
for i in range(5):
    print(i)
```

**Output**
```text
0
1
2
3
4
```

### `range(start, stop)`

Starts at `start` and stops **before** `stop`.

```python
for i in range(1, 6):
    print(i)
```

**Output**
```text
1
2
3
4
5
```

### `range(start, stop, step)`

The third argument is called `step`. It determines how much the number changes each time; it is not a condition.

```python
for i in range(2, 10, 2):
    print(i)
```

**Output**
```text
2
4
6
8
```

Here, `start = 2`, `stop = 10`, and `step = 2`. The loop adds `2` each time and stops before `10`.

You can also count backward with a negative step:

```python
for i in range(5, 0, -1):
    print(i)
```

**Output**
```text
5
4
3
2
1
```

## 3. `pass`, `continue`, and `break`

These statements have different purposes when used inside loops.

### A. `pass` — do nothing

`pass` is a placeholder statement. It does not skip the loop iteration or stop the program; execution simply continues with the next statement.

```python
for i in range(1, 6):
    if i == 3:
        pass
    print(i)
```

**Output**
```text
1
2
3
4
5
```

When `i == 3`, Python executes `pass` (which does nothing), then continues to `print(i)`. That is why `3` is still printed.

A common use is to leave a block empty temporarily while planning code:

```python
def future_feature():
    pass  # Implement this function later
```

### B. `continue` — skip to the next iteration

`continue` skips the rest of the current loop iteration and moves to the next value.

```python
for i in range(1, 6):
    if i == 3:
        continue
    print(i)
```

**Output**
```text
1
2
4
5
```

When `i == 3`, `print(i)` is skipped.

### C. `break` — stop the loop

`break` immediately exits the nearest enclosing loop.

```python
for i in range(1, 6):
    if i == 3:
        break
    print(i)
```

**Output**
```text
1
2
```

When `i == 3`, the loop ends, so `4` and `5` are never reached.

### Quick comparison

| Statement | Meaning | What happens in the loop? |
|---|---|---|
| `pass` | Do nothing | The loop continues normally |
| `continue` | Skip this iteration | Moves to the next iteration |
| `break` | Stop the loop | Exits the loop immediately |

## 🧠 Quick Revision

- `if` checks a condition; `elif` checks another condition; `else` handles the remaining case.
- `range(stop)` starts at `0` and excludes `stop`.
- `range(start, stop)` starts at `start` and excludes `stop`.
- `range(start, stop, step)` changes by `step` each time.
- `pass` is a placeholder and does not skip printing by itself.
- `continue` skips the rest of the current iteration.
- `break` exits the loop.

## ✍️ Practice Exercises

1. Set `marks = 85` and write conditions to print `Grade A`, `Grade B`, `Grade C`, or `Learn more`.
2. Use `range()` to print numbers from `1` to `10`.
3. Use `range()` to print even numbers from `2` to `20`.
4. Print numbers from `1` to `10`, but skip `5` using `continue`.
5. Print numbers from `1` to `10`, but stop when the number reaches `6` using `break`.
6. Use `pass` inside an `if` block and observe why the following `print()` still runs.
