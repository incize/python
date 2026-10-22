# Python List Methods (English Notes)

A list is **mutable**, meaning its elements can be changed after creation. Python lists have **11 methods** in total.

## Quick Table

| # | Method | What it does | Returns |
|---|--------|--------------|---------|
| 1 | `append(x)` | Adds **one** element at the end | `None` |
| 2 | `extend(iterable)` | Adds **many** elements at the end | `None` |
| 3 | `insert(i, x)` | Inserts `x` at index `i` | `None` |
| 4 | `remove(x)` | Removes the first match by **value** | `None` |
| 5 | `pop(i)` | Removes by **index** | The removed element |
| 6 | `clear()` | Removes all elements | `None` |
| 7 | `index(x)` | Returns the index of `x` | `int` |
| 8 | `count(x)` | Counts how many times `x` appears | `int` |
| 9 | `sort()` | Sorts the list (in place) | `None` |
| 10 | `reverse()` | Reverses the list (in place) | `None` |
| 11 | `copy()` | Returns a shallow copy | New list |

> **Watch out:** Most list methods change the list **in place** and return `None`. Writing `lst = lst.append(4)` makes `lst` become `None`.

---

## 1. `append(x)`: add one element at the end

```python
lst = [1, 2, 3]
lst.append(4)
print(lst)   # [1, 2, 3, 4]

lst.append([5, 6])
print(lst)   # [1, 2, 3, 4, [5, 6]]  (the whole list becomes one element)
```

## 2. `extend(iterable)`: add many elements at the end

```python
lst = [1, 2]
lst.extend([3, 4])
print(lst)   # [1, 2, 3, 4]

lst.extend("ab")
print(lst)   # [1, 2, 3, 4, 'a', 'b']
```

**append vs extend:**

```python
a = [1, 2]; a.append([3, 4])   # [1, 2, [3, 4]]
b = [1, 2]; b.extend([3, 4])   # [1, 2, 3, 4]
```

`extend()` always needs **one iterable**. `lst.extend()` (empty) or `lst.extend(5)` raises a `TypeError`.

## 3. `insert(index, x)`: insert at a position

```python
lst = [1, 2, 4]
lst.insert(2, 3)
print(lst)   # [1, 2, 3, 4]

lst.insert(0, 100)
print(lst)   # [100, 1, 2, 3, 4]

lst.insert(999, 7)   # index too large: it is added at the end
print(lst)   # [100, 1, 2, 3, 4, 7]
```

## 4. `remove(x)`: remove by value (first match)

```python
lst = [10, 20, 30, 20]
lst.remove(20)
print(lst)   # [10, 30, 20]  (only the first 20 is removed)

# lst.remove(99)   # ValueError: value not in list
```

Safe way:

```python
if 99 in lst:
    lst.remove(99)
```

## 5. `pop(index)`: remove by index and return the value

```python
lst = [10, 20, 30, 40]
print(lst.pop())     # 40  (default: last element)
print(lst.pop(0))    # 10  (index 0)
print(lst)           # [20, 30]

# [].pop()           # IndexError: cannot pop from an empty list
```

**remove vs pop:**

| | `remove(x)` | `pop(i)` |
|---|---|---|
| You give | a **value** | an **index** |
| Returns | `None` | the removed element |

## 6. `clear()`: remove everything

```python
lst = [1, 2, 3]
lst.clear()
print(lst)   # []
```

## 7. `index(x)`: find the index of a value

```python
lst = ["a", "b", "c", "b"]
print(lst.index("b"))      # 1  (first match)
print(lst.index("b", 2))   # 3  (start searching from index 2)

# lst.index("z")           # ValueError: not found
```

Unlike a string's `find()`, it does not return `-1`. It raises an error.

## 8. `count(x)`: how many times a value appears

```python
lst = [1, 2, 2, 3, 2]
print(lst.count(2))   # 3
print(lst.count(9))   # 0  (not found gives 0, not an error)
```

## 9. `sort()`: sort the list (in place)

```python
nums = [5, 2, 9, 1]
nums.sort()
print(nums)   # [1, 2, 5, 9]

nums.sort(reverse=True)
print(nums)   # [9, 5, 2, 1]
```

Custom sorting with `key`:

```python
words = ["banana", "kiwi", "apple"]
words.sort(key=len)
print(words)   # ['kiwi', 'apple', 'banana']  (sorted by length)

servers = ["web-10", "web-2", "web-1"]
servers.sort()
print(servers)   # ['web-1', 'web-10', 'web-2']  (string order, not numeric order)
```

**`sort()` vs `sorted()`:**

```python
a = [3, 1, 2]
print(sorted(a))   # [1, 2, 3]  (returns a new list, a is unchanged)
print(a)           # [3, 1, 2]

a.sort()           # changes a itself, returns None
print(a)           # [1, 2, 3]
```

