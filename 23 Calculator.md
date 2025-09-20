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