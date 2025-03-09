#### Spanning Trees: 
- A spanning tree is a connected graph with no cycles
- Representing Rooted Trees:
	- A rooted tree is a tree together with a root.
	- This gives direction, from the root to the leaves
		- Leaves are nodes without children
		- The root is the only node without a parent
	- we use pi to represent the parent of a node.
	- π[5] = 4 <- This means the parent of node "5" is 4.

#### Spanning Forests:
- A graph (G) has a spanning tree if G is not empty and is connected.
- However every graph has a spanning forest
	- If we have a disconnected graph, we can split it into connected components and consider them separately.
``
#### Breadth First Search (BFS):
- This search starts from a source vertex *s* and constructs a rooted spanning tree for the graph, also known as a BFS Tree. (The root is s)
- BFS uses a queue (FIFO) for its main data structure
- BFS computes the parent π[x] = y of each vertex x in the BFS tree (the parent of the root is NIL)
- The specialty of BFS is it also computes the distances d[x] of the source s (initialised to infinity). This is also the length of the path from s (root) to x (current node)
- This the BFS contains the shortest paths from s to any other vertex and is such considered an SPT

#### The Basic Idea:
- Assume we start with a graph G and a root s
	- We now want to visit everything reachable from s
	- we do this in layers:
		- First everything reachable in 0 steps (s)
		- Then everything reachable in 1 step (Neighbours of s)
		- Then everything reachabe in 2 steps: (neighbours of neighbours of s)
		- etc.. etc...
	- We need to keep an eye on which vertexes we've visited / completed. Hence - a queue.

### Why do we shortest paths? 
- S gets the correct distance of 0 and is the only vertex with that distance
- Exactly neighbours from S get a distance of 1
- All unexplored neighbours of these vertices get a distance of 2 etc etc 
- We can assume we found all vertices with distance <= k *and* the unexplored neighbours at distance K  are then precisely the vertices at distance k+1 and indeed they get this distance assigned


### Running BFS on a disconnected graph:
- We make a spanning *forest* not spanning trees
- Restart BFS on each spanning tree in the spanning forest
- maintain old (pi) and d values
- repeat until all vertices reached

You'll need to restart BFS X times where X is the number of connected components in the graph.


### Running BFS on directed graphs:
- For digraphs we have directed spanning trees
- Only the vertices reachable from S following the directions defined in the graph are in the directed tree.
- Still, the paths from S to any reachable vertex are the shortest possible
- BFS still computes shortest distance for this
- Sometimes you may need to do it on a spanning forest. Remembering the d-array prevents overlap.
- Each tree in a directed spanning forest must have no common vertices, this ensures BFS runs in linear time.
- 