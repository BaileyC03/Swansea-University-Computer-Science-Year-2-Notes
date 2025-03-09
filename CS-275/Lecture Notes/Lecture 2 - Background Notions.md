#### PROPOSITIONAL LOGIC:
- Very simple logic
- Useful to understand core aspect of logical inference and truth values
- Symbols:
	- letters of the alphabet, then can do like a0, a1, a2
	- T and F denote true and false (or 1 and 0)
- Connectives
	- connect different propositional symbols:
		- ^ - and
		- v - or
		- ¬ - not
		- -> if-then
- Auxhillary symbols:
	- () - specifies order of operations

#### BUILDING FORMULAS:
1. start with propositional symbols
2. connect them
3. potentially connect these formulas with other formulas

#### TRUTH VALUES - How to reason about truth
- When considering if something is true (P V Q) we can consider all possible values for both P and Q and make a table for it. 
- for implication (p->q), this does not describe a cause-effect relationship. It just means, whenever p is true, q has to be true.
	- eg if coin flips head, alice pays bob doesnt mean if its tails, bob pays alice. it is unrelated
- p -> q is NOT the same as q -> p
	- Look into this

#### Logical consequences
- Implication are important to study if a reasoning is valid, namely if the conclusions are logical consequences of the premises.
	- p -> q doesnt mean that q is true
	- if p is true, q is true
	- but if p is false, q may also still be true.
[Look into this]

#### LOGICAL EQUIVALENCE
- Two formulae are logically equivalent if they always have the same truth value independently of the truth tables of the propositional symbols
	- AKA p -> q and ¬p v q are logically equiv
		- this is because for every value of p and q, they return the same value
- Can be represented via <-> 
	- p <-> q implies p and q are logically equivalent

#### DE MORGANS LAWS
- Rules that allow us to write conjunctions and disjunctions in terms of eachother via negation
	- E.G: "The coin landed on head and the die showed 6"
	- negated - "the die did not land on head or the die did not show a 6"
- This is formalised as:
	- ¬(P ^ Q) <-> ¬P v ¬Q
	- ¬(PvQ) <-> ¬P ^ ¬Q
- AKA you swap the operator and negate the symbols inside

#### FIRST-ORDER LOGIC
- We describe quantifiers with symbols
	- (upside down A) - for ALL 
		- For every element of a set
		- (An)(n>= 0)
			- for all n, n >= 0
	- (Backwards E) - EXISTS
		- For 1+ element of a set
- In first order logic, as there is more than just T/F, we need to know the set in which n resides (known as a domain) and we may also want to know the relations between the elements within the domain to make a model:
- IMPORTANT: 
	- WE NEED TO BE CAREFUL TO DIFFERENTIATE THE SYMBOLS WE USE AND THE ELEMENTS WE REFER TO
	- Always allowed: 
		- Infinite variables x,y,z,... and x0, x1, x2
		- Logical connectives
		- Quantifiers
		- Brackets
	- Language dependent
		- Symbols for constants (0,1,2,3)
		- Symbols for functions
		- Symbols for relations (predicates)
- Exists M... and For All A ... are not valid on their own.

#### DE MORGANS LAWS FOR FIRST ORDER LOGIC
- To negate, flip the quantifier and negate the formula
	- formula must be valid and well-formed

#### SETS NOTATION
{x (element of) X | func(x)}
| -> Such that
- func(x) must be true for any values in X for it to be in the resulting set of this setbuilder notation. Consider the right side of the "|" (or ":", both work) to be a filter for all the values of X

[[CONTINUE TO "some mathematical notation" SLIDE]]
