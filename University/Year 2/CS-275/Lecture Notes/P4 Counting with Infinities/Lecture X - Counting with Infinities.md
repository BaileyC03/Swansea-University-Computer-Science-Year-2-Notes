#### Injections, Surjections and Bijections
Definition:
- We call a function f: X -> Y
- an injection (or 1 - 1)
	- if ∀x, y ∈ X f (x) = f (y) ⇒ x = y
- Contraposition 
	- if ∀x, x2 ∈ X x1 ̸ = x2 ⇒ f (x1) ̸ = f (x2)
- Plain reading
	- every element in Y is the image of at most element of X
- A surjection (or a onto function)
	- f ∀y ∈ Y ∃x ∈ X f (x) = y
- plain reading
	- every element in Y is the image of some element from X
- bijection
	- both an injection and a surjection

#### Connection to Cardinality
- Let n = {0, 1, ..., n-1}. Observe that:
	- there is an injection from n to X iff X has at least n elements
	- There is a surjection from n to X iff X has at most n elements
	- There is a bijection from n to X iff X has exactly n elements

#### Some Facts: 
- There is an injection from X to Y iff there is a surjection from Y to X.
- If there is no inection from X to Y, there is an injection from Y to X
- If there is an injection from X to Y and an injection from Y to X there is a bijection from X to Y 

#### Cardinality
- Definition:
	- We write |X| <= |Y| if there is a surjection from Y to X.
	- By the previous observations, this is reuivalent to say there is an injection from X to Y.
	- We write |X| = |Y| if there is a bijection from X to Y
- For any two sets |X| <= |Y| or |Y| <= |X|
	- If |X| <= |Y|  and |Y| <= |X|, then |X| = |Y| 
	- If |X| ≤ |Y| and |Y| ≤ |Z|, then |X| ≤ |Z|
- We usually write |X| = n instead of |X| = |n|


#### SIDE NOTE:
{a,b}* means all words made from the set {a,b}

#### Infinite Cardinalities
- Proposition - |{2n | n ∈ N}| = |N| 
	- AKA there are as many even natural numbers as there are natural numbers
- Theorem - |Q| = |N|
	- AKA there are as many rational numbers as there are natural numbers

#### So it's all just infinity?
- Theorem:
	- There is no surjection φ : N → R.
- Proof:
- Let (Rn) n [subset of] N be a list of real numbers. We argue that the list cannot contain ALL real numbers
- pick r [subset of] R as follows: 
	- r = 0.n0n1n2... where ni is 3 if the i-th decimal digit of r is greater than 5 and ni=7 otherwise.
	-   Then, (∀n ∈ N)(r ̸ = rn).

#### Cantor's Theorem
- Theorem:
	- Let X be a set, there is no surjection φ X -> P(X)
		- Recall P(X) is the set of all subsets of X
- Proof:
	- Let φ : X -> P(X) be a function.
	- Consider Dφ := {x ∈ X | x /∈ φ(x)}.
	- Assume that there is some x0 ∈ X with φ(x0) = Dφ
		- (if φ  were surjection, there would need to be one
	- Does x0 ∈ Dφ = φ(x0) hold?
	- CONTRADICTION!

#### Questions to ask yourself:
- What are the possible cardinalities of formal languageS? 
- How many grammars are there?
- How many formal languages are thereDoes x0 ∈ Dφ = φ(x0) hold

