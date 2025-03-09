#### Unification:
2 terms unify if: 
1. They are identical terms or 
2. They contain variables that can be consistently instantiated with terms in such a way that the resuting terms are equal.

	E.G:  f(a,Y) and f(X,g(z)) unify with X = a and Y = g(Z)

#### Unification - a recursive definition:
- Two terms T1 and T2 unify if:
	- T1 and T2 are atomic (then they unify on same atom)
	- T1 is a variable and T2 is any type of term. Then T1 is instantiated to T2 and vice versa.
	- T1 T2 complex terms, then:
		- Same functor and arity AND
		- all their corresponding arguments unify AND
		- the variable instantiations are complete

If we try to launch the goal:
	X = f(X)
prolog will make an infinite term (f(f(f(f(f....(x)))))
- Standard unification algorithm carries out an "occurs" check
- If it is asked to unify a variable with another term, it checks if the variable occurs in the term to avoid infinite terms.
- If you want to enforce the occurs check, use: "unify_with_occurs_check".

Prolog uses proof trees to find results. 
It uses DFS specifically. 
Pros: Much less memory consumption than BFS
Cons: Some solutions may not be found