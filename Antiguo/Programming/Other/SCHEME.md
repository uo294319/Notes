
---
# SCHEME

[HOME](../../README.md)

---

# THEORY
## Functional Programming
- Datatypes: s-expressions or functions (procedures)
- Function-based:
	- **Function composition** -> No assignments.
	- **Loops through recursion** -> Not iteration.
	- **Higher Order Functions (HOF)** -> Functions receive other functions.
- Scheme
	- Based in LISP (List Processing)
	- Pure functional
## Data types

- **S-expressions** (symbolic data)
	- **Atoms**
		- Independent values
		- Examples: `a`, `B`, `#t`, `#f`
	- **Pairs**
		- Grouping of two s-expressions.
			- Can be atoms or another pairs.
		- Structure: `(s1 . s2)`
	
- **Lists**
	- Grouping of atoms.
	- The empty list `()` is an atom (In scheme, `'()` or `null`).
	- Structure: `(s1 . L)` where L is another list.
	- Note that `s1` can also be another list.

## Environments

- The **General Environment** are the functions/constants defined by Scheme
- The **User Environment** are the functions defined by the user
- The **Function Environment** are the arguments and local definitions.

---
# Basic Functions summary
## Managing s-expressions

- `(atom? X)`
	- Returns `#t` if `X` is an atom.

- `(null? X)`
	- Returns true if `X` is the empty list.

- `(pair? X)`
	- Returns `#t` if `X` is a pair.

- `(list? X)`
	- Returns `#t` if `X` is a list.

- `(equal? X Y)`
	- Returns `#t` if  the s-expression `X` is equal to `Y`.
	- `(eq? X Y)` does the same but only for atoms.

- `(quote X)`
	- Returns `X` as an s-expression (data).
	- `(quote a)` -> `a`
	- `'a` -> `a`

> [!NOTE]
> `X` is a procedures and `'X` is a s-expression.
> The parenthesis are used to evaluate procedures. `(X)`

- `(car X)`
	- Returns first element of a pair.
	- `(car '(a . b))` -> `a`
	- `(car '(a b c))` -> `a`
	- `(car '((a b) c))` -> `(a b)`

- `(cdr X)`
	- Returns second element of a pair.
	- `(cdr '(a . b))` -> `b`
	- `(cdr '(a b c))` -> `(b c)`
	- `(cdr '((a b) c))` -> `(c)` (NOT `c`)

> [!NOTE]
> `car` and `cdr` can be combined.
> `(car (car (cdr X)))` = `(caadr X)`

- `(cons X Y)`
	- Returns the pair `(X . Y)`
	- (cons 'a 'b) -> (a . b)
	- (cons '(a b) '((c d) e)) -> ((a b) (c d) e)

- `(list X Y ...)`
	- Returns a list containing given args.
	- `(list 'a)` -> `(a)`
	- `(list 'a 'b)` -> `(a b)`

> [!NOTE]
> `cons` and `list` are not the same:
> `(cons 'a '(b c) )` -> `(a b c)`
> `(list 'a '(b c) )` -> `(a (b c) )`

## List functions

- `(list X Y ...)`
	- Returns a list containing the arguments provided.
	- `(list 1 2 3)` -> `'(1 2 3)`

- `(sort X criteria)`
	- Returns the list sorted by a criteria.
	- `(sort '(1 4 3 2) <)` -> `'(1 2 3 4)`

- `(length X)`
	- Returns the length of a list.
	- `(length '(1 2 3 4)` -> 4

- `(member X Y)`
	- Checks if `X` is inside list `Y`.
	- `(member 1 '(2 3 4))` -> `#f`
	- Note that instead of true, it returns the sub-list starting at `X`.
	- `(member 1 '(2 1 4))` -> `(1 4)`

- `(reverse X)`
	- Reverses list `X`. (Not recursively)
	- `(reverse '(1 2 3) )` -> `(3 2 1)`
	- `(reverse '(1 2 (3 4) ) )` -> `( (3 4) 2 1)`

## Let Keyword
- `(let [(a X) (b Y)] (func a b))`
	- Let us define some variables in a local scope. `a=X` and `b=Y`.
	- The binding is done in parallel (all at the same time)
	- To use sequential binding use `let*`.
	- `(let [(a 3) (b 2)] (* a b))` -> 3 x 2 = 6
	- `(let [(a 3) (b (+ a 1))] (* a b))` -> ERROR. `a` not defined

