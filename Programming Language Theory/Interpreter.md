
Using **type-case** to access the modifier of each type.

## Implementation of the AE interpreter

```
; interp: AE -> number  
(define (interp an-ae)  
	(type-case AE an-ae  
		;; n is recognized as actual number for computers  
		[num (n) n]  
		;; add is recognized as a real behavior to sum two AEs.  
		[add (l r) (+ (interp l) (interp r))]  
		;; sub is recognized as a real behavior to subtract two AEs.  
		[sub (l r) (- (interp l) (interp r))]
	)
)
```

## Implementation of the WAE interpreter

```
; [contract] subst: WAE symbol number -> WAE
(define (subst wae id val)
	(type-case WAE wae
		[num (n)      wae]
		[add (l r)    (add (subst l idtf val) (subst r idtf val))]
		[sub (l r)    (sub (subst l idtf val) (subst r idtf val))]
		[with (i v e) (with i (subst v idtf val) (if symbol=? i idtf) e (subst e idtf val))]
		[id (s)       (if (symbol=? s idtf) (num val) wae)]))
```
Here's a test,
```
; {with {x 10} {+ 1 x}}
(test (subst (add (num 1) (id 'x)) 'x 10) (add (num 1) (num 10)))
```
1. Initial state:
	1. `wae`: `(add (num 1) (id 'x))`
	2. `id`: `'x`
	3. `val`: `10`
2. The `wae` has an `add` type:
	1. `l`: `(num 1)`
	2. `r`: `(id 'x)`
	3. `idtf`: `'x`, always constant in this example
	4. `val`: `10`, always constant in this example
3. For the right-hand side of the `add` type, `wae` is given as the `id` `x`
	1. `s`: `x`, bound identifier
	2. `idtf`: `x`, binding identifier
	3. `val`: `10`
4. If a free identifier exists,
	1. `s` is a free identifier which is different from the binding identifier
	2. `idtf`: `x` so the false branch is executed
	3. `wae` itself is returned

```
; interp: WAE -> number
(define (interp wae)
	(type-case WAE wae
		[num (n) n]
		[add (l r) (+ (interp l) (interp r))]
		[sub (l r) (- (interp l) (interp r))]
		[with (i v e) (interp (subst e i (interp v)))]
		[id (s) (error `interp "free identifier")]))
```
If `id` is left as it is, it means there exists a free identifier.
