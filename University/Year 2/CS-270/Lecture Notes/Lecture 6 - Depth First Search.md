BFS uses FIFO queues
DFS uses LIFO Stacks

## Fundamental DFS:
- DFS recursively visits the next unvisited vertex, extending the current path as long as possible until it gets "stuck" at a leaf with no path. Then it backtracks until a new avenue opens up for it to travel down.

- DFS creates a depth-first forest composed of several depth first trees which are the rooted spanning trees of the connected components.

### DFS Computes:
- The parent of each vertex (pi)[u] where u is the verted in the DFS tree (parents of the initial vertices are NIL).
- Also discovery d[u] where the vertex is first counted, initialised to infinity.
- Finishing time f[u] when the search has finished, utilising adjacent vertices.

### DFS on directed graphs: 
- Directed spanning tree (woah :o)
- Unlike BFS, the root here is not that important.
- This covers all vertices via a directed spanning forest.

- DFS does not contain shortest paths. They explore graphs in an "adventurous" way vs BFS' safer way.
- DFS can be used for scheduling

### Directed Acyclic Graphs (DAGs)
- Useful for scheduling
- a -> b -> c means action a must be carried out before b, and b before c. 
- If there is a cycle, (aka not a DAG) then you cannot satisfy all requirements

### Topological Sort: 
- Given a dag G modelling a scheduling task, a basic task is to find a linear ordering of vertices (actions) such that all dependencies are respected.
- This can be done via topological sorting:
	- Ordering linearly its vertices such that for every arc (u,v), u appears before v.
- To topologically sort a dag G, we must run DFS on G and print the vertices in reverse order of finishing times.
- An arbitrary digraph is a DAG if it has a topological sorting
	- the runtime of running topological sort on a DAG is linear.


## DFS is non-deterministic
- it allows choices:
	- 1 in Line 4 of the main body, running through all vertices in  
		the graph — any order of the vertices can be used;  
	- 2 in Line 3 for the recursive procedure, running through all  
		neighbours — any ordering of the neighbours can be used
	