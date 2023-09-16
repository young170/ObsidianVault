## Proofs
### Proof by Contradiction

All of the members of the set of natural numbers are finite.
Is the cardinality of the set of natural numbers infinite?
* If the cardinality was to be finite there exists the largest natural number.
* However, it is possible to add 1 to the largest natural number which contradicts the fact that it is the largest number.
* $\therefore$ The cardinality of the set of natural numbers is infinite.

### Alphabets

Sets of symbols
* finite
* non-empty

### Strings

$\sum^*$: the set of all ($*$) strings over alphabet $\sum$.
* Is $\sum^*$ finite? or infinite?
	* Although $\epsilon$ is a a member of the string, the alphabet that composes the string has a non-empty property.
	* $\therefore$ $\sum^*$ is infinite.

### Languages

Set of strings all of which are chosen from some $\sum^*$, given an alphabet $\sum$.

## Finite Automata

The final state determines if the automaton $A$ accepts the language $L$.
To handle inputs that cause the automaton to go over the bounds, extra states are needed, i.e. dead states.
* This may raise a question of efficiency.
	* For the theory of automata, computation efficiency is not considered.
	* Only consider the if it can be computed, computation itself.
* There are two types of efficiency, interpretation & implementation.

Essentially, finite automata is interchangeable with language. Automata are simply representations/expressions.

### Deterministic Finite Automata

The automaton moves from its current state to *one and only one* state.

### Non-deterministic Finite Automata

The automaton moves from its current state to *several states at once*.

### Language of an Automaton

The set of strings from the input alphabet $\sum$ is the language $L$ of the automaton $A$. This denoted $L(A)$.
* In this case, $L$ is used both as a set and a function. Read the context.

### Regular Language

A language is a regular language if at least one automata accepts the language.
* As it says, "at least one" you can know the mapping is one-to-one.
	* Each automata is designed to accept a language.