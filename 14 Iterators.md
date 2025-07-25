# Iterators

A container can provide an iterator that provides access to its elements in some order.

`iter(<iterable>)`: Return an iterator over the elements of an iterable value.

`next(<iterator>)`: Return the next element in an iterator.

When `next` is called on an iterator which has reached the end, an error will occur.

```python
>>> s = [1, 2, 3, 4, 5]
>>> t = iter(s)
>>> next(t)
1
>>> next(t)
2
>>> list(t)
[3, 4, 5]
```

## For Statements

For statement can iterate over iterators.

```python
>>> r = range(3, 6)
>>> ri = iter(r)
>>> for i in ri:
...     print(i)
... 
3
4
5
```

## Built-In Iterator Functions

Many built-in Python sequence operations return iterators that compute results **lazily**.

|Name|Depict|
|---|---|
|`map(func, iterable)`|Iterate over `func(x)` for `x` in `iterable`|
|`filter(func, iterable)`|Iterate over `x` in iterable if `func(x)` is `True`|
|`zip(first_iter, second_iter)`|Iterate over co-indexed `(x, y)` pairs|
|`reversed(sequence)`|Iterate over `x` in a sequence in reverse order|

To view the contents of an iterator, place the resulting elements into a container. We can use `list(iterable)`, `tuple(iterable)` or `sorted(iterable)`.

## Zip

If one iterator is longer than the other, `zip` only iterated over matches and skips extras.

```python
>>> list(zip([1, 2], [3, 4, 5]))
[(1, 3), (2, 4)]
```

More than two iterables can be passed to `zip`.

```python
>>> list(zip([1, 2], [3, 4, 5], [6, 7]))
[(1, 3, 6), (2, 4, 7)]
```
