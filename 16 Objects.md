# Objects

## Class Statements: the Account Class

```python
class Account:
    def __init__(self, account_holder):
        self.balance = 0
        self.holder = account_holder
    
    def deposit(self, amount):
        self.balance =  self.balance + amount
        return self.balance
    
    def withdraw(self, amount):
        if amount > self.balance:
            return "Insufficient funds"
        self.balance -= amount
        return self.balance
```

`__init__` is the constructor of a class.

## Creating Instances

When a class is called:

1. A new instance of that class is created.
2. The `__init__` method of the class is called with the new object as its first argument (named `self`), along with any additional arguments provided in the call expression.

Any attribute can be assigned any value. A new attribute can be added at **any time**.

Binding an object to a new name using assignment does not create a new object.

## Methods

### Invoking Methods

All invoked methods have access to the object via the self parameter, and so they can all access and manipulate the object's attribute. Dot notation automatically supplies the first argument to a method.
