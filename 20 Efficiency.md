# Efficiency

## Measuring Efficiency

```python
def count(f):
    def counted(*args, **kwargs):
        counted.count += 1
        return f(*args, **kwargs)

    counted.count = 0
    return counted
```

About `counted.count`:

- In Python, functions are first-class objects, meaning they can have attributes.
- `counted` is a closure and `counted.count` is not a variable captured by the closure. Instead, it is an attribute of the `counted` function itself, so it can be accessed as `counted.count` outside the function.

## Memoization

```python
def memoize(f):
    cache = {}
    def memoized(*args):
        if args not in cache:
            cache[args] = f(*args)
        return cache[args]
    return memoized
```
