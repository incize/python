# Python String Methods (A to Z)

A complete reference of Python's built-in string methods, in alphabetical order.

> **Note:** Strings are **immutable**. No method changes the original string. Each one returns a **new** value.

```python
s = "hello"
s.upper()   # 'HELLO'
print(s)    # hello (original is unchanged)
```

## All Methods (A to Z)

| # | Method | Description | Example | Output |
|---|--------|-------------|---------|--------|
| 1 | `capitalize()` | First character uppercase, the rest lowercase | `"hello world".capitalize()` | `'Hello world'` |
| 2 | `casefold()` | Aggressive lowercase, used for caseless comparison | `"Straße".casefold()` | `'strasse'` |
| 3 | `center(width, fillchar)` | Centers the string and pads both sides | `"hi".center(10, "-")` | `'----hi----'` |
| 4 | `count(sub)` | Counts occurrences of a substring | `"banana".count("a")` | `3` |
| 5 | `encode(encoding)` | Converts the string to bytes (default utf-8) | `"hi".encode()` | `b'hi'` |
| 6 | `endswith(suffix)` | True if the string ends with the suffix | `"file.py".endswith(".py")` | `True` |
| 7 | `expandtabs(tabsize)` | Replaces tab characters with spaces | `"a\tb".expandtabs(4)` | `'a   b'` |
| 8 | `find(sub)` | Index of first match, or -1 if not found | `"hello".find("l")` | `2` |
| 9 | `format()` | Fills `{}` placeholders with values | `"{} is {}".format("Sam", 20)` | `'Sam is 20'` |
| 10 | `format_map(dict)` | Like `format()`, but takes values from a dict | `"{a} and {b}".format_map({"a": 1, "b": 2})` | `'1 and 2'` |
| 11 | `index(sub)` | Like `find()`, but raises `ValueError` if not found | `"hello".index("e")` | `1` |
| 12 | `isalnum()` | True if all characters are letters or digits | `"abc123".isalnum()` | `True` |
| 13 | `isalpha()` | True if all characters are letters | `"abc1".isalpha()` | `False` |
| 14 | `isascii()` | True if all characters are ASCII | `"abc".isascii()` | `True` |
| 15 | `isdecimal()` | True if all characters are decimal digits (0-9) | `"123".isdecimal()` | `True` |
| 16 | `isdigit()` | True if all characters are digits (includes `²`) | `"12a".isdigit()` | `False` |
| 17 | `isidentifier()` | True if the string is a valid Python identifier | `"my_var".isidentifier()` | `True` |
| 18 | `islower()` | True if all cased letters are lowercase | `"hello".islower()` | `True` |
| 19 | `isnumeric()` | True if all characters are numeric (includes `½`) | `"½".isnumeric()` | `True` |
| 20 | `isprintable()` | True if all characters are printable | `"hi\n".isprintable()` | `False` |
| 21 | `isspace()` | True if the string contains only whitespace | `"   ".isspace()` | `True` |
| 22 | `istitle()` | True if the string is in title case | `"Hello World".istitle()` | `True` |
| 23 | `isupper()` | True if all cased letters are uppercase | `"HELLO".isupper()` | `True` |
| 24 | `join(iterable)` | Joins items of an iterable using the string as separator | `"-".join(["a", "b", "c"])` | `'a-b-c'` |
| 25 | `ljust(width, fillchar)` | Left-aligns and pads on the right | `"hi".ljust(5, "*")` | `'hi***'` |
| 26 | `lower()` | Converts all letters to lowercase | `"HeLLo".lower()` | `'hello'` |
| 27 | `lstrip()` | Removes whitespace from the left | `"  hi  ".lstrip()` | `'hi  '` |
| 28 | `maketrans(x, y)` | Builds a mapping table for `translate()` | `str.maketrans("abc", "123")` | mapping table |
| 29 | `partition(sep)` | Splits at the first `sep` into a 3-tuple | `"a=b=c".partition("=")` | `('a', '=', 'b=c')` |
| 30 | `removeprefix(prefix)` | Removes the prefix if present (Python 3.9+) | `"test_file".removeprefix("test_")` | `'file'` |
| 31 | `removesuffix(suffix)` | Removes the suffix if present (Python 3.9+) | `"file.py".removesuffix(".py")` | `'file'` |
| 32 | `replace(old, new)` | Replaces all occurrences of `old` with `new` | `"cat".replace("c", "b")` | `'bat'` |
| 33 | `rfind(sub)` | Index of last match, or -1 if not found | `"hello".rfind("l")` | `3` |
| 34 | `rindex(sub)` | Like `rfind()`, but raises `ValueError` if not found | `"hello".rindex("l")` | `3` |
| 35 | `rjust(width, fillchar)` | Right-aligns and pads on the left | `"hi".rjust(5, "*")` | `'***hi'` |
| 36 | `rpartition(sep)` | Splits at the last `sep` into a 3-tuple | `"a=b=c".rpartition("=")` | `('a=b', '=', 'c')` |
| 37 | `rsplit(sep, maxsplit)` | Like `split()`, but splits from the right | `"a,b,c".rsplit(",", 1)` | `['a,b', 'c']` |
| 38 | `rstrip()` | Removes whitespace from the right | `"  hi  ".rstrip()` | `'  hi'` |
| 39 | `split(sep)` | Splits into a list (default separator is whitespace) | `"a b c".split()` | `['a', 'b', 'c']` |
| 40 | `splitlines()` | Splits at line breaks | `"a\nb\nc".splitlines()` | `['a', 'b', 'c']` |
| 41 | `startswith(prefix)` | True if the string starts with the prefix | `"hello".startswith("he")` | `True` |
| 42 | `strip()` | Removes whitespace from both ends | `"  hi  ".strip()` | `'hi'` |
| 43 | `swapcase()` | Swaps uppercase and lowercase | `"HeLLo".swapcase()` | `'hEllO'` |
| 44 | `title()` | First letter of every word uppercase | `"i love python".title()` | `'I Love Python'` |
| 45 | `translate(table)` | Replaces characters using a `maketrans()` table | `"aabbcc".translate(str.maketrans("abc", "123"))` | `'112233'` |
| 46 | `upper()` | Converts all letters to uppercase | `"hi".upper()` | `'HI'` |
| 47 | `zfill(width)` | Pads with zeros on the left | `"42".zfill(5)` | `'00042'` |

## Quick Groups

| Category | Methods |
|----------|---------|
| Change case | `capitalize` `casefold` `lower` `upper` `swapcase` `title` |
| Search and count | `count` `find` `index` `rfind` `rindex` `startswith` `endswith` |
| Check (True/False) | `isalnum` `isalpha` `isascii` `isdecimal` `isdigit` `isidentifier` `islower` `isnumeric` `isprintable` `isspace` `istitle` `isupper` |
| Padding and alignment | `center` `ljust` `rjust` `zfill` `expandtabs` |
| Trim and clean | `strip` `lstrip` `rstrip` `removeprefix` `removesuffix` |
| Split and join | `split` `rsplit` `splitlines` `partition` `rpartition` `join` |
| Replace and translate | `replace` `translate` `maketrans` |
| Formatting | `format` `format_map` |
| Encoding | `encode` |

## Method Chaining

The result of one method can be passed straight to another:

```python
s = "  Hello World  "
print(s.strip().upper().replace("WORLD", "PYTHON"))   # HELLO PYTHON
```