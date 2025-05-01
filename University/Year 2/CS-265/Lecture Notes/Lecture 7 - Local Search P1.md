#### Minmax with a "Stupid" opponent:
- For every game tree, the utility obtained by MAX using minmax decisions against a suboptimal MIN will never be lower than the utility obtained playing against an optimal MIN.
- Other strategies against unoptimal opponents may do better than the minmax strategy however these strategies necessarily do worse against optimal opponents.

#### Properties of Minimax Search:
Note:
b - maximum branching factor for "reasonable" games
d - depth of the least cost solution
m - maximum depth of the state space
- Complete
	- Yes, if the tree is finite
- Optimal
	- Yes, against an optimal opponent
- Time
	- O(b^m)
- Space
	- O(b^m)

#### Alpha-beta pruning
- General configutation (MIN Version)
	- Compute MIN-VALUE at some node n
	- Loop over n's children
	- Who cares about N's value? MAX
	- let a be the best value that MAX can get at any choice point along the current path from the root
	- If n becomes worse than a, MAX will avoid it (so we can stop considering n's other children[bad enough it wont be played])
- MAX version is symmetric

- Case A:
	- m is the best value (to max) found so far on the current path
	- if n is worse than m, max will void it (prune that branch)
	- if m is better than n for player, we will never get to n in play
	- define beta similarly for min
	- alpha -> best choice found so far for MAX
	- beta -> best choice found so far for MIN
#### Local Search:
- Looks at the environment, makes small changes & looks to make a goal state

#### Iterative Improvement Algorithms:
- In many optimisation problems, the path is irrelevant and the goal state is the solution
- The state space -> set of "complete" configurations
	- Find an optimal config (TSP) or
	- Find configurable satisfying constraints
- in such cases, we can use iterative improvement algorithms:
	- keep a single "current"  state, try to improve it (idea)
- Constant space
	- Suitable for online and offline search

#### Travelling Salesperson Problem:
- Given a list of cities and the distances between them each pair of cities, whats the shortest possible route that visits ech city and returns to the origin city?
- TSP is an NP-hard problem in combinational optimisation
- Importance in operations research and theoretical computer science

#### TSP - Towards a solution
- Start with any complete tour and perform pairwise exchanges
	- Variants of this approach get within 1% of optimal very quickly with thousands of cities