- `(let* [(a X) (b Y)] (func a b))`
	- Same as `let` but with sequential binding.
	- `(let* [(a 3) (b (+ a 1))] (* a b))` -> 3 x (3 + 1) = 12

- `(letrec [(a X) (b Y)] (func a b))`
	- Same as `let` but allows recursive calls (inside the variable declaration)

```scheme
(letrec
	[
		(even? (lambda (n) (if (= n 0) #t (odd?  (- n 1)))))
	    (odd?  (lambda (n) (if (= n 0) #f (even? (- n 1)))))
    ]
	(even? 6)
)
```

## Constants & Functions Definition

- `(define (name X Y ...) (func))`
	- Creates a reusable function (or constant).

```scheme
; This is a recursive function definition
; 1. Base: Whats the case to stop? Output?
; 2. Recurrence: l is not the empty list
;                l = cons(car(l), cdr(l))
;
;      - Hipothesis: assume we know func(cdr(l)) = H
;      - Thesis    : my-func(l) ::= ?


(define (compare a b)
	(if (null? a)
		'()
		(cons
			(cond (
				[< (car a) (car b)) -1]
				[(= (car a) (car b)) 0]
		        [(> (car a) (car b)) 1]
		    )
			(compare (cdr a) (cdr b))
		)
    )
)

; This is a constant
(define my-list '(1 2 3))
```

## Control flow
- `if cond val_true val_false`
	- If the condition is true it returns val_true, otherwise it returns val_false.

```scheme
(define (abs x)
  (if (< x 0) (- x) x)
)
```

- cond

---
# Higher Order Functions (HOF)
## Basic HOF Functions

- `(map func X Y ...)`
	- Applies given function to each element of one or more lists IN ORDER.
	- `(map max '(1 2) '(3 4) '(5 6))` -> `(list (max 1 3 5) (max 2 4 6))`

- `(apply func X Y ... L)`
	- Applies given function to all elements passed.
	- All elements but last one should be numbers.
	- Last one should always be a list (that will be unpacked).
	- `(apply * '(5   2   3) )` -> 5 x 2 x 3 = 30
	- `(apply *   5 '(2   3) )` -> 5 x 2 x 3 = 30
	- `(apply *   5   2 '(3) )` -> 5 x 2 x 3 = 30
	- `(apply * '(5)  2 '(3) )` -> ERROR. `(5)` is not a number.
	- `(apply *   5   2   3  )` -> ERROR. `3` is not a list.

- `(lambda X func)`
	- Creates a function that does something with a set of variables `X`.
	- `((lambda (x y) (+ x y)) 2 3)` -> `(x y)` = `(2 3)` -> 5
	- `((lambda (x . y) (apply + x y)) 2 3 4)` -> `(x . y)` = `(2 . (3 4))` -> 9
	- `((lambda X (cons 1 X)) 2 3)` -> `(1 2 3)`

> [!NOTE]
> In lambdas the arguments are tricky. For example:
> - In `(lambda (x y) ... )` x and y are mandatory arguments.
> - In `(lambda (x . y) ... )` x is mandatory and y is the list with the rest of arguments.
> - In `(lambda x ... )` x is a list with all the arguments passed.

- `(filter func X)`
	- Filters a list by a provided boolean function
	- `(filter (lambda x (atom? (car x))) '(1 (2) 3))` -> `(1 3)`
	- Note that the arguments are encapsulated inside another list
	- `(filter (lambda x (list? x)) '(1 (2) 3))`
		`(list? '((1 (2) 3)) ))` = `#t` -> `(1 (2) 3)`

## Composition & Curryfication

- `(compose func1 func2 ...)`
	- Allows to apply functions one after another.
	- `((compose add1 *) 2 3)` -> `(add1 (* 2 3))` -> (2 x 3) + 1 = 7

- `(foldl func base X )`
	- Applies recursively a function to all the elem. of a list from left to right.
	- `(foldl f base '(e1 e2 e3))` = `(f e3 (f e2 (f e1 base)))`

- `(foldr func base X )`
	- Applies recursively a function to all the elem. of a list from right to left.
	- `(foldl f base '(e1 e2 e3))` = `(f e1 (f e2 (f e3 base)))`

- `((curry func X) Y)`
	- Allows creating a function without an argument.
	- Same as doing `(func X Y)`+
	- `((curry / 2) 3)` -> `(/ 2 3)` -> `2/3`

- `((curryr func X) Y)`
	- Similar to curry but the argument is inserted the first.
	- Same as doing `(func Y X)`
	- `((curryr / 2) 3)` -> `(/ 3 2)` -> `3/2`






