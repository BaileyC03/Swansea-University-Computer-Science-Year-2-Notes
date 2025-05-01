![[Pasted image 20250303232804.png]]
### Optimality of A*:
- f(n) = g(n) + h(n)
- For node S:
	- g(S) = 0 [path cost of S]
	- h(S) = 7 [heuristic estimation to reach goal]
	- f(S) = 0+7 = 7
- Calculate:
	- f(A) = 1+6 = 7
	- f(G) = 5+0 = 5
- Actual goal cost needs to be greater than estimated cost.
	- Therefore estimates need to be less than actual cost

#### Admissible Heuristics:
- A heuristic h is admissible (optimistic) if:
	- 0 <= h(n) <= h*(n)
- coming up with admissible heuristics is the most important aspect of using A* in practice.

#### Contours:
- A* Expands nodes in order of increasing f value
- Gradually add "f-contours" of nodes.
- Contour i has all nodes with f = fi where fi < f(i+1)
- In comparison: Breadth-first search adds layers

#### Properties of A*:
- Complete
	- Yes, unless infinite nodes with f<= f(G)
- Time:
	- Exponential (relative error in h x length of solution)
- Space:
	- Keeps all nodes in memory
- Optimal:
	- Yes, cannot expand f(i+1) until f(i) is finished.

- A* expands:
	- all nodes with f(n) < C*
	- some nodes with f(n) = C*
	- no nodes with f(n) > C*
- where C* is the cost of the optimal solution

#### Termination of A*
- Only stop when you *DEQUEUE* a goal.

#### Applications of A*
- Video games
- Pathfinding / routing problems
- Resource planning problems
- Robot motion planning
- Language analysis

#### Summary:
- Heuristic functions estimate costs of shortest path
	- Good heuristics can dramatically reduce search cost
- Greedy best-first search expands lowest h
	- incomplete and not always optimal
- A* search expands lowest g+h
	- complete and optimal
	- also optimally efficient (up to tie-breaks, for forward search)
