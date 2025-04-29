#### Some Questions:
- We've spoken about what we can and can't computer, but what can we compute fast?
- What would fast even mean?
- Are nont-deterministic turing machines a thing?
- What kind of questions can theoretical computer scientists not solve? 

file:///home/bailey/Downloads/day28-pvsnp.pdf

#### Defining P and NP
Definition:
- Let P be the class of all languages decidable in a polynomial time by a deterministic TM.
- Let NP be the class of all languages decidable in polynomial time by a non-deterministic TM.
Question:
- Is P = NP?
	- We dont know (most people think no)
	- We know of a lot of proof techniques that they dont work for this
	- If the answer is yes, cryptography doesnt work

#### Karp Reduction
Definition:
- We say a language L 1 is karp-reducible to a language L2 if there is a polynomial-time computable function such that a word within L1 <=> f(word) within L2.

#### NP - Completeness
Definition:
- We can call a language L NP-complete if:
	- if L (within) NP and
	- for every L2 (within) NP it holds that L2 <=p L
		- We konw an insane amount of NP complete languages
		- If we find a polynomial-time algorithm for a single NP-complete language, then P = NP.
		- If we can prove for a single NP-complete language that it is not in P, then P /= NP.

#### Example of an NP-complete Language:
Definition:
- A hamiltonian cycle in a graph is a cycle visiting each vertex exactly once.
- In other words, you have to traverse the graph visiting each vertex exactly once, never traverse the same edge twice and end on the starting verted.
Proposition:
- The languages of all graphs having a Hamiltonian cycle is NP-complete.

#### Satisfiability:
Definition:
- The instances of SAT are formulas built up from boolean variables x0, x1, ....., negation ¬ and and ∧ and or v. 
- An instance is positive if there is an assignment to the variables making the formula true.
- Proposition:
	- SAT is NP-complete.

- SAT-solver
	- A SAT-solver is an algorithm for the SAT-problem.
	- Existing SAT-solvers typically have exponential worst-case runtime but do fine on lots of insances - including instances with length in the millions.
	- SAT solvers are used in industry for things like chip design and railway verification

#### A Local Success Story:
Definition:
- a triple a,b,c (within) N is called a pythagorean triple iff a^2 + b^2 = c^2
Question:
	Can we colour each natural number red or blue in such a way that there is no monochromatic pythagorean triple? 

#### Translating to SAT
- For each N (within) N [as in nat number], we can easily write down a SAT-instance expressing "We can colour all numbers up to N while avoiding monochromatic Pythagorean triples"
- Oliver Kullman did this and ran his CUBE-SAT solver on it.
- There are about 10^2355 colourings up to 7825.
- The proof produced by the SAT solver was >200tb large
- Largest mathematical proof ever found :o 

#### Probabilistic and Quantum:
- Besides non-determinism, we can also consider probabilistic of Quantum TMs.
- we can define what polynomial time means in these models
- But we haven't fared any better in figuring out whether or not these models can actually do more in polynomial time than deterministic TMs.