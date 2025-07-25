# Functional Abstraction

## Lambda Function Environments

```python
a = 1

def f(g):
    a = 2
    return lambda y: a * g(y)

print(f(lambda y: a + y)(a))  # Evaluates to 4
```

## Return

A return statement completes the evaluation of a call expression and provides its value.

```python
def end(n, d):
    """Print the final digits of N in reverse order until D is found.
    
    >>> end (34567, 5)
    7
    6
    5
    """
    while n > 0:
        last, n = n % 10, n // 10
        print(last)
        if d == last:
            return None
```

A more complicated example:

```python
def square(x):
    return x * x

def search(f):
    x = 0
    while not f(x):
        x += 1
    return x
        
def inverse(f):
    # Return g such that g(f(x)) -> x.
    return lambda y: search(lambda x: f(x) == y)
    
sqrt = inverse(square)
sqrt(256)  # Evaluates to 16
```

## Abstraction

- Function abstraction
- Choosing names for functions
- Which values deserve a name
  - Repeat compound expressions
  - Meaningful parts of complex expressions

## Errors and Tracebacks

Errors:

- Syntax errors
- Runtime errors -> Tracebacks
- Logical or behavior errors
