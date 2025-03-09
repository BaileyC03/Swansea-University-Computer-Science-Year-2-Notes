#### Motivating Example
- We had seen the grammar:
	- S -> aTb
	- T -> ε
	- T -> TXY
	- YX -> XY
	- aX -> aa
	- Yb -> bb
	to describe the language {a^n b^n | n > 0}

- The context-free grammar:
	- S -> aSb
	- S -> ab
	describes the same language {a^n b^n | n >0} much more elegantly

- Is there a right-linear grammar for this job? 
- Is there a finite automaton for this job? 

#### The pidgeonhole principle
- If you try to fit more pigeons than you have holes, some holes get more than one pigeon.

#### Why is a^n b^n not regular? 
- If {a^n b^n | n > 0} were regular, there would exist a finite automaton for it.
- Then there is a state v and numbers i != j (within) N such that the automaton is in state v after reading both a^i and a^j 
- But then the automaton is also in the same state after reading a^i b^j and a^j b^i. 
	- It's meant to accept the former and reject the latter
- Henceforth: Contradiction [cringe]

#### Aside: Useful Info:
If a language is regular, any string within the language can be pumped any number of times and still be within the language.


#### The Pumping Lemma:
- f L is regular, then ∃k ∈ N such that ∀p ∈ L, |p| ≥ k there exists  (∃) a splitting p = uvw where |uv | ≤ k and v != ε such that ∀i ∈ N it holds that uv i w ∈ L.
- But what the fuck does this mean I hear you ask?
	- Good question. I still dont know but below is another explanation

- For all k (element of) Natural numbers
	- you can pick a word P (element of) L with |p| >= k
- Such that however p is written as p = uvw 
	- Subject to |uv| <= k and v is not the empty set.
- you can find some Natural Number i such that uv^i w (not an element of) L,
- then L is not regular.

#### Pumping Lemma: Youtube video notes because what are these slides about?
https://www.youtube.com/watch?v=qtnNyUlO6vU
- Pumping lemma states that if a language is regular, every string in the language has a section which can be repeated (or pumped) any number of times and still be in the language.  
- Or, all strings in the language can be repeated - "pumped" - if they are at least as long as a certain length. [The pumping length, P]
- We can commonly assign the P (pumping length) to be the size of the automata thingy
	- 3 nodes? P is 3
- This implies a "loop" in our FSM
- We can split this into 3 parts:
	- 1. Pre pumping [can be empty]
	- 2. The pumped part [NOT ALLOWED TO BE EMPTY >:o]
	- 3. Post pump  [can be empty]
- The "pumped" part must be less than or equal to the "p" number and must occur in the first "p" symbols. 
#### Pumping Lemma: In Application
- Question:
	- Is L(pal) = {u ∈ {a, b}∗ | u = uR} regular?
		- We get some natural number k
		- We pick a^k ba^k within L(pal).
		- if uvw = a^k ba^k, |uv| <= k and v is not the empty set, then v = a^I for some 1 <= I <= k. so uv^2w = a^k+1 ba^k (not element of) l(pal)

#### Pumping Lemma: In Application (Non stupid version)
- We look to do a proof by contradiction
-  Let's say we want to prove a language is not regular
	- B = {0^n 1^n | n >= 0} 
- First we claim it is regular, which gives us a pumping length P from the pumping lemma (explained in a previous paragraph)
- For all strings in the language of length P, there is a section that can be pumped any number of times
- We must find a string that is at least length P that breaks the pumpng lemma.
	- In our example, 0^p 1^p works
- According to the pumping lemma, this should be split into 3 diff components (pre, pump, post) [pre , post can be empty]
	- In our example we have 3 options for the pump
		- the 0^p
			- End up with string of all 0s which doesnt belong in our language
		- All 1s
			- End up with string of all 1s which doesnt belong in our language
		- Both
			- We end up with a string of 01010101 which doesnt belong in the language
	- Therefore, 0^p 1^p cannot be pumped 
	- And because there is 1 or more options which cannot be pumped, it does not satisfy the pumping lemma
	- And therefore is not a regular language
- Side note: 
	- If we remembered the pumped part must be within the first P symbols, we could have eliminated "all 1s" and "both" before it even begun.


