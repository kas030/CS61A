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

## Built-in List Processing Procedures

- `(append s t)`: list the elements of `s` and `t`; `append` can be called on more than 2 lists
- `(map f s)`: call a procedure `f` on each element of a list `s` and list the results
- `(filter f s)`: call a procedure `f` on each element of a list `s` and list the elements for which a true value is the result
- `(apply f s)`: call a procedure `f` with the elements of a list as its arguments

```scheme
> (map (lambda (s) (cons 5 s)) (filter list? `(5 (6 7))))
((5 6 7))
> (apply + `(1 2 3 4))
10
```

## Example: Even Subsets

Definition: a non-empty subset of a list s is a list containing some of the elements of s.

```scheme
;;; none-empty subsets of integer list s that have an even sum
;;; scm> (even-subsets `(3 4 5 7))
;;; ((5 7) (4 5 7) (4) (3 7) (3 5) (3 4 7) (3 4 5))
(define (even-subsets s) 
  (if (null? s) nil
    (append (even-subsets (cdr s))
            (subset-helper even? s))))

;;; none-empty subsets of integer list s that have an odd sum
(define (odd-subsets s) 
  (if (null? s) nil
    (append (odd-subsets (cdr s))
            (subset-helper odd? s))))

(define (subset-helper f s)
  (append (map (lambda (t) (cons (car s) t))
               (if (f (car s))
                   (even-subsets (cdr s))
                   (odd-subsets (cdr s))))
          (if (f car s)
              (list (list (cdr s)))
              nil)))
```

## Discussion Question: Even Subsets Using Filter

```scheme
;;; non-empty subsets of s
(define (nonempty-subsets s)
  (if (null? s) 
      nil
      (let ((rest (nonempty-subsets (cdr s))))
           (append rest
                   (map (lambda (t) (cons (car s) t))
                        rest)
                   (list (list (car s)))))))

;;; non-empty subsets of integer list that have an even sum
(define (even-subsets s)
  (filter (lambda (s) (even? (apply + s)))
          (nonempty-subsets s)))
```