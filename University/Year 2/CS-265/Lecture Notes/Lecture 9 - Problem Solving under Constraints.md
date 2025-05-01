#### Constraint Satisfaction Problem:
- A CSP is characterised by:
	- A set of variables V1, V2, ..., Vn
	- Each variable Vi has an associated domain dom(Vi) which specifies the set of possible values the variable can take.
		- We assume domains are infinite
	- A total assignment is an assignment of a value to each variable
	- A hard constraint on a subset of variables specifies which combinations of values are legal. 
		- The legal assignments are said to satisfy the constraints
	- A solution to CSP is a total assignment which satisfies all constraints.

#### CSP Example: Map Colouring:
- Assign a colour (red/green/blue) to each state so neighbouring states have differing colours
	- What are the variables?
	- What are the domains?
	- How many total assignments are there?
	- What are the constraints?

#### CSP Variants
- What is the aim?
	- Determine if a solution exists or not
	- Find a solution
	- Find all solutions
	- Count the number of solutions
	- Find the best solution given some solution quality
		- Soft constraints specify preferences
	- Determine whether some property might hold in all of the solutions

#### Hard vs Soft Constraints:
- Given a set of variables, assign a value to each variable that either:
	- Satisfies some set of constraints (satisfiability problems)
		- HARD CONSTRAINTS
	- Minimises some cost function where each assignment of values to variables has some cost (optimisation problems)
		- SOFT CONSTRAINTS
- Many problems are a mix of both, known as constrained optimisation problems

#### Generate-and-Test Algorithm
- Generate the assignment space
	D = dom(V1) x dom(V2) X ... X dom(Vn).
	Test each assignment with the constraints
	E.G: D = dom(A) × dom(B) × dom(C) × dom(D) × dom(E)  
	= {1,2,3,4} × {1,2,3,4} × {1,2,3,4} × {1,2,3,4} × {1,2,3,4}  
	= {⟨1,1,1,1,1⟩, ⟨1,1,1,1,2⟩, ..., ⟨4,4,4,4,4⟩}
- Can be implemented with n-nested FOR-loops.

#### Backtracking Algorithms:
- Systematically explore D by instantiating the variables one at a time
- Evaluate each constraint predicate as soon as all its valuables are bound
- Any partial assignment that doesnt satisfy the constraint can be pruned
- Example:
	- Variables A,B,C each with domain {1,2,3,4}
	- Constraints: A < B, B < C
	- Assignment A = 1 ∧ B = 1 is inconsistent with  
		constraint  regardless of the value of the  
		other variables.

#### CSP as Graph Searching:
- a CSP can be solved by graph-searching
- A node is an assignment of values to some of the variables
- Suppose node N is the assignment X1 = v1, ..., Xk = vk
	- select a variable Y that isnt assigned in N
	- for every value Yi in domain(Y), the node X1 = v1, ..., Xk = vk, Y = Yi is a neighbour if it is consistent with the constraints that can be evaluated.
- The start node is the empty assignment
- A goal node is the total assignment that satisfies the constraints
- The search space depends on which variable is selected to be assigned for each node.
	- There are no cycles and no multiple paths to a node
