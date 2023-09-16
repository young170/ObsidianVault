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
