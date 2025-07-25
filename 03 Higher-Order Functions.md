# Higher-Order Functions

## Control Expressions

### Logical Operators

The logical operators exhibit a behavior called 'short-circuiting'.

To evaluate the expressions `<left> and <right>`:

1. Evaluate `<left>`
2. If the result is a false value `v`, then the expression evaluates to `v`
3. Otherwise, the expression evaluates to `<right>`

To evaluates the expression `<left> or <right>`:

1. Evaluate `<left>`
2. If the result is a true value `v`, then the expression evaluates to `v`
3. Otherwise, the expression evaluates to `<right>`

Python's and and or operators short-circuit. That is, they don't necessarily evaluate every operand.

|Operator|Checks if:|Evaluates from left to right up to:|Example|
|---|---|---|---|
|`and`|All values are true|The first false value|`False and 1 / 0` evaluates to False|
|`or`|At least one value is true|The first true value|`True or 1 / 0` evaluates to True|

### Assertion

E.g.:

```python
assert 3 > 2, 'Math is broken.'
assert 2 > 3, 'That is false.'
```

## Higher-Order Functions

E.g.:

```python
from math import pi, sqrt

def area(r, shape_constant):
    assert r > 0, 'A length must ne positive.'
    return r * r *shape_constant

def area_square(r):
    return area(r, 1)

def area_circle(r):
    return area(r, pi)

def area_hexagon(r):
    return area(r, 3 * sqrt(3) / 2)
```

A formal parameter can be bound to a function, so we can pass a function to a function as its argument.

## Functions as Return Values

```python
def make_adder(n):
    """
    
    >>> add3 = make_adder(3)
    >>> add3(4)
    7
    """
    def adder(k):
        return n + k
    return adder
```

We can also use `make_adder(2000)(13)` to get `2013`.
