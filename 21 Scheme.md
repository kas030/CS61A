# Scheme

Scheme is a minimalist dialect of the Lisp programming language.

## Scheme Fundamentals

Scheme programs consist of expressions, which can be:

- Primitive expressions: 2, 3.3, true, +, quotient, etc.
- Combinations: (quotient 10 2), (not true), etc.

Numbers are self-evaluating; symbols are bound to values.

Call expressions include an operator and 0 or more operands in the parentheses.

Combinations can span multiple lines, and indentation doesn't matter.

```scheme
> (quotient 10 2)
5
> (+ (* 3
        (+ (* 2 4)
           (+ 3 5)))
     (+ (- 10 7)
        6))
26
> (+ 1 2 3 4)
10
> (+)
0
> +
#[+]
> (number? 3)
#t
> (zero? 0)
#t
```

## Special Forms

A combination that is not a call expression is a special form:

- **If** expressions: `(if <predicate> <consequent> <alternative>)`
- **And** and **or**: `(and <e1> <e2> ...)`, `(or <e1> <e2> ...)`
- Binding symbols: `(define <symbol> <expression>)`
- New procedures: `(define (<symbol> <formal-parameters>) <body>)`

```scheme
> (define (square x) (* x x))
> (square 5)
25
> (define (sqrt x)
    (define (update guess)
      (if (= (square guess) x)
          guess
          (update (/ (+ guess (/ x guess)) 2))))
    (update 1))
> (sqrt 9)
3
```

The `cond` special form that behaves like `if-elif-else` statements in Python:

```scheme
(cond ((> x 0) 'positive)
      ((< x 0) 'negative)
      (else 'zero))
```

The `begin` special form allows multiple expressions to be evaluated in sequence:

```scheme
(begin
  (define x 10)
  (define y 20)
  (+ x y))
```

The `let` special form binds symbols to values temporatily; just for one expression:

```scheme
(let ((x 10)
      (y 20))
  (+ x y))
```

## Lambda Expressions

Lambda expressions evaluate to anonymous procedures.

```scheme
(lambda (<formal-parameters>) <body>)
```

Two equivalent expressions:

```scheme
(define (plus4 x) (+ x 4))
(define plus4 (lambda (x) (+ x 4)))
```

## Example: Sierpinski's Triangle

```scheme
(define (line) (fd 50))
(define (twice fn) (fn) (fn))
(define (repeat k fn)
  (fn)
  (if (> k 1) (repeat (- k 1) fn)))
(define (tri fn)
  (repeat 3 (lambda () (fn) (lt 120))))
(define (sierpinski d k)
  (tri (lambda () (if (= d 1) (fd k) (leg d k)))))
(define (leg d k)
  (sierpinski (- d 1) (/ k 2))
  (penup) (fd k) (pendown))
(sierpinski 5 200)
```

@import "img/scheme-01.png" {width=200}
