#### Right-linear Grammars: 
- A grammar is right-linear if all rules are of the form:
	- T-> ε
	- T -> aR [the part that makes this right linear is the R comes AFTER the a]
		- T, R are both natural numbers
		- a ∈ Σ.
			- This means that a is within the alphabet of the grammar. 

#### Non-deterministic finite automata
- Definition:
	- A non-deterministic finite automaton over an alphabet Σ is given by:
		- a set of states [V]
		- a transition relation [δ ⊆ V × Σ × V]
		- a start state [s ∈ V]
		- a set of accepting (final) states [F ⊆ V .]

#### The run of an automaton
- Definition:
	- The set of all accepted words is the language of an automaton, written as L(A).
	- it reads in a word letter by letter, following a path through its states. 
	- It starts at the initial state and moves according to the transition rules. 
		- If it ends at an accepting (final) state, the word is accepted.
		- If not, word is rejected

#### Equivalence: 
- Theorem:
	- Right linear grammars and non-deterministic automata describe the same languages
		- AKA - regular languages
- Proof (Sketch).
	- We translate back and forth:
		- Non-terminal symbols correspond to states 
		- We have a rule T -> ε iff the state T is final.
		- we have a rule T -> aR iff there is a transition 
			(T , a, R) ∈ δ.

#### Reversal of a language: 
- Definition:
	- if a word W is within the alphabet of automaton L
	- the word backwards is within the backwards automaton L^r
- Theorem:
	- if L is regular, L^r is
	- 