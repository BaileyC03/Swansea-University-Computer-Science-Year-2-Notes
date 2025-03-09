- In an undirected graph, if vertex v is a neighbour of vertex w, it is assumed that vertex w is a neighbour of v.
	- 2 vertices can be considered adjacent if neighbours

- The degree of a vertex -> The number of neighbours

#### Adjacency Lists:
- On undirected graphs, both directions need to be listed in adjacency lists
- The total space is V + E
- Especially suited to sparce graphs where E is less then V^2
- Ordering in numerical order is preferred, but not necessary.
	- Changing the order of numbers doesnt affect the graph as they use sets of vertexes and edges (sets dont care for order)
		- Algorithms working on these lists however, will be affected
##### Digraphs (Directional Graphs) and adjacency lists:
- Shows only the out-neighbours (not the in-neighbours)
- Do numerically descending order for this (for some reason)


#### Adjacency Matrix Representation:
##### Undirected Graphs:
- Matrix is symmetric
- V^2 space is requred
- More suited to dense graphs (lots of 0s is a waste of space)
	- where E is closer to V^2
- Vertices must be named from 1 ... |V|
##### Digraphs (Directional Graphs) and adjacency matrices:
- Rows will represent out-neighbours
	- The number of 1s in a row is the out-degree of a vertex
- Columns represent in-neighbours
	- The number of 1s in a column is the in-degree of a vertex

#### Note:
0 -> Not a graph (not a pair)
(0,0) -> Not a graph (not a pair of sets)
({}.{}) -> Yes
({1,2},{2}) -> Not a graph (the 2nd set for edges must contain edges)
({1,2},{1,2}) -> Not a graph (2nd set must contain edges, defined as such {x,y})
({1,2}, {{1,2}}) -> A graph :D  
({1,2},∅) -> YES! (∅ implies an empty set)
#### WHICH REPRESENTATION SHOULD I USE?
- This depends on the questions you need to answer with your representation
	- Are vertex V and W adjacent? -> MATRIX!
	- What is the out-degree of v? -> LIST!
	- What is the in-degree of v? -> MATRIX!

