#### Individuals and Relations:
- It is useful to view the world as consisting as individuals
	- Entities, Objects, Things 
	- Individuals have properties and relations with other individuals.
- Features are made from:
	- Properties of individuals 
	- relations among individuals
		- E.G: Argentina is a country and won the world cup in 2022
- Reasoning in terms of individuals and relationships can be simpler than reasoning in terms of features if we can express general knowledge that covers all individuals.
- Sometimes you may know some individual exists, but not know which one.
- Sometimes there are infinite individuals we want to refer to (like number sets N or R)

#### Role of Semantics in Automated Reasoning:
- Users can have meanings for symbols in their head.
	- They tell the computer what is true.
- The computer doesnt need to know these meanings to derive logical consequences
- Users can interpret any answers according to their meaning

#### Predicate Calculus
- Predicate calc (or predicate logic, same thing) extends propositional calculus in 2 ways:
	- Atoms have structure and can include constants and logical variables
	- Quantification of logical variables

- Syntactic convention of Datalog / Prolog:
	- Variables start with an uppercase letter
	- Constants, predicates and functions start with a lowercase
	- Predicate symbol starts with lowercase letter
	- a term is either a variable or constant
	- atomic symbol is of the form p(x,y,z)
	- Logical connectives: 
		- ¬ (not), 
		- ∧ (and),
		- ∨ (or), 
		- ← (if),
		- →  (implies),
		- ↔ (equivalence)
	- Quantification
		- ∀ (For all)
		- ∃ (There exists)

#### Syntax of Datalog
- A definite clause is either:
	- an atomic symbol (a fact)
	- or a rule of the form:
		- a [head] <- b1 ^ ... ^ bm [body]
			- where a and bi are atomic symbols
	- Query is of the form ?b1 ^ ... ^ bm.
	- Knowledge base is a set of definite clauses.

#### Example Data: 
The following table:
![[Pasted image 20250430101411.png]]
Can be represented by the followin facts:
- scheduled(cs111, 7, 830, dp101).
- scheduled(cs422, 2, 1030, cc208).
- scheduled(cs502, 1, 1230, dp202).

A student is busy when they have a class:
- busy(StudentNum, Time) <- enrolled(StudentNum, Course, Section) ^ scheduled(Course, Section, Time, Room).

#### Semantics - The General Idea: 
- Semantics specifies the meaning of sentences in the language
- An interpretation specifies:
	- What objects (individuals) are in the world
	- The correspondence between symbols in the computer and objects & relations in world
		- Constants denote individuals
		- Predicate symbols denote relations

#### Formal Semantics:
- An interpretation is a triple I = <D,φ,π> where:
	- D is the domain (and is a non empty set). Elements of D are individuals.
	- φ is a mapping that assigns each constant to an element of D. Constant c denotes individual φ(c).
	- π is a mapping that assigns to each n-ary predicate symbol a relation:
		- A function from D^n into {TRUE,FALSE}

#### Example Interpretation:
- Constants: Scissors, Phone, Pencil
- Predicate Symbol: Noisy(unary), left_of(binary).
gang I cant type a fuckin pencil so sorry to anyone reading this but check out slide 12 for the photo
![[Pasted image 20250430103427.png]]

#### Important points to note:
- The domain D can contain real objects
	- a person
	- a room
	- a course
- D cant necessarily be stored in a computer
- π(p) specifies whether the relation denote by the n-ary predicate symbol p is true or false for each n-tuple of individuals
- if predicate symbol p has no arguments, then π(p) is either TRUE or FALSE

#### Truth in an interpretation
- An interpretation is just a way to say:
	- What objects exist
	- What constant names refer to which objects
	- What relationships are true between those objects

-  "A constant c denotes in I the individual φ(c)"
	- If you use a name like "kim", the interpretation tells us who or what that actually refers to in the real world.
	- φ(kim) might refer to a person called kim

- "p(t1, ..., tn) is true if π(p)(〈φ(t1), ..., φ(tn)〉) = TRUE"
	- You're checking some statement like in(kim, r123) is true
	- To do that you:
		- Look up what kim and r12 refer to using φ
		- Ask "is that combination actually in the 'in' relationship"
			- if yes -> true
			- if no -> false
- 〈φ(t1), ..., φ( tn)〉 ∈ π(p)"
	- Some cringe way of saying:
		- "Ah the combination of real world things that the names refer to is listed as true for this relationship"

#### Models and Logical Consequences:
- A knowledge base, KB, is true in interpretation I iff:
	- every clause in KB is true in I.
- A model of a set of clauses is an interpretation in which all clauses are true.
- If KB is a set of clauses, and g is a conjunction of atoms:
	- g is a LOGICAL CONSEQUENCE of KB (written KB|=g) if g is true in every model of KB.
	- KB |= g if there's no interpretation in which KB is true and g is false.
#### User's view of Semantics
1. Choose a task domain
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
