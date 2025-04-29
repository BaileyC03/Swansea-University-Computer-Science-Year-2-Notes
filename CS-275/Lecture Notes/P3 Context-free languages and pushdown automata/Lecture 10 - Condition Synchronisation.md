#### Consistency Algorithms
- Idea:
	- Pruning the domains as much as possible before selecting values from them.
	- A variable is **domain consistent** if no value of the domain of the variable is ruled impossible by any of the constraints
	- a CSP is domain consistent if all of its variables are domain consistent

#### Constraint Network
- Oval shaped node for each variable
- Rectangular node for each constraint
- Domain of values associated with each variable node
- Arc from variable X to each constrain which involves X
- An arc is written as "⟨X, r(X, Y)⟩
![[Pasted image 20250225121238.png]]

#### Arc Consistency
- An arc is arc consistent if, for each value x (member of) dom(X), there is some value y(member of) dom(Y) such that r(x,y) is satisfied.
- A network is arc consistent if all of its arc are arc consistent.

#### Arc Consistency Algorithm:
- The arc cans be considered in turn making each arc consistent
- When an arc has been made arc consistent, does it ever need to be checked again?
	- An arc ⟨X, r(X, Y)⟩ needs to be revisited if the domain of one of the Ys is reduced.
- 3 Possible outcomes when all arc are made arc consistent:
	- One domain is empty -> No solution
	- Each domain has 1 value -> Unique solution
	- More than one value -> May or may not be a solution

#### Complexity of Checking Arc Consistency (GAC)
- Consider Binary Constraints
- Each variable domain is of size d
- There are e arcs
- Checking an arc takes time of O(d^2)
- ⟨X, c(X, Y)⟩ for each value for X, check each value for Y
- Each constraint needs to be checked at most d times.
- ⟨X, c(X, Y)⟩ rechecked when a value for Y is removed.
- Thus the algorithm GAC takes time O(ed^3)
- **SOLVING A CSP is an NP-Complete provlem the number of variables**
	- Given a solution can it be checked in polynomial time?
- But it can be made arc consistent in polynomial time. how?
	- Making the network arc consistent does not solve the problem, we need to search for a solution

#### Finding Solutions with AC and domain splitting
- To solve a CSP:
	- Simplify with Arc consistency
	- If a domain is empty, return no solution
	- If all domains have size 1, return solution found
	- Else, split a domain and recursively solve each half

#### Local Search for CSP:
General local search:
- Maintain a complete assignment of a value to  
	each variable.  
-  Start with random assignment or a best guess.  
- Repeat:  
- Select a variable to change  
-  Select a new value for that variable  
-  Until a satisfying assignment is found
Adapted for CSP:
- Aim: find an assignment with zero  
unsatisfied constraints.  
- Given an assignment of a value to each  
variable, a conflict is an unsatisfied  
constraint.  
- The goal is an assignment with zero  
conflicts.  
- Function to be minimised: the number of  
conflicts

#### Outlook: Uncertainty
- Let actions At = leave for airport t minutes before flight
- Will At get me there on time?
- Problems:
	- Partial observability
	- Noisy sensors
	- Uncertainty in action outcomes
	- complexity of modelling
- hence a purely logical approach either:
	- risks falsehood
	- Leads to conclusions too weak for decisionmaking

#### Formalisms for handling uncertainty
- Non monotonic logics
	- E.g: many-valued logics
	- E.g: Probabilistic Logic
	- E.g: Default logic
		- The default assumption when reasoning about a car is that it does not have a flat tyre.
	- E.g: Fuzzy Logic
		- Given the available evidence, x.
		- Handles degrees of truth not uncertainty

#### Probability:
- Probabilistic assertions summarise effects of:
	- Laziness (failure to enumerate all exceptions)
	- Ignorance (lack of relevant facts, initial conditions etc)
- Subjective / Bayesian Probability:
	- Probabilities relate propositions to one's own state of knowledge
	- Probabilities of propositions change with new evidence

#### Inference by Enumeration:
- Start with the joint distribution

#### Bayesian network topology
- Topology of network encodes conditional independence assertions:
- Weather, Toothache <- Cavity -> Catch
- Weather is independent of other variables
- Toothache and catch are conditionally independent given Cavity.