Arithmetic Expressions.

## BNF of AE
```
<AE> ::= <num>
		| {+ <AE> <AE>}
		| {- <AE> <AE>}
```
The reason the BNF **substitutes** AE instead of num is to allow expansions:

## Syntax of AE
```
(define-type AE
	[num (n number?)]
	[add (lhs num?)
		 (rhs num?)]
	[sub (lhs num?)
		 (rhs num?)])
```
What is wrong with this syntax?

```
(define-type AE
	[num (n number?)]
	[add (lhs AE?)
		 (rhs AE?)]
	[sub (lhs AE?)
		 (rhs AE?)])
```
Just like in the BNF, need expandability.
