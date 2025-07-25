# Data Abstraction

An abstract data type let us manipulate compound objects as units.
Data abstraction is a methodology by which function enforce an abstraction barrier between representation and use.

## Example: Rational Numbers

Assume we can compose and decompose rational numbers:

- Constructor:
  - `rational(n, d)`: returns a rational number `x`
- Selectors:
  - `numer(x)`: returns the numerator of `x`
  - `denom(x)`: returns the denominator of `x`

These functions implement an abstract data type for rational numbers. Then we can implement rational number arithmetic:

- `add_rational(x, y)`
- `mul_rational(x, y)`
- `equal_rational(x, y)`

## Representing Rational Numbers

```python
from fractions import gcd

def rational(n, d):
    g = gcd(n, d)
    return [n // g, d // g]

def numer(x):
    return x[0]

def denom(x):
    return x[1]
```

## Abstraction Barrier

The higher we stay up without crossing these boundaries, the easier it will be to change the program in the future.

|Parts of the program that...|Treat rationals as...|Using...|
|:---|:---|:---|
|Use rational numbers to perform computation|whole data values|`add_rational`, `mul_rational`, `equal_rational`, `print_rational`|
|Create rationals or implement rational operations|numerators and denominators|`rational`, `numer`, `denom`|
|Implement constructor and selectors for rationals|two-elements lists|list literals and element selection|

### Violating Abstraction Barriers

```python
add_rational([1, 2], [1, 4])  # Does not use constructors

def divide_rational(x, y):
    return [x[0] * y[1], x[1] * y[0]]  # Does not use selectors
```

## Data Representations

Data abstraction is recognized by its behavior, not necessarily by how it is constructed or how the constructor and selectors is implemented.

In the case below, we changed the implementation of the constructor and selectors of rationals, which still works well with the old code.

```python
def rational(n, d):
    def select(name):
        if name == 'n':
            return n
        elif name == 'd':
            return d
    return select

def numer(x):
    return x('n')

def denom(x):
    return x('d')
```
