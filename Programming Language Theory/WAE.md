With Arithmetic Expressions.

## BNF of WAE

```
<WAE> ::= <num>
		| {+ <WAE> <WAE>}
		| {- <WAE> <WAE>}
		| {with {<id> <WAE>} <WAE>}
		| <id>
```

`<id>` is a non-terminal.

Example:
```
{with {x {+ 1 2}} {+ x x}}
---
6
```

There are three terms to remember,
* Binding identifier
	* The defining part of the identifier
	* `{x {+ 1 2}}`
* Bound identifier
	* The usage of the identifier
	* `{+ x x}`
* Free identifier
	* An undefined identifier
	* `{+ x y}`
	* Causes error: free identifier

## Syntax of WAE

```
(define-type WAE
	[num (n number?)]
	[add (lhs WAE?)
		 (rhs WAE?)]
	[sub (lhs WAE?)
		 (rhs WAE?)])
```
This was the original AE definition.

```
(define-type WAE
	[num (n number?)]
	[add (lhs WAE?)
		 (rhs WAE?)]
	[sub (lhs WAE?)
		 (rhs WAE?)])
	[with (name symbol?) (name-exp WAE?) (body WAE?)]
	[id (name symbol?)])
```