#### Recap:
- Purpose of AI
	- Find solutions to a diverse set of questions
- Use a representation of knowledge:
	- Global knowledge
	- Local knowledge
- Act on knowledge, Perception and goals
	- Various types of agents with different sets of capabilities

#### Designing rational agents -> PEAS:
- We must specify the task environment
- We need to deterine:
	- P -> Performance measure
	- E -> Environment(s)
	- A -> Actuators
	- S -> Sensors

#### Problem Solving Agents
- Restricted form of a general agent.
- A basic form of a problem solving agent:
- Goal & problem -> Search for solution by sequence of actions

#### E.G: Romania
![[Pasted image 20250429123113.png]]
#### SEARCHING FOR THE BEST ROUTE:
- What do we mean by the best? 
	- Distance
	- Time
	- Lowest petrol consumption
	- Combination?
- Can we always find the best solution?
	- Lmao no
	- We look for satisfactory solutions instead
		- Specify a set of goals which we deem as satisfactory

#### Let's encode the problem as a Graph Search!
- Directed graphs:
	- Properties of directed graphs:
		- Acyclic (forward / backward)
		- Branching factor
- Search Problem:
	- Is there a path from the initial node to a goal node? 

#### Searching in Graphs: 
``` PseudocodeFuckIDK
procedure Search(G,S,goal)
	inputs:
		G -> graph with ondes N and arcs A
		s -> start node
		goal -> Boolean function of nodes

	output: 
		path from s to a node for which goal is true
		or (upside down T) if no solution paths

	local:
		frontier: set of paths
		frontier := {<s>}
		while frontier != {} do@
			select and remove <n0, ..., nk> from frontier
			if goal(nk) then:
				return <n0, ..., nk>
			frontier := frontier U {<n0, ..., nk, n} : <nk, n> (element of A)
	return (upside down T)
```

### Example: Romania: 
- Situation 
	- On holiday in Romania, currently in ARAD. Flight leaves tomorrow from Bucharest.
- Formulate goal:
	- Be in bucharest
- Formulate problem:
	- States -> Various cities
	- Actions -> Drive between cities
- Find solution:
	  Sequence of states 

#### Problem Types: 
- Deterministic, Fully Observable -> Single State Problem
	- Agent knows exactly which state it will be in
	- Solution is a sequence

- Non-Observable -> Conformant Problem
	- Agent may have no idea where it is
	- Solution (if any) is a sequence

- Non-deterministic and / or partially observable -> Contingency problem
	- Percepts provide new information about current state
	- Solution is a contingent plan or policy
	- Often interleave search & execution

- Unknown state space -> exploration problem
	- "online"

#### Single-state problem formulation
- A single state problem is defined by 4 items:
	- Initial state 
	- Successor function
		- S(x) = set of action-state pairs.
		- S(Arad) = {(drive,Zerind), (drive, Sibiu), ...}
	- Goal test:
		- can be:
			- Explicit x = "at bucharest"
			- Implicit NoDirt(x)
	- Path cost (additive):
		- Sum of distances, number of actions executed etc 

#### Selecting a State Space
- Real world is absurdly complex
	- We must make a state space abstracted for problem solving
- (Abstract) state <-> set of real states
- (Abstract) action <-> complex combination of real actions
	- E.G: "Arad -> Zerind" represents a bunch of routes, rest stops etc.
- For guaranteed realisability, any real state "in arad" must be able to get to some real state "in Zerind"
- (Abstract) solution <-> set of real paths that are solutions in the real world
- Each abstract action should be "easier" than the original problem

#### Vacuum world: A cleaning robot
- States: 8 possible states
- Actions:
	- Arc inscriptions
	- plus NoOp (no operation)
- Goal test:
	- no dirt
- Path cost:
	- 1 unit per action
	- 0 units for NoOp
![[Pasted image 20250429125010.png]]

#### Example: The 8-Puzzle
- States:
	- Locations of tiles
- Actions:
	- Move blank left, right, up or down
- Goal test:
	- Check if current state is goal state
- Path cost:
	- 1 unit per move


#### Example: Robotic Assembly:
- States:
	- Real-valued coordinates of robot joint angles
	- Coordinates of Parts of the object to be assembled
- Actions:
	- Continuous motions of robo joints
- Goal Test:
	  Complete assembly with no robot included
- Path cost:
	- time to execute

#### Tree-search algorithms
- Basic Idea:
	- Offline
	- Simulated exploration of state space by generating successors of already explored states
		- AKA expanding states
``` SkibidiCode
function TREE-SEARCH(problem)
	returns: a solution or failure

	initialise the frontier using the initial state of problem
	loop do:
		if frontier empty, return failure
		choose leaf node and remove from frontier
		if node contains goal state return solution
		expand chosen node, adding resulting nodes to frontier
```
#### Implementation: States VS Nodes:
- A state is a (representation of) a physical configuration
- A node is a data structure contituting part of a search tree
- States do not have children, parents, depth or path cost.
- The EXPAND function creates new nodes, filling in the various fields and using SuccessorFn of the problem to create the corresponding states.
