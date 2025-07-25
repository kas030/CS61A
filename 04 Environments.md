# Environments

## Environments for Higher-Order Functions

Higher-Order function: A function that takes a function as an argument value or return a function as a return value.

```python
def apply_twice(f, x):
    return f(f(x))
    
def square(x):
    return x * x
    
result = apply_twice(square, 2)
```

@import "img/environments-01.png" {width=500}

## Environments for Nested-Definitions

E.g.:

```python
def make_adder(n):
    def adder(k):
        return k + n
    return adder

add_three = make_adder(3)
result = add_three(4)
```

@import "img/environments-02.png" {width=500}

Every user-defined function has a parent frame(often global).
The parent of a function is the frame in which it was defined.

Every local frame has a parent frame(often global).
The parent of a frame is the parent of the function called.

## Local Names

```python
def f(x, y):
    return g(x)
    
def g(a):
    return a + y
    
result = f(1, 2)
```

This will cause an error, because the name `y` cannot be found in the global frame.

## Function Composition

```python
def make_adder(n):
    def adder(k):
        return n + k
    return adder
    
def square(x):
    return x * x

def triple(x):
    return 3 * x

def compose1(f, g):
    def h(x):
        return f(g(x))
    return h

squiple = compose1(square, triple)
squiple(5)  # Evaluates to 225

tripare = compose1(triple, square)
tripare(5)  # Evaluates to 75

squadder = compose1(square, make_adder(2))
squadder(3)  # Evaluates to 25
compose1(square, make_adder(2))  # The same as above
```

## Lambda Expressions

```python
square = lambda x: x * x
square(10)  # Evaluates to 100
```

## Function Currying

Currying: Transforming a multi-argument function into a single-argument, higher-order function.

```python
def curry2(f):
    def g(x):
        def h(y):
            return f(x, y)
        return h
    return g

curry2(add)(2)(3)  # Evaluates to 5
```

We can also write it like this:

```python
curry2 = lambda f: lambda x: lambda y: f(x, y)
```
