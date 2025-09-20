# Scheme Lists

## Lists

Basic symbols in Scheme related to lists:

- `cons`: Two-argument procedure that creates a linked list
- `car`: Procedure that returns the first element of a list
- `cdr`: Procedure that returns the rest of a list
- `nil`: The empty list

Scheme lists are written in **parentheses with elements separated by spaces**.

```scheme
> (cons 1 (cons 2 nil))
(1 2)
> (define x (cons 1 (cons 2 nil)))
> x
(1 2)
> (car x)
1
> (cdr x)
(2)
> (cons (cons 3 (cons 4 nil)) (cons 1 (cons 2 nil)))
((3 4) 1 2)
```

Some built in procedures related to lists:

- `(list? s)`: test if s is a list
- `(null? s)`: test if s is an empty list
- `(list e1 e2 ...)`: build a list with the provided elements

## Symbolic Programming

Symbols normally refer to values, while quotation is used to refer to symbols directly in Lisp.

```scheme
> (define a 1)
> (define b 2)
> (list 'a 'b)
(a b)
```

The quote is actually shorthand for a special form called quote: `'a` is short for `(quote a)` and `'b` is short for `(quote b)`.

Quotation can also be applied to combinations to form lists.

```scheme
> '(a b c)
(a b c)
> (car '(a b c))
a
```

We can refer to a symbol even before it have been defined.
