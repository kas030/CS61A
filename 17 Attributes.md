# Attributes

## Attribute Lookup

Both instances and classes have attributes that can be looked up by dot expressions: `<expression>.<name>`.

To evaluate a dot expression:

1. Evaluate the `<expression>` to the left of the dot, which yields the object of the dot expression.
2. `<name>` is matched against the instance attributes of that object; if an attribute with that name exists, its value is returned.
3. If not, `<name>` is looked up in the class, which yields a class attribute value.
4. That value is returned unless it is a function, in which case a bound method is returned instead.

Using `getattr`, we can look up an attribute using a string.

```python
>>> getattr(tom_account, 'balance')
10
>>> hasattr(tom_account, 'deposit')
True
```

## Class Attributes

```python
class <name>:
    <suite>
```

A class statement creates a new class and binds that class to `<name>` in the first frame of the current environment.

Assignment & def statements in `<suite>` create attributes of the class (not names in frames).

Class attributes are shares across all instance of class because they are attributes of the class, not the instance.

```python
class Account:
    interest = 0.02  ## A class attribute
    ...

tom_account = Account("Tom")
tom_account.interest  # 0.02
```

Here the `interest` attribute is not part of the instance: it's part of the class. It's just the lookup procedure that gives us access to it.

## Bound Methods

Terminology:

@import "img/attributes-01.png" {width=300}

Functions and bound methods are both objects. Dot expressions evaluate to bound methods for class attributes that are functions.

Python distinguishes between functions and bound methods.

```python
>>> type(Account.deposit)
<class 'function'>
>>> type(tom_account.deposit)
<class 'method'>

>>> Account.deposit(tom_account, 100)
100
>>> tom_account.deposit(100)
200
```

## Attribute Assignment

Assignment statements with a dot expression on their left-hand side affect attributes for the object of that dot expression.

- If the object is an instance, then assignment sets an instance attribute.
- If the object is a class, then assignment sets a class attribute.

```python
class Account:
    interest = 0.02
    ...

tom_account = Account('Tom')
```

Class attribute assignment: `Account.interest = 0.04`

Instance attribute assignment: `tom_account.interest = 0.08`

The name `interest` is not looked up in the object. Instead of going find it in the class, it just directly assigned to the attribute of the object.

Attribute assignment statement adds or modifies the attribute `interest` of `tom_account`.

Instance attributes and class attributes are totally independent in case of attribute assignment. They just relate to each other in attribute lookup.
