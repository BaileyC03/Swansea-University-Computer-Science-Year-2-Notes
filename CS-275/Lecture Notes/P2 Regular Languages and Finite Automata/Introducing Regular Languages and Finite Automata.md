#### Right-linear grammars
- A grammar is right-linear if all the rules are of form:
	- T -> e or
	- T -> aR
	- assuming R element of N and a element of Σ
- We shall now also allow the form: 
	- T -> a as an abbreviation for:
		- T -> aQ
		- Q -> e

#### Defining non-deterministic finite automata
- Definition:
	- A non-deterministic finite automaton over an alphabet Σ is given by: 
		- A set V of states
		- A transition relation  δ ⊆ V × Σ × V
		- A start state s [element of] V 
		- a set of accepting (or final) states F [subset of] V.

#### OMG LOOK ITS A FINITE STATE AUTOMATON!
![[Pasted image 20250419135055.png]]

#### A run of an automaton:
- Definition:
	- A non-deterministic finite automaton over an alphabet Σ is given by: 
		- A set V of states
		- A transition relation  δ ⊆ V × Σ × V
		- A start state s [element of] V 
		- a set of accepting (or final) states F [subset of] V.
	- A run of an automaton A over a word w [element of] Σ* is a word q0q1...q|w| [element of] V* such that q0 = s
		- and ∀i < |w| (qi , wi , qi+1) ∈ δ. If q|w| ∈ F ,
			- aka for all i less than |w|,  (qi, wi and qi+1) are all within the transition relation.
		- If q|w| is an element within F (the final states), it is accepting. If not? It's rejecting.
	- We let L(A) be the language of all words accepted by A.
- Now in real people words:
	  AKA trace it on the automata and if there is a path you can take following the words which takes you to a terminal state, youre cooling. 

#### Reversal of a language
- Definition:
	- Given a word w [element of] Z*, let its reversal w^R [element of] Z* be defined by:
		- |w^R| = w and
		- w^R(i) = w(|w| - i - 1)
		- This is literally just that w^R is w read backwards
	- Given a language L [subset of] Σ*:
		- let L^R := {w^R | w [element of] L}.

#### Outlook:
- Deterministic automata would be even nicer.
- Regular languages are closed under union, intersection, interleaving
- REGEXES :o 
