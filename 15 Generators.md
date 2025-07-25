# Generators

A generator is a special kind of iterator. It is returned from a generator function.

## Generator Function

A generator function is a function that **yields** values instead of returning them. That computation will be executed **lazily**.

```python
def pos_neg(x):
    yield x
    yield -x

t = pos_neg(3)  # <generator object pos_neg ...>
next(t)  # 3
next(t)  # -3
```

## Generators &  Iterators

A `yield from` statement yields all values from an iterator or iterable (*Python 3.3*).

```python
def a_then_b(a, b):
    yield from a
    yield from b

list(a_then_b([3, 4], [5, 6]))  # [3, 4, 5, 6]

def countdown(k):
    if k > 0:
        yield k
        yield from countdown(k - 1)

list(countdown(3))  # [3, 2, 1]
```

## Example: Partitions

```python
def partitions(n, m):
    if n > 0 and m > 0:
        if n == m:
            yield str(m)
        for p in partitions(n - m, m):
            yield p + " + " + str(m)
        yield from partitions(m, m - 1)
```
