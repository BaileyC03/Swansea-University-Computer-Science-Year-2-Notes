-- Do up to slide 17

#### User's view of Semantics
1. Choose a tank domain
	- Intended interpretation
2. Associate constants with individuals you want to name
3. For each relation you want to represent, associate a predicate symbol in the language.
4. Tell the system clauses that are true in the intended interpretation
	- Axiomatizing the domain
5. Ask questions about the intended interpretation
6. If KB |= g, then g must be true in the intended interpretation

#### Computer's view of Semantics: 
- The computer doesnt have access to the intended information
- All it knows is the knowledge base
- The computer can determine if a formula is a logical consequence of KB.
- If KB |= g, then g must be true in the intended interpretation
- If KB |/= g, then there is a model of KB in which g is false. This could be the intended interpretation.

#### Variables: 
- A variable assignment is a function from variables to into the domain
- Given an interpretation and a variable assignment, each term denotes an individual and each clause is either true or false.
- Variables are universally quantified in the scope of a clause.
	- ∀X [noisy (X ) ← left of (X , scissors)]
		- For all X, X is noisy IF X is left of scissors.
- A clause containing variables is true in an interpretation if it is true for all variable assignments. That is, it considers a variable assignment for all entities in the domain, testing whether the instantiation is true of the clauses. This is because of the universal quantifier.

#### Queries and Answers
- A query is a way to ask if a body is a logical consequence of the knowledge base 
	- ?b1 ^ ... ^ bm.

- An answer is either:
	- An instance of the query that is a logical consequence of the knowledge base KB or 
	- "no" if no instance is a logical consequence of KB.

#### Example Queries:
![[Pasted image 20250311121646.png]]
- ?part_of(r123,B).
	- part_of(r123, cs_building)
- ?part_of(r023, cs_building).
	- no
- ?in(kim, r023).
	- no
- ?in (kim, B).
	- in(kim, r123)
	- in(kim, cs_building)

#### Electrical Environment
![[Pasted image 20250311121857.png]]

#### Axiomitazing the Electrical Environment:
- light(L) is true if L is a light  
	- light(l1). light(l2).  
- down(S) is true if switch S is down  
	- down(s1). up(s2). up(s3).  
- ok(D) is true if D is not broken,  
- where D can be lights (l) or circuit breakers (cb)  
	- ok(l1). ok(l2). ok(cb1). ok(cb2).

- ?light(l1). -> yes
- ?light(l6). -> no
- ?up(X). -> up(s2), up(s3)
etc etc... 
- Note:
	- If a switch is disconnected, then some wire will be disconnected (or)
![[Pasted image 20250311122315.png]]
^ this is a RECURSIVE definition of live.

#### Recursion and Mathematical Induction:
- above(X,Y) <- on(X,Y).
- above(X,Y) <- on(X,Y) ^ above(Z,Y).
- The above can be seen as:
	- recursive definition of above, proving above in terms of a base case (on) or a simler instance of itself
	- Way to prove by mathematical induction; the base case is when there are no blocks between X and Y, and if you can prove *above* when there are n blocks between them, you can prove it when there are n+1 blocks
