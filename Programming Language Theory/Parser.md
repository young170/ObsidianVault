Transforms the **concrete syntax** (the code we write) into **abstract syntax**.
Examples:
* BNF (Backus-Naur Form)
* AST (Abstract Syntax Tree)

## BNF
### BNF Grammar
```
<expr> → Non-terminal: Meta-variable

::= Can be written as

| One more choice

<…> literal syntax

Terminal
```
* `Non-terminal`: A symbol that can be replaced by one or more **terminals** or other **non-terminals**.
* `Terminal`:  The smallest units that cannot be further broken down. Examples are literal values, keywords, or symbols in the language.

Example:
```
<digit> ::= 0 | <non-zero digit>
<non-zero digit> ::= 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
```

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
