Transforms the **concrete syntax** (the code we write) into **abstract syntax**.

Examples:
* [[BNF]] (Backus-Naur Form)
* AST (Abstract Syntax Tree)

## Implementation of the AE parser

```
;; parse : sexp -> AE
;; to convert sub-expressions into AE types in abstract syntax  
(define (parse sexp)
	(cond  
		[(number? sexp) (num sexp)]  
		[(eq? (first sexp) '+) (add (parse (second sexp))  
									(parse (third sexp)))]  
		[(eq? (first sexp) '-) (sub (parse (second sexp))  
									(parse (third sexp)))]  
		))

(test (parse '3) (num 3))  
(parse '{+ 3 4}) ;; our code must start with a single quote to deal with them as symbols!  
(test (parse '{+ 3 4}) (add (num 3) (num 4)))
```
How about this?  (parse '{+ 3 4 5})
* Need to limit the length of the sub-expressions

```
(define (parse sexp)
	(cond  
		[(number? sexp) (num sexp)]  
		[(and (= 3 (length sexp))
			  (eq? (first sexp) `+))
		(add (parse (second sexp))
			 (parse (third sexp)))]
		[(and (= 3 (length sexp))
			  (eq? (first sexp) '-))
		(sub (parse (second sexp))
			 (parse (third sexp)))] 
		[else (error `parse "bad syntax: ~a" sexp)] 
	)
)
```
By limiting the length of the concrete syntax, it is possible to detect [[Error]]s.

## Implementation of the WAE parser

```
(define (parse sexp)
	(cond  
		[(number? sexp) (num sexp)]  
		[(and (= 3 (length sexp))
			  (eq? (first sexp) `+))
		(add (parse (second sexp))
			 (parse (third sexp)))]
		[(and (= 3 (length sexp))
			  (eq? (first sexp) '-))
		(sub (parse (second sexp))
			 (parse (third sexp)))] 
		[...(with...)]
		[...(id)]
		[else (error `parse "bad syntax: ~a" sexp)] 
	)
)
```
Try implementing by yourself!

```
(define (parse sexp)
	(match sexp
		[(? number?)                     (num sexp)]
		[(list `+ l r)                   (add (parse l) (parse r))]
		[(list `- l r)                   (sub (parse l) (parse r))]
		[(list `with (list id val) exp) (with id (parse val) (parse exp))]
		[(? symobl?)                     (id sexp)]
		[else (error `parse "bad syntax: ~a" sexp)])
)
```
