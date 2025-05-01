#### Consistency Algorithms:
- Idea:
	- Prune the domains as much as possible before selecting values from them.
- A variable is domain consistent if no value of the domain of the variable is ruled impossible by any of the constraints.

#### Constraint Network:
- There is an oval shaped node for each variable
- There is a rectangular node for each constraint
- There is a domain of values associated with each variable node
- There is an arc from each variable X to each constraint that involves X
![[Pasted image 20250305164156.png]]

#### Arc Consistency:
- An arc ⟨X, r(X, Y)⟩ is arc consistent if, for each value x within dom X, there is some value y within dom Y such that r(x,y) can be satisfied
	- AKA an arc is arc consistent if it can actually be satisfied by some combination of values of the nodes it connects.
- A network is arc consistent if all of its arcs are arc consistent.

#### Arc Consistency Algorithm
- The arcs can be considered in turn making each arc consistent.
- When an arc has been made arc concistent, does it ever need to be checked again?
	- An arc ⟨X, r(X, Y)⟩ needs to be revisited if the domain of one of the Ys is reduced 
- Three possible outcomes when all arcs are made arc consistent:
	- One domain is empty -> No solution
	- Each domain has a single value -> Unique solution
	- Some domains have >1 value -> May or may not be a solution

#### Complexity of Checking Arc Consistency:
AKA GAC
- Consider binary constraints
- Each variable domain is of size d
- There are e arcs
- Checking an arc takes time O(d^2)
- ⟨X, c(X, Y)⟩ for each value of X, check each value of Y
- Each constraint needs to be checked at most d times.
- ⟨X, c(X, Y)⟩ rechecked when a value for Y is removed.
- Thus the algorithm GAC takes time O(ed^3)
- Solving a CSP is an NP-complete problem given the number of variables
	- Given a solution is can be checked in polynomial time
- But it can be made arc consistent in polynomial time?
	- Making the network arc consistent doesnt solve the problem, you still need to search for the solution! 

#### Finding solutions with AC and domain splitting
- To solve a CSP:
	- Simplify with arc-consistency
	- If a domain is empty, return no solution
	- If all domains have size 1, return solution found
	- Else, split a domain and recursively solve each half

#### Local Search for CSP: 
- General Local Search:
	- Maintain a complete assignment of a vlue to each variable
	- Start with random assignment of a best guess.
	- Repeat:
		- Select a variable to change
		- Select a new value for the 
	- Until a satisfying assignment is found

- Local Search adapted from CSP:
	- Aim: find an assignment with zero unsatisfied constraints.
	- Given an assignment of a value to each variable, a conflict is an unsatisfied constraint.
	- The goal is an assignment with zero conflicts
	- Function to be minimised:
		- Number of conflicts

#### Uncertainty:
- Some things are not certain, like "will leaving at time X get me to an airport before my flight?"
- This has problems:
	- Partial observability
		- State of roads, other drivers plans etc
	- Noisy sensors
		- Traffic reports, modern SatNav
	- Uncertainty in action outcomes
		- Flat tyre, etc...
	- Immense complexity of modelling and predicting traffic
- These result in a purely logical approach either:
	- Risking falsehood
		- "If I leave 25 mins early ill make it 100%"
	- Leading to conclusions that are too weak for decision making
		- "If I leave 25 mins early ill make it assuming X, Y, Z, A, B and C factors"

#### Formalisms for handling uncertainty:
- Non monotonic logics
	- E.G: Many-Valued Logics
		- Introduction of an additional truth value for unknown

	- E.G: Probabilistic Logic
		- A25 -> 0.3AtAirportOnTime
		- Sprinkler -> 0.99WetGrass
		- WetGrass -> 0.7Rain

	- E.G: Default Logic
		- When reasoning about a car, the default assumption is that it does not have a flat tyre.
		- When reasoning about birds, the default assumption is that they can fly
			- What default assumptions are reasonable 
			- How do we handle contradictions?

	- E.G: Fuzzy Logic
		- Given the available evidence:
			- A25 will get me there on time with probability 0.04
		- Fuzzy logic handles degrees of truth not uncertainty (E.g: wetGrass is true to degree 0.2)

#### Probability
- Probabilistic assertions summarise effects of:
	-  Laziness
		- Failure to enumerate all exceptions, qualifications etc
	- Ignorance
		- Lack of relevant facts, initial conditions etc

- Subjective of Bayesian probability:
	- Probabilities relate propositions to one's own state of knowledge
		- E.G, P(A25 | no reported accidents) = 0.06
	- Probabilities of propositions change with new evidence
		- E.G: (A25 | no reported accidents, 5am) = 0.15

#### Making decisions under uncertainty
- Assume you believe the following:
	-  P(A25 gets me there on time | ...) = 0.04
	- P(A90 gets me there on time | ...) = 0.70
	- P(A120 gets me there on time | ...) = 0.95
	- P(A1440 gets me there on time | ...) = 0.9999
- Which action do you choose?
	- Depends on your preferences for missing flights vs airport cuisine etc...
	- Utility theory is used to represent and infer preferences
	- Decision theory = utility theory + probability theory

Prior probability & Joint distribution
- Prior or unconditional probabilities of propositions
	- E.g: 
		- P(cavity = true) = 0.1 and
		- P(weather = sunny) = 0.72
	- Correspond to belief prior to arrival of any(new) evidence.
- A probability distribution gives values for all possible assignments
	- P(weather) = ⟨0.72, 0.1, 0.08, 0.1⟩
		- NORMALISED - adds up to 1
- Joint probability distribution for a set of random variables gives the probability of every atomic event on those random variables. 
- P(weather, cavity) = 4x2 matrix of values
![[Pasted image 20250305171009.png]]

#### Conditional Probability:
- Conditional or posterior probabilities
	- E.G: P(cavity | toothache) = 0.8
		- given toothache is all IK is true
- If we know more, like cavity is also true, then we have:
	- P(cavity | toothache) = 1
	- The less specific belief remains valid after more evidence arrives however may not be useful
- New evidence may be irrelevant, allowing simplification:
	- P(cavity|toothache, sunny) = P(cavity|toothache) = 0.8
- This kind of inference, sanctioned by domain knowledge, is crucial.

#### Definition of conditional probability:
![[Pasted image 20250305171300.png]]
- Product rule gives an alternative formulation
	- P(a ∧ b) = P(a | b)P(b) = P(b | a)P(a)

- Chain rule is derived by successive application of product rule

#### Inference by enumeration:
- Start with the joint distribution
![[Pasted image 20250305171538.png]]
- For any proposition, calculate the sum of all atomic events
![[Pasted image 20250305171612.png]]
![[Pasted image 20250305171700.png]]
- Essentially youre cutting down the "domain" to be only those in which toothache is true, and then calculating the chance of having a cavity within that smaller pool

#### Bayesian Network Topology
- Topology of network encodes conditional independence assertions:
![[Pasted image 20250305171927.png]]
- Weather is independent of other variables
- Toothache and Catch are conditionally independent, given cavity.
- The meaning of the arrow X -> Y
	- means that X has a direct influence on Y, which suggests that causes should be parents of effects.
