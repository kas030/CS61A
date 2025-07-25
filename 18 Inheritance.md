# Inheritance

Syntax:

```python
class <name>(<base class>):
    <suite>
```

## Inheritance example

```python
>>> ch =CheckingAccount('Tom')
>>> ch.interest  # Lower interest rate
0.01
>>> ch.deposit(20)  # Deposits are the same
20
>>> ch.withdraw(5)  # Withdrawals incur a $1 fee
14
```

Since we are looking the name `withdraw` on a class in the implementation of `withdraw` as opposed to on an instance, we will not get a bound method back. We have to supply the `self` ourselves.

```python
class CheckingAccount(Account):
    withdraw_fee = 1
    interest = 0.01

    def withdraw(self, amount):
        return Account.withdraw(self, amount + self.withdraw_fee)
```

## Looking up Attribute Names on Classes

Base class attributes **aren't copied** into subclasses.

To look up a name in a class:

1. If it names an attribute in the class, return the attribute value.
2. Otherwise, look up the name in the base class, if there is one.

### A Complicated Example

```python
class A:
    z = -1
    def f (self, x):
        return B(x - 1)

class B(A):
    n = 4
    def __init__(self, y):
        if y:
            self.z = self.f(y)
        else:
            self.z = C(y + 1)

class C(B):
    sef f(self, x):
    return x
```

@import "img/inheritance-01.png" {width=360}

```python
>>> a = A()
>>> b = B(1)
>>> b.n = 5
>>> C(2).n
4
>>> a.z == C.z
True
>>> a.z == b.z
False
```

## Multiple Inheritance

```python
class SavingAccount(Account):
    deposit_fee = 2

    def deposit(self, amount):
        return Account.deposit(self, amount - self.deposit_fee)
```

CleverBank marketing executive wants:

- Low interest rate of 1%
- A $1 fee for withdrawals
- A $2 fee for deposits
- A free dollar when you open your account

```python
class AsSeenOnTVAccount(CheckingAccount, SavingAccount):
    def __init__(self, account_holder):
        self.holder = account_holder
        self.balance = 1
```
