# Calculator

## Exceptions

### Raise Statements

Python exceptions are raised with a **raise statement**: `raise <exception>`.

`<exception>` must evaluate to a **subclass** of `BaseException` or an **instance** of one.

Exception are constructed like any other object. 
E.g., `TypeError('Bad argument!')`.

Some built-in error types:
- `TypeError`: A function was passed the wrong number/type of argument.
- `NameError`: A name wasn't found.
- `KeyError`: A key wasn't found in a dictionary.
- `RecursionError`: Too many recursive calls.

These exceptions get raised automatically in certain cases and we can also raise them ourselves.

### Try Statements

Try statement handle exceptions, which can prevent a program from terminating.

```python
try:
    <try suite>
except <exception class> as <name>:
    <except suite>
...
```

**Execution rule:**

- The `<try suite>` is executed first.
- If, during the course of executing the `<try suite>`,
an exception is raised that is not handled otherwise,
and if the class of the exception inherits from `<exception class>`,
then the `<except suite>` is executed,
with `<name>` bound to the exception.

## Example: Reduce

Reduce is an important higher-order function which is there to reduce a whole sequence of values to a single value.

There is a built-in version of reduce, but we can also write our own version.

```python
def reduce(f, s, initial): 
    for x in s:
        initial = f(initial, x)
    return initial
```

`f` is a two-argument function,
`s` is a sequence of values that can be the second argument,
`initial` is a value that can be the first argument.

With the `reduce` function, we can complement a `divide_all` function:

```python
def divide_all(n, ds):
    try:
        return reduce(truediv, ds, n)
    except ZeroDivisionError:
        return float('inf')
```

## Parsing

To interpret text as a programming language, we first need to parse that text into some structure that makes it easy to perform interpretation.

A parser takes text and returns an expression.

@import "img/calculator-01.png" {width=500}

Syntactic analysis identifies the hierarchical structure of an expression, which may be nested.