## 10. `reverse()`: reverse the list (in place)

```python
lst = [1, 2, 3]
lst.reverse()
print(lst)   # [3, 2, 1]
```

To reverse without changing the original, use slicing:

```python
lst = [1, 2, 3]
print(lst[::-1])   # [3, 2, 1]
print(lst)         # [1, 2, 3]  (original is safe)
```

## 11. `copy()`: make a copy of the list

```python
a = [1, 2, 3]
b = a.copy()
b.append(4)
print(a)   # [1, 2, 3]
print(b)   # [1, 2, 3, 4]
```

**The mistake everyone makes:**

```python
a = [1, 2, 3]
b = a          # NOT a copy: both names point to the same list
b.append(4)
print(a)       # [1, 2, 3, 4]  (a changed too!)
```

Other ways to copy: `a[:]` and `list(a)`.

> `copy()` makes a **shallow copy**. With nested lists (`[[1, 2], [3, 4]]`), the inner lists are still shared.

---

# Useful Things Beyond Methods

## Built-in functions

```python
nums = [4, 1, 7, 3]
print(len(nums))     # 4
print(min(nums))     # 1
print(max(nums))     # 7
print(sum(nums))     # 15
print(sorted(nums))  # [1, 3, 4, 7]
```

## `del`: remove by index or slice

```python
lst = [10, 20, 30, 40, 50]
del lst[0]
print(lst)   # [20, 30, 40, 50]

del lst[1:3]
print(lst)   # [20, 50]
```

## The `in` operator

```python
lst = ["nginx", "redis"]
print("nginx" in lst)       # True
print("mysql" not in lst)   # True
```

## Slicing (same rules as strings)

```python
lst = [10, 20, 30, 40, 50]
print(lst[1:4])    # [20, 30, 40]
print(lst[::-1])   # [50, 40, 30, 20, 10]
print(lst[-2:])    # [40, 50]
```

## `+` and `*`

```python
print([1, 2] + [3, 4])   # [1, 2, 3, 4]
print([0] * 5)           # [0, 0, 0, 0, 0]
```

## List comprehension (shortcut)

```python
squares = [x * x for x in range(5)]
print(squares)   # [0, 1, 4, 9, 16]

evens = [x for x in range(10) if x % 2 == 0]
print(evens)     # [0, 2, 4, 6, 8]
```

## `split()` and `join()` (string to list, list to string)

```python
parts = "a,b,c".split(",")
print(parts)             # ['a', 'b', 'c']
print("-".join(parts))   # a-b-c
```

---

# DevOps Examples

**Parsing a log line:**

```python
log = "2026-10-22 14:32:10 ERROR [nginx] Connection refused to 10.0.0.5:8080"

parts = log.split()
level = parts[2]
service = parts[3][1:-1]
ip, port = parts[-1].split(":")
print(level, service, ip, port)   # ERROR nginx 10.0.0.5 8080
```

**Collecting error lines:**

```python
logs = ["INFO ok", "ERROR db down", "INFO ok", "ERROR disk full"]
errors = []
for line in logs:
    if line.startswith("ERROR"):
        errors.append(line)
print(errors)   # ['ERROR db down', 'ERROR disk full']
```

**Removing duplicates (keeping order):**

```python
servers = ["web1", "db1", "web1", "web2", "db1"]
unique = []
for s in servers:
    if s not in unique:
        unique.append(s)
print(unique)   # ['web1', 'db1', 'web2']
```

---

# Common Mistakes

| Mistake | Correct |
|---------|---------|
| `lst = lst.append(4)` | `lst.append(4)` (it returns `None`) |
| `lst = lst.sort()` | `lst.sort()` or `lst = sorted(lst)` |
| `b = a` thinking it is a copy | `b = a.copy()` |
| `lst.extend(5)` | `lst.extend([5])` or `lst.append(5)` |
| Calling `remove()` on a list while looping over it | Loop over a copy: `for x in lst.copy():` |
| `lst.remove(x)` without checking | Check first: `if x in lst:` |
| `lst[len(lst)]` | `lst[-1]` (last index is `len(lst) - 1`) |

---

# Practice Questions

1. Sort `[5, 3, 8, 1]` in ascending and descending order.
2. Remove duplicates from a list while keeping the order.
3. Find the **second largest** element in a list.
4. Insert `"x"` at index 1 in `["a", "b", "c"]`.
5. Join `[1, 2]` and `[3, 4]` in three different ways (`+`, `extend`, unpacking `[*a, *b]`).
6. Find the **sum of a list without `sum()`** (use a loop).
7. From a list of log lines, build a new list with only the `ERROR` lines.
8. Split a list into **two equal halves** using slicing.
9. Count how many times each element appears, as a dictionary: `["a", "b", "a"]` gives `{'a': 2, 'b': 1}`.
10. Reverse a list without `reverse()` and without `[::-1]` (use a loop).