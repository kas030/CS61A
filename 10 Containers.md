# Containers

## Box-and-Pointer Notation

Box-and-pointer notation is a way to represent a list without environment diagrams.

### The Closure Property of Data Types

- A method for combining data values satisfies the **closure property** if: The result of combination can itself be combined using the same method
- Closure is powerful because it permits us to create hierarchical structures
- Hierarchical structures are made up of parts, which themselves are made up of parts, and so on

### Box-and-Pointer Notation in Environment Diagrams

Lists are presented as a row of index-labeled adjacent boxes, one per element.
Each box either contains a primitive value or points to a compound value.

A complicated example of nested lists represented by box-and-pointer notation:

```python
pair = [1, 2]
nested_list = [[1, 2], [], [[2, False, None], [4, lambda: 5]]]
```

@import "img/containers-01.png" {width=550px}

## Slicing

Slicing is an operation that we can perform on sequences, such as lists and ranges.

`[:]` is the slicing operator.

```python
a = [1, 2, 3, 4, 5]
a[1:3]  # [2, 3]
a[:3]   # [1, 2, 3]
a[1:]   # [2, 3, 4, 5]
a[:]    # [1, 2, 3, 4, 5]
```

## Processing Container Values

### Sequence Aggregation

Several built-in functions take iterable arguments and aggregate then into a new value.

#### Sum

`sum(iterable[, start]) -> value`

Return the sum of an iterable of numbers (NOT strings) plus the value of parameter `start` (which defaults to `0`). When the iterable is empty, return start.

E.g.:

```python
sum([2, 3, 4])  # 9
sum([[2, 3], [4]], [])  # [2, 3, 4]
```

#### Max

`max(iterable[, key=func]) -> value`

`max(a, b, c, ...[, key=func]) -> value`

With a single iterable argument, return its largest item.
With two or more arguments, return the largest argument.
The `key` parameter: It applies a function to every element that are being considered, and actually computes the maximum based on the values of calling those functions.

E.g.:

```python
max(range(5))  # 4
max(0, 1, 2, 3, 4)  # 4
max(range(10), key=lambda x: 7 - (x - 4) * (x - 2))  # 3
```

#### All

`all(iterable) -> bool`

Return `True` if `bool(x)` is `True` for all values `x` in the iterable. If the iterable is empty, return `True`.

E.g.

```python
all([x < 5 for x in range(5)])  # True
```

There's also `min` and `any`, which are complements to `max` and `all`.

## Strings

The function `exec` can execute the code stored in a string.

### String literals

```python
'I am string!'
"I'm string!"
"""The Zen of Python
claims, Readability counts.
Read more, import this."""
```

Single-quoted and double-quoted strings are equivalent except for that we can put an apostrophe in the double-quoted string, but it will not work on single-quoted strings, which will end string.

A triple-quoted string can span multiple lines. We often use it for docstrings.

### String are Sequences

Length and element selection are similar to all sequences.
However, the `in` and `not in` operators **match substrings**.

## Dictionaries

Looking up values by their keys uses the element selection operator.

```python
numerals = {"I": 1, "V": 5, "X": 10}
numerals["I"]  # 1
numerals["V"]  # 5
numerals["X"]  # 10
```

Dictionaries are also **sequences**. In particular, they are sequences of keys. This means we can use dictionaries inside of a for statement to go through all of the keys.

```python
list(numerals)  # ["I", "V", "X"]
```

Dictionaries support various methods of iterating over the contents. The methods `keys`, `values`, and `items` all return iterable values. Although their return values are not a list, we can sum them up or iterate through them using a for statement. If for some reason we really need a list, we can call the method `list` on them to get a list.

```shell
>>> numerals.keys()
dict_keys(['I', 'V', 'X'])
>>> numerals.values()
dict_values([1, 5, 10])
>>> numerals.items()
dict_items([('I', 1), ('V', 5), ('X', 10)])
>>> list(numerals.keys())
['I', 'V', 'X']
```

Dictionaries can be constructed with no elements.

```python
d = {}
```

Two important **restrictions** about the keys of a dictionary:

- There can be at most one value for a given key.
- The key itself cannot be a list or a dictionary (or any mutable type).

```python
>>> {1: "first", 1: "second"}
{1: 'second'}
>>> {[1]: "first"}
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unhashable type: 'list'
```

### Dictionary Comprehensions

Dictionaries also have a comprehension syntax analogous to those of lists.

```python
{<key exp>: <value exp> for <name> in <iter exp>[ if <filter exp>]}
```

An expression that evaluates to a dictionary using this evaluation procedure:

1. Add a new frame with the current frame as its parent
2. Create an empty result dictionary that is the value of the expression
3. For each element in the iterable value of `<iter exp>`:
   1. Bind `<name>` to that element in the new frame from step 1
   2. If `<filter exp>` evaluates to a true value, then add to the result dictionary an entry that pairs the value of `<key exp>` to the value of `<value exp>`

#### Example: Indexing

```python
def index(keys, values, match):
    """Return a dictionary from keys k to a list of values v for which match (k, v) is a true value.
    
    >>> index([7, 9, 11], range(30, 50), lambda k, v: v % k == 0)
    {7: [35, 42, 49], 9: [36, 45], 11: [33, 44]}
    """
    
    return {k: [v for v in values if match(k, v)] for k in keys}
```
