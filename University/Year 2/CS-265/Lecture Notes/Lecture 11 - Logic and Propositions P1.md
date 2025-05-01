#### Propositions:
- A proposition is a sentence, written in a language which has a truth value. True or false, in a world. Boolean refers to an expression being either true or false and nothing between. 
- A proposition is either an atomic proposition or built from simpler (atomic or non atomic) propositions and logical connectives.

#### Propositional Calculus Syntax
- An atomic proposition - atom - is a symbol, written as sequences of letters, digits and the underscore and start with a lowercase
	- is_fun, live_outside, sunny
- A proposition or logical formula is either
	- An atomic proposition or
	- a compound proposition
		- think negation, conjunction, disjunction, implication, equivalence or xor
		- ^ logical connectives

#### Why Propositions
- Logical formulae are modular statements of what is true
- It is easy to check correctness and debug formulae using tables of what could be true
	- AKA truth tables
- We can exploit the boolean nature for efficient reasoning
- We need a language for asking queries (of what follows in all models) that may be more complex than asking the value of a variable
- It is easy to incrementally add formulae
- It can be extended to infinitely many propositions
 
#### Semantics of the Propositional Calculus
- An interpretation - or possible world - is an assignment of true or false to each variable
- An interpretation is defined by function (pi) that maps atoms to {true, false}
- if π(a) = true, atom a is "true" in this interpretation
- if π(a) = false, atom a is "false" in this interpretation
- Truth of a compound proposition in an interpretation is defined in terms of the truth of its components.

#### Models and Logical Consequence
- a model of a set of clauses is an interpretation in which all the clauses are true
- if KB is a set of propositions, proposition g is a logical consequence of KB, written KB |= g, if g is true in every model of KB.
- That is, KB |= g if there is no interpretation in which KB is true and g is false.

#### Semantics: Varying views:
- Humans
	- Step 1 - Begin with a task domain
	- Step 2 - Choose atoms in the computer to denote propositions. These aroms have meaning to the KB designer.
	- Step 3 - Tell the system knowledge about the domain
	- Step 4 - Ask the system questions
		- The system can tell you whether the question is a logical consequence
		- You can interpret the answer with the meaning associated with the atoms
- Computers
	- The computer doesnt have access to the intended information
	- All it knows is the knowledge base
	- The computer can determine if a formula is a logical consequence of KB.
	- If KB |= g, then g must be true in the intended interpretation
	- If KB |/= g, then there is a model of KB in which g is false. This could be the intended interpretation.
