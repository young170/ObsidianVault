
Using **type-case** to access the modifier of each type.

## Implementation of the interpreter
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
