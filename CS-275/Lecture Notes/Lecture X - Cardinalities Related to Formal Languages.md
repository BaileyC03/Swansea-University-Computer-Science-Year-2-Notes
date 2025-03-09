#### More Terminology:
- We consider X countable if there is a surjection:
	- s N -> X
- Otherwise, it is uncountable
- A set X is infinite if there is an injection i: N -> X.
- The cardinality of N is called אo (read aleph-zero)

#### How big are formal languages? How many are there? 
- Proposition:
	- For a non-empty finite alphabet Σ, it holds that 
		- |Σ*| = |N|
- Corollary:
	- Every formal language is countable
- Corollary:
	- For a non empty finite alphabet Σ it holds that
		- |R| = |P(Σ∗)| = |P(N)| > |N|.
		- Read: There are uncountably many formal languages

#### How many grammars are there? 
- Proposition:
	- For a finite alphabet Σ, there are countably many grammars (up to renaming of non-terminal symbols).
- Corollary:
	- There are (way) more formal languages than there are grammars
	- There are formal languages not describable by any grammar

#### Looking at the details: 
- Let the alphabet be Σ = {0,1}.
- We want to code all context-free grammars as words over {0,1}.
- Without limitation of generality, we may assume that the non terminals are 
	- N = {S, T0, T1, T2, ...}
- As we do only context free rules, we dont need to worry about the -> in something like T2 -> 0(T1)011, we just code (T2)0(T1)011
	- This is because we always know the left side will have a single, non terminal

- We turn each individual rule in a word avoiding 11.
- The word begins with 101 if the rule starts with S->, and 10^(n+2)1 if the rule starts with Tn->
- Then, we continue with the right hand side, using 101 for 0, 1001 for 1, 10001 for S and 10^(n+4)1 for Tn
- Then, we smush together all the rules, separated by 11 each.

- Now every word w ∈ {0, 1}∗ codes a context free grammar Gw, and essentially every context-free grammar shows up as some Gw

- Considering the formal language
	- D = {w ∈ {0, 1}∗ | w /∈ L(Gw )}.
- Can it be context free? 
	- Naur :(

#### Ok but why care? 
- If we can code elements of a set X as words over some finite alphabet, we can use algorithms to compute with them.