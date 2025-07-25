# Representation

## String Representations

In Python, all objects produce two string representations:

- The `str` is legible to humans.
- The `repr` is legible to the Python interpreter.

The `repr` function returns a Python expression that evaluates to an equal object.

`repr(object) -> string`: Return the canonical string representation of the object.
For most object types, `eval(repr(object)) == object`.

The result of calling `repr` on a value is what Python prints in an interactive session.

```python
>>> 12e3
12000.0
>>>print(repr(12e3))
12000.0
```

Some objects do not have a simple Python-readable string.

```python
>>> repr(min)
'<built-in function min>'
```

The result of calling `str` on teh value of an expression is waht Python prints using `print` function:

```python
>>> from fractions import Fraction
>>> half = Fraction(1, 2)
'Fraction(1, 2)'
>>> str(half)
'1/2'
>>> print(half)
1/2
```

## String Interpolation

String interpolation involves evaluating a string literal that contains expressions. Sub-expressions in an f-string are evaluated in the current environment.

```python
>>> f'pi starts with {pi}...'
'pi starts with 3.141592653589793...'
```

The result of evaluating an f-string expression is the str string of the values of the sub-expressions.

```python
>>> repr(half * half)
'Fraction(1, 4)'
>>> f'{half * half}'
'1/4'
```

## Polymorphic Functions

Polymorphic function: A function that applies to many (*poly*) different forms (*morph*) of data.

`str` and `repr` are both polymorphic.
`repr` invokes a zero-argument method `__repr__` on its argument. `str` invokes a zero-argument method `__str__` on its argument.

```python
>>> half.__repr__()
'Fraction(1, 2)'
>>> half.__str__()
'1/2'
```

The behavior of `repr` is slightly more complicated than invoking `__repr__` on its argument:

- An instance attribute called `__repr__` is ignored.
- Only class attributes are found.

```python
def repr(x):
    return type(x).__repr__(x)
```

The behavior of `str` is also complicated:

- An instance attribute called `__str__` is ignored.
- If no `__str__` attribute is found, uses repr string.

### Interface

Message passing: Objects interact by looking up attributes on each other.

The attribute look-up rules allow different data types to respond to the same message. A shared message (attribute name) that elicits similar behavior from different data types is called an interface, along with the its expected behavior.

```python
class Ratio:
    def __init__(self, n, d):
        self.numer = n
        self.denom = d

    def __repr__(self):
        return "Ratio({0}, {1})".format(self.numer, self.denom)

    def __str__(self):
        return "{0}/{1}".format(self.numer, self.denom)
```

```python
>>> half = Ratio(1, 2)
>>> print(half)
1/2
>>> half
Ratio(1, 2)
```

## Special Method Names

Special method names are used to implement the behavior of built-in functions and operators. These names always start and end with double underscores.

|Names|Behaviors|
|---|---|
|`__init`| Method invoked automatically when an object is constructed.|
|`__repr__`| Method invoked to display an object as a Python expression.|
|`__str__`| Method invoked to display an object as a string.|
|`__add__`| Method invoked to add one object to another.|
|`__bool__`| Method invoked to convert an object to a boolean value.|

```python
>>> a, b = 1, 2
>>> a.__add__(b)
3
>>> a.__bool__()
True
```

Extend the `Ratio` class:

```python
class Ratio:
    def __init__(self, n, d):
        self.numer = n
        self.denom = d

    def __repr__(self):
        return "Ratio({0}, {1})".format(self.numer, self.denom)

    def __str__(self):
        return "{0}/{1}".format(self.numer, self.denom)

    def __add__(self, other):
        if isinstance(other, int):
            n = self.numer + other * self.denom
            d = self.denom
        elif isinstance(other, Ratio):
            n = self.numer * other.denom + other.numer * self.denom
            d = self.denom * other.denom
        elif isinstance(other, float):
            return float(self) + other
        g = gcd(n, d)
        return Ratio(n // g, d // g)

    __radd__ = __add__

    def __float__(self):
        return self.numer / self.denom
```

`isinstance`: Returns whether an object is an instance of a class or a subclass thereof.

