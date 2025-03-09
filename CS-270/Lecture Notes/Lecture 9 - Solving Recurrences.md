We present a basic tool for analysing algorithms by Solving Recurrences
#### Divide and Conquer Paradigm:
- Divide
- Conquer
- Combine

We use recurrences to characterise the running-time of a divide and conquer algorithm. Solving the recurrence gives us the asymptotic running time.

A recurrence is defined in terms of:
- 1+ Base cases
- Itself, with smaller arguments

#### EXAMPLES FOR RECURRENCES (1):
- lmao good luck idk what the fuck im looking at
- ![[Pasted image 20241223150355.png]]
- ![[Pasted image 20241223150406.png]]

#### MAIN TECHNICAL ISSUES WITH RECURRENCES:
- Exact VS Asymptotic Functions
	- Sometimes we want the exact analysis of an algorithm.
	- Mostly, we want an asymptotic analysis however.
- Boundary Conditions
	- Runtime on small inputs is bounded by a constant
		- T(n) = (-)(1) for small n.
	- We usually dont mention this constant however as it doesnt affect the rate of growth
	- These are only important if we care about exact solutions
- Floors and Ceilings
	- A recurrence of a worst case runtime of merge sort is:
	![[Pasted image 20241223153639.png]]
#### RECURSION TREES: QUADRATIC GROWTH:
- The mergeSort recurrence:
	T(n) = n+2T(n/2)
	- the height of the tree is lg n
	- however this time, the "workload" of each level is n
	- so all workloads are the same

#### MASTER THEOREM:
- Let A>=1, B>=1 and C>=0 be constants.
- Let T(n) be defined by the recurrence:
	T(n) = aT(n/b) + Θ(n^c)
		(n/b represents the ceiling or floor of n/b)
- If so, the following is bound asymptotically as follows:
- if c < (logb a) then T(n) = Θ(n^(logb a))
- if c = (logb a)  then T(n) =  Θ(n^c lg n)
- if if c > (logb a) then T(n) =  Θ(n^c)

#### IN OTHER WORDS...:
- We start by an equation for T(n) of the form:
	T(n) = b^x * T(n/b) +  Θ(n^c)
	[where the x you have to find: x = logb a (so B^x = b(logb a) = a)]
- etc etc master theorem cringe as shit

#### GROWTH RATES AS RESPONSE RATES:
- The fundamental setting:
	- input size n>= 1 (but sometimes 0 is ok too)
	- Some 'abstract' runtime f(n) >= 1

- Understanding the growth rate of f(n) means:
	- understanding how a change of n effects f(n)
		- increasing n in a certain way, how much is f(n) increased?
- Thus, we get a DICTIONARY:
	- Slow growth - a big change of n causes only a small change of f(n)
	- Large growth - a small change of n causes a big change of f(n)
	- Intermediate growth - the change of n is kind of proportional to the change of f(n)

#### WAYS OF CHANGE:
The two most basic forms of quantitative change are: 
- Additive 
	- quantity (n or f(n)) is changed by adding a constant
	- small, relatively
- Multiplicative
	- quantity (n or f(n)) is changed by multiplying a constant
	- big, relatively

#### LINEAR GROWTH:
- Compared to other rates of growth, linear growth is in the middle
	- For pure algorithms, it is the bottom.
- Small change of n leads to a small change of f(n)
- big change of n leads to a big change of f(n)

#### POLYNOMIAL GROWTH:
- Polynomial means, roughly, a function f(n) = n^a for some constant a>=
	- sublinear - a < 1
	- superlinear - a > 1

- A big change in n yields a proportional change of f(n)

#### LOGARITHMIC GROWTH:
- This means roughly a function f(n) = logb(n) for some b > 1
- A big change in n leads to a small change in f(n)

#### EXPONENTIAL GROWTH:
- Roughly a function f(n) = b^n for some constant b > 1

#### CLOSING REMARKS:
- Algorithm fast if (and only if) growth rate is slow
- Algorithm slow if growth rate if (and only if) fast