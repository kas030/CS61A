# Control

## Multiple Environments

@import "img/control-01.png" {width=280}

@import "img/control-02.png" {width=460}

An environment is a sequence of frames.
In the case above, there's 3 environments.

- The global frame
- f1, followed by the global frame
- f2, followed by the global frame

Names has no meanings without these environments.

## Miscellaneous Python Features

### Division

There are two kinds of division:

- True division, `/`
- Integer division, `//`

These have corresponding functions in the `operator` module:

- `truediv`
- `floordiv`

And `%` gives the remainder of division. The corresponding function is `mod`.

### Return Multiple Values from a Function

```shell
>>> def divide_exact(n, d):
... return n//d, n%d
...
>>> quotient, remainder = divide_exact(2013, 10)
>>> quotient
2013
>>> remainder
3
```

### Interactive Mode

```shell
python3 -i *.py
```

### Doc Test

It is suggested to use cap letters to refer to the formal parameters in comments.

```python
def divide_exact(n, k):
    """Return the quotient and remainder of dividing N by D.
    
    >>> q, r = divide_exact(2013, 10)
    >>> q
    201
    >>> r
    3
    """
    return q // r, q % r
```

Then we can type `python3 -m doctest test.py` in the terminal to test  the code. If everything does what it is supposed to do, we will see no output.
If we want to see more information, we can use `python3 -m doctest -v test.py`, which will tell us everything that happen.

### Default Values

```python
def <function name>(<formal parameter> = <default value>)
```

## Conditional Statements

Compound statements have a structure like this:

@import "img/control-03.png" {width=370}

The first statements determines a statement's type. The header of a clause 'controls' the suite that follows. Def statements are compound statements.

```python
if <condition>:
    ...
elif <condition>:
    ...
else:
    ...
```

There can be zero or one 'else' clause in the end.

### Boolean Context

False values in python:

- `False`
- `0`
- Empty string
- `None`

## Iteration

### While Statement

```python
while <condition>:
    ...
```
