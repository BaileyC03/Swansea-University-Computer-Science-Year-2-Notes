#### Regular Languages: 
- We call a formal language regular if there exists a right-linear grammar describing it. 
- Theorem: The following are equivalent for a formal language:
	- It is regular
	- There exists a left-linear grammar describing it
	- There exists a non-deterministic finite automaton describing it
	- There exists a deterministic finite automaton describing it
	- There exists a regex describing it
- Theorem: 
	- If L1 and L2 are regular languages, so are: 
	- L^R 1
	- L1 (intersect) L2
	- L1 (union) L2
	- Σ* \ L1
	- L1 o L2
	- L^* 1

#### Exercises: 
1. Find a left-linear grammar for the language {aab, bbbb}
		S -> Ab
		A -> a B 
		A -> b C
		B -> a
		C -> b D
		D -> b E
		E -> b
2. Try to construct a finite automaton for the language over the alphabet Σ = {a,b} of all words with exactly 3 b's in it. 
3. Try to construct a finite automaton for {a^nb^m | n,m (elements of) N}
