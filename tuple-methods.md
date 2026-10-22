# Python Tuple Methods (English Notes)

A tuple is an **ordered, immutable** sequence. Once created, you cannot add, remove or change its elements. Because of that, tuples have only **2 methods**: `count()` and `index()`.

```python
t = (10, 20, 30)
```

## Quick Table

| # | Method | What it does | Returns |
|---|--------|--------------|---------|
| 1 | `count(x)` | Counts how many times `x` appears | `int` |
| 2 | `index(x)` | Returns the index of the first `x` | `int` |

Verify yourself:

```python
print([m for m in dir(tuple) if not m.startswith("__")])
# ['count', 'index']
```

---

## 1. `count(x)`

```python
t = (1, 2, 2, 3, 2)
print(t.count(2))   # 3
print(t.count(9))   # 0  (not found gives 0, not an error)
```

## 2. `index(x)`

```python
t = ("a", "b", "c", "b")
print(t.index("b"))      # 1  (first match)
print(t.index("b", 2))   # 3  (start searching from index 2)

# t.index("z")           # ValueError: not found
```

Like list `index()`, it raises an error when the value is missing (it does not return `-1` like a string's `find()`).

---

# Creating Tuples

```python
a = (1, 2, 3)
b = 1, 2, 3          # parentheses are optional
c = tuple([1, 2, 3]) # from a list
d = ()               # empty tuple
```

## Single-element tuple (very common trap)

```python
x = (5)
print(type(x))   # <class 'int'>  (NOT a tuple)

y = (5,)
print(type(y))   # <class 'tuple'>  (the comma makes it a tuple)

z = 5,
print(type(z))   # <class 'tuple'>
```

---

# Immutability

```python
t = (10, 20, 30)
# t[0] = 99        # TypeError: tuple does not support item assignment
# t.append(40)     # AttributeError: no such method
```

To "change" a tuple, build a new one:

```python
t = (10, 20, 30)
t = t + (40,)
print(t)   # (10, 20, 30, 40)

t = (99,) + t[1:]
print(t)   # (99, 20, 30, 40)
```

Or convert to a list, edit, and convert back:

```python
lst = list(t)
lst.append(50)
t = tuple(lst)
```

## The nested mutable trap

The tuple itself cannot change, but a **mutable object inside it can**:

```python
t = (1, [2, 3], 4)
t[1].append(99)
print(t)   # (1, [2, 3, 99], 4)
```

---

# Things That Work on Tuples (Same as Lists)

## Indexing and slicing

```python
t = (10, 20, 30, 40, 50)
print(t[0])       # 10
print(t[-1])      # 50
print(t[1:4])     # (20, 30, 40)
print(t[::-1])    # (50, 40, 30, 20, 10)
```

## Operators and built-ins

```python
t = (4, 1, 7, 3)
print(len(t))        # 4
print(min(t))        # 1
print(max(t))        # 7
print(sum(t))        # 15
print(sorted(t))     # [1, 3, 4, 7]  (returns a LIST)
print(7 in t)        # True
print((1, 2) + (3,)) # (1, 2, 3)
print((0,) * 3)      # (0, 0, 0)
```

> `sorted()` always returns a list. Wrap it with `tuple(sorted(t))` to get a tuple back. Tuples have no `sort()` or `reverse()` method.

## Looping

```python
for item in (10, 20, 30):
    print(item)

for i, item in enumerate(("a", "b")):
    print(i, item)
```

---

# Unpacking (the best feature of tuples)

```python
point = (3, 4)
x, y = point
print(x, y)   # 3 4

# swap two variables
a, b = 1, 2
a, b = b, a
print(a, b)   # 2 1

# star unpacking
first, *rest = (1, 2, 3, 4)
print(first)  # 1
print(rest)   # [2, 3, 4]  (a list)

head, *middle, last = (1, 2, 3, 4, 5)
print(middle) # [2, 3, 4]
```

Functions returning multiple values actually return a tuple:

```python
def min_max(nums):
    return min(nums), max(nums)

lo, hi = min_max([4, 1, 9])
print(lo, hi)   # 1 9
```

---

# Tuple vs List

| | List | Tuple |
|---|------|-------|
| Syntax | `[1, 2, 3]` | `(1, 2, 3)` |
| Mutable | Yes | **No** |
| Methods | 11 | **2** |
| Speed / memory | Slightly slower, more memory | Slightly faster, less memory |
| Can be a dict key / set element | No | **Yes** (if all items are hashable) |
| Use when | Data changes | Data is fixed (coordinates, config, return values) |

```python
d = {("web", 80): "nginx", ("db", 5432): "postgres"}
print(d[("web", 80)])   # nginx
```

---

# DevOps Examples

**Fixed config of allowed environments:**

```python
ENVIRONMENTS = ("dev", "staging", "prod")

env = "prod"
if env in ENVIRONMENTS:
    print("valid environment")
```

**Server as (host, port) pairs:**

```python
servers = [("web1", 80), ("web2", 8080), ("db1", 5432)]

for host, port in servers:
    print(f"Checking {host}:{port}")
```

**Splitting an address into a tuple:**

```python
address = "10.0.0.5:8080"
ip, port = address.split(":")
print(ip, port)   # 10.0.0.5 8080
```

**Counting statuses:**

```python
codes = (200, 404, 200, 500, 200, 404)
print(codes.count(200))   # 3
print(codes.count(404))   # 2
```

**`startswith` / `endswith` accept a tuple:**

```python
filename = "deploy.yaml"
print(filename.endswith((".yaml", ".yml")))   # True
```

---

# Common Mistakes

| Mistake | Correct |
|---------|---------|
| `x = (5)` expecting a tuple | `x = (5,)` |
| `t[0] = 1` | Build a new tuple or convert to a list |
| `t.append(4)` | Tuples have no `append`; use `t + (4,)` |
| `t.sort()` | `sorted(t)` (returns a list) |
| `t.index(x)` without checking | `if x in t:` first |
| Thinking nested lists inside are frozen | They can still change |

---

# Practice Questions

1. Create a tuple `(1, 2, 3, 2, 2)` and find how many times `2` appears and the index of `3`.
2. Create a single-element tuple and verify its `type()`.
3. Swap two variables using tuple unpacking.
4. Given `(1, 2, 3, 4, 5)`, use star unpacking to get the first, last and middle elements.
5. Write a function that returns the min, max and average of a list as a tuple.
6. Convert `(3, 1, 2)` to a sorted tuple.
7. Add `99` to the end of `(1, 2, 3)` (remember: build a new tuple).
8. Given `[("web1", 80), ("db1", 5432)]`, print each as `host:port`.
9. Use a tuple as a dictionary key to store a server's role by `(host, port)`.
10. Check whether a filename ends with `.yaml` or `.yml` using one `endswith()` call.