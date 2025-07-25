# Recursion

## Self-Reference

```python
def print_all(x):
    print(x)
    return print_all

print_all(1)(3)(5)
```

The output is:

```shell
1
3
5
```

A more complicated example:

```python
def print_sums(x):
    print(x)
    def next_sum(y):
        return print_sums(x + y)
    return next_sum

print_sums(1)(3)(5)
```

The output is:

```shell
1
4
9
```

The environment diagram of the code above is:

@import "img/recursion-01.png" {width=400}

Notice that the function `next_sums` was defined 3 times.

## Recursive Functions

Definition: A function is called recursive if the body of that function calls itself, either directly or indirectly.

## Mutual Recursion

### The Luhn Algorithm

The Luhn sum of a valid credit card number is a multiple of 10.

How to compute:

1. From the right most digit, which is the check digit, moving left, double the value of every second digit; if product of this doubling operation is greater than 9, then sum the digits of the products.
2. Take the sum of all the digits.

```python
def split(n):
    return n // 10, n % 10

def sum_digits(n):
    if n < 10:
        return n
    else:
        return all_but_last, last = split(n)
        return sum_digits(all_but_last) + last

def luhn_sum(n):
    if n < 10:
        return n
    else:
        all_but_last, last = split()
        return luhn_sum_double(all_but_last) + last

def luhn_sum_double(n):
    all_but_last, last = split()
    luhn_digit = sum_digits(2 * last)
    if n < 10:
        return luhn_digit
    else:
        return luhn_sum(all_but_last) + luhn_digit
```
