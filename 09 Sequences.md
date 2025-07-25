# Sequences

## Lists

Bind a list literal to a name:

```python
a = [1, 2, 3]
```

To get the number of elements, we can use the built-in function `len`:

```python
a =  [1, 2, 3]
len(a)  # Evaluates to 3
```

If we want to get an element selected by its index, we can use the element selection syntax or the `getitem` function in the `operator` module:

```python
from operator import *
a = [1, 2, 3]
a[0]  # Evaluates to 1
getitem(a, 0)  # The same as above
```

Concatenation and repetition:

```python
a = [1, 2, 3]
[4, 5] * 2 + a  # Evaluates to [4, 5, 4, 5, 1, 2, 3]
```

## Containers

The built-in operator `in` can test whether an element appears in a compound value.

```python
a = [1, 2, 3]
1 in a       # True
5 not in a   # True
not(5 in a)  # Equivalent to the above
[1, 2] in a  # False
[1, 2] in [[1, 2], 3]  # True
```

## For Statements

### Sequence Iteration

```python
def count(s, value):
    total = 0
    for element in s:
        if element == value:
            total += 1
    return total
```

The name `element` is bound in the first frame of the current environment. No new frames were introduced to the for statement.

### For Statement Execution Procedure

```python
for <name> in <expression>:
    <suite>
```

1. Evaluate the header `<expression>`, which must yield an iterable value.
2. For each element in that sequence, in order:
   1. Bind `<name>` to that element in the current frame.
   2. Execute the `<suite>`.

```python
for i in [1, 2, 3]:
    print(i)
print(i)
```

The output of the code above is:

```shell
1
2
3
3
```

### Sequence Unpacking in For Statement

Sequence unpacking works for a sequence of **fixed-length** sequence.

```python
pairs = [[1, 2], [2, 2], [3, 2], [4, 4]]
same_count = 0

for x, y in pairs:
    if x == y:
        same_count += 1

print(same_count)  # Output: 2
```

## Ranges

Ranges are another sequence type to represent consecutive integers.

To convert ranges to lists, we can call the list constructor `list`, a built-in function. When we call it on any other sequence, it gives us back a list full of the elements of that sequence.

There are cases when we actually don't care about the integers themselves. A typical way to write that is a for statement like this:

```python
for _ in range(n):
    <suite>
```

## List Comprehensions

A list comprehension takes an existing list and computes a new list from it according to some expressions.

```python
letters = ['a', 'b', 'c', 'd', 'e']
[letters[i] for i in [0, 2, 4]]  # Evaluates to ['a', 'c', 'e']

odds = [1, 3, 5, 7, 9]
[x + 1 for x in odds]  # Evaluates to [2, 4, 6, 8, 10]
[x for x in odds if 25 % x == 0]  # Evaluates to [1, 5]

def divisors(n):
    return [1] + [x for x in range(2, n) if n % x == 0]
divisors(12)  # Evaluates to [1, 2, 3, 4, 6]
```

## Lists, Slices, & Recursion

For any list `s`, the expression `s[1:]` is called a slice from index 1 to the end (or 1 onward).
