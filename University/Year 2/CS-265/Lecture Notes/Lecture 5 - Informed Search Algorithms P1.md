#### Search Heuristics -> Informed (Heuristic) Search
- A heuristic is:
	- A function that estimates how close a state is to a goal
	- Designed for a particular search problem

#### Best-first search
- Idea: use an evaluation function for each node
	- estimate of "desirability"
		=> expand most desirable unexpanded node
- Implementation: "fringe" is a queue sorted in decreasing order of desirability
- Special Cases:
	- Greedy Search
	- A* Search

#### Greedy Search
- Evaluation function h(n) is a heuristic
	- It estimates the cost from n to the closest goal
- Greedy search expands the node that appears to be the closest goal.
#### Completeness of Greedy Search
- Time: O(b^m)
	- Good heuristics can give dramatic improvement
- Space: O(b^m)
	- All nodes are kept in memory
- NOT COMPLETE
	- Unless you use repeated state checking

#### General Summary: Greedy Search
- Strategy:
	- Expand a node that you think is closest to a goal state
- Heuristic
	- Estimate of distance to nearest goal for each state
- A common case:
	- Best-first takes you straight to the (wrong) goal
- Worst case
	- A badly guided DFS

#### Combining Uniform-cost Search (UCS) with Greedy Search
- Uniform-cost orders by path cost, or backward cost g(n)
- Greedy orders by goal proximity, or forward cost h(n)
- A* search orders by the sum f(n) = g(n) + h(n)

#### A* Search
- Idea:
	- Avoid expanding paths that are already expensive
	- Evaluation function f(n) = g(n)+h(n)
		- g(n) = cost so far to reach n
		- h(n) = estimated cost to goal from n
		- f(n) = estimated total cost of path through n to goal
- A* search uses an admissible heuristic 
	- i.e. h(n)<= h*(n) where h*(n) is the true cost from node n
- Theorem:
	- A* search is optimal