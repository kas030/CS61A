# Function Examples

## Decorators

```python
def trace(fn):
    """Returns a version of fn that first prints before it is called.
    
    fn - a function of 1 argument
    """
    def traced(x):
        print('Calling', fn, 'on argument', x)
        return fn(x)
    return traced

@trace
def square(x):
    return x * x
```

When we call `square(12)`, we will get the output below:

```shell
Calling <function square at 0x...> on argument 12
```

It is identical to this:

```python
def square(x):
    return x * x
square = trace(square)
```

## Project - Hog: Arbitrary Positional Arguments

Instead of listing formal parameters for a function, we can write `*args`, which represents all of the arguments that get passed into the function.

```python
def printed(f):
    def print_and_return(*args):
        result = f(*args)
        print('Result:', result)
        return result
    return print_and_return
```
