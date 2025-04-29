- We've talked about what we can and can't compute but what can we compute reasonably fast?
- What does fast even mean in this context? 

#### Recap - O notation
Definition:
	We evaluate algorithms by counting how many steps that take on an input of a certain size
	The function itself is not too meaningful but O(T) is.
	Running the algorithm on a faster computer doesn't change O(T)

#### Run-tme.
- Fix a machine-style model of computation
- The time complexity of a given machine M is the function:
	- Tm : N -> N where:
		- T(n) is the maximum number of steps taken on an input length n
- A machine runs in polynomial time if there are natural numbers abk such that ∀n within N, Tm(n) <= an^k + b

#### Efficient Church-Turing thesis
- For reasonable deterministic models of computation, the notion of polynomial time coincides.
	- So we dont have to specify if we're talking 1tape TMs, 2tape Tms, java programs, python programs, register machines etc when talking about polynomial time
	- It is a convenient oversimplification to consider polynomial time computability to formalise whats actually computable

#### Connecting this to previous classes:
- Every language is decidable in time O(n)
- Context free languages are decidable in polynominal time
- It is not known if all context-sensitive languages are decidable in polynomial time (but prolly no)
- 