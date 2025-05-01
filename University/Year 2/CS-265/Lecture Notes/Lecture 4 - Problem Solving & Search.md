#### SINGLE-STATE PROBLEMS: (flesh out)
- Initial State
- Successor Function
- Goal Test
- Path Cost
- Solution
	- Sequence of actions leading from initial state to goal state

#### SELECTING A STATE SPACE:
- Real world complex as shit
	- State space must be abstracted for problem solving
	- Each abstract action should be "easier" than the original problem
- Abstract State <-> Set of real states
- Abstract action <-> Complex combination of real actions

#### E.G: VACUUM CLEANER ROBOT:
- States:
	- 8 Possible states (2^ 3 representing 2 rooms, each with 2 booleans (robot position, and if each is dirty))
- Actions:
	- Arc inscriptions
	- plus NoOp
- Goal Test:
	- No Dirt
- Path cost:
	- 1 unit per actions
	- 0 units for NoOp (NoOp is "no operation", as in nothing needed)

#### TREE-SEARCH ALGORITHMS:
- Basic Idea:
	- Offline, simulated exploration of state by generating successors of already explored states (explanding states)

#### STATE VS NODES:
- A state is a representation of a physical configuration
- A node is a data structure constituting part of a search tree and includes parent, childen, depth, path cost g(x)
- States do not have parents, children, depth or costs
- Expand function creates new nodes, filling in the various fields and using SuccessorFn of the problem to create the corresponding states

#### PERFORMANCE MEASURES:
- Completeness - Is the algorithm guaranteed to find a solution when there is one?
- Optimality - Does the strategy find the optimal solution
- Time complexity - How long does it take to find a solution
- Space complexity - How much memory is needed to perform the search?

Time and space complexity are measured in terms of:
- b 
	- Maximum branching factor of search tree
- d
	- depth of the least-cost solution
- m
	- maximum depth of the state space (may be inf)

#### PROPERTIES OF BFS:
- Completeness:
	- Yes (if b is finite)
- Time complexity:
	- O(b^(d+1)) - Exponential in d
- Space complexity
	- O(b^(d+1)) - Every node kept in memory

#### UNIFORM-COST SEARCH
- Expand least cost unexpanded node
- Implementation:
	- Fringe - queue ordered by path cost (lowest first)
- Equivalent to BFS if step-cost is all equal

#### Ask with iterating deepening, can you take advantage of previous - shallower searches or do you need to reproduce those again

