Graphs come in many forms, notably:
- Trees
- Forests

#### Components of a Graph:
G = (V,E)
- V - Vertices
- E - Edges
	- An edge is denoted {u,v}
	- u is one vertex, v is another. it's noting the vertices it links
	- u /= v in this case as loops are not allowed

E.G: G = {{1,2,3,4,5}, {{1,2},{1.3},{2,4},{3,4}}}
- The first {1,2,3,4,5} implies there are 5 vertices, labelled 1,2,3,4 and 5
- The second {} of {{1,2},{1,3},{2,4},{3,4}} implies there is a link between 1-2 , 1-3, 2-4 and 3-4.
This graph can be denoted as such:
![[Pasted image 20241009123439.png]]
Note: This is one graph
- In order for a node to be considered connected, ALL nodes must be able to (directly or indirectly) access all other nodes.
- In the example above, this graph is disconnected as 5 cannot access 1 (or any other node tbh)
- If a graph is disconnected, however, it has 2+ connected components
	- 1-2-3-4 is connected, for example
- Components are a subset of graphs


#### Directed Graphs:
Like normal graphs, however their direction is shown and they are typed slightly differently.
G = {{1,2,3,4,5}, {(1,2),(3,1),(2,4),(4,3)}} <- Note the () not {} on this one.
- (a,b) means the edge is pointing to b from a
![[Pasted image 20241009123830.png]]
- If you want to have an arrow point in both directions, like an undirected graph edge technically would, you have to do a (a,b) and (b,a)

#### Max number of edges a graph can have:
(n(n-1))/2 <- This is the formula for the amount of edges in a complete UNDIRECTED graph.
(n(n-1)) <- This is the fomula for the amount of edges in a complete DIRECTED graph
- A complete graph is a graph in which no more edges can be added

#### How do we represent graphs?
##### Adjacency Lists:
 - Associates vertex with a collection of its neighbouring vertices / edges
 - E.G: 
		 - 1: 2
		 - 2: 4
		 - 3: 1
		 - 4: 3
		 - 5: 

* note: for undirected graphs, youll have to treat it as a directed graph where arrows point in both directions and will need to have 3:1 and 1:3.

##### Adjacency Matrix:
- A giant matrix of order v x v where v is the number of vertices is used to represent a graph. 
- E.G: 
- X 1 2 3 4 5
- 1 X O X O O
- 2 O X O O O
- 3 X O X O O
- 4 O O O O X


