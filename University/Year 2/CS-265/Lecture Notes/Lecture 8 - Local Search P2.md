#### n-Queens:
- Place n queens on an nxn board with no two queens on the same row, column or diagonal.
- Move a queen to reduce the number of conflicts
- Almost always solves n-queens problems almost simultaneously for very large n (e.g n = 1,000,000)

#### Hill-climbing Search [AKA GREEDY]
- "Is a loop that continuously moves in the direction of the increasing value"
	- Terminates when the peak is reached
 - Hill climbing does not look ahead of the immediate neighbours of the current state (only looks at immediate)
 - Hill-climbing chooses randomly among the set of best successors, if there is more than one
 - AKA GREEDY SEARCH

#### Example of hill climbing:
- 8 Queens problem (complete-state formulation).
- Successor Function:
	- Move a single queen to another square in the same column
- Heuristic function h(n)
	- The number of pairs of queens that are attacking eachother (directly or indirectly)

#### Drawbacks of hill climbing algorithms
- Ridges 
	- (Sequence of local maximums difficult for greedy algorithms to navigate)
	- Counterplay: Random restart hill climbing
- Plateau
	- Area of the state space in which the evaluation function is flat
	- Counterplay: Random sideway moves

#### Hill-climbing variations
- Stochastic hill climbing
	- Random selection among the uphill moves
	- The selection probability can vary with the steepness of the uphill move

- First-choice hill climbing
	- Variant of stochastic hill climbing that generates successors randomly until a better one is found

- Random-restart hill climbing
	- Tries to avoid getting stuck in local maxima

#### Simulated annealing
- Escape local maxima by allowing "bad" moves.
	- Idea:
		- But gradually decrease their size and frequency
- Bouncing ball analogy
	- Shaking hard (= high temperature)
	- Shaking less (= lower temperature)
- If temp decreases enough slowly, the best state is reached.
- Applied for VLSI layours, graph drawing, airline scheduling etc....

#### n-Queens solved by Simulated Annealing
- Local Beam Search:
	- Idea:
		- Keep k states instead of 1
		- Choose top K of all their successors
			- Not the same as K searches run in parallel
		- Searches that find good states recruit other searches to join them.
	- Problem:
		- Quite often, all k states end up on the same local hill
		- Lack of diversity

#### Genetic Algorithms:
- Variant of local beam search with recombination
- Typically applied to discrete optimisation
- Attributed features:
	- Not too fast
	- Good heuristic for combinatorial problems
- Special features
	- Traditionally emphasises combining information from good parents (crossover)
- Many variants :o 

#### Generic Algorithm Reproduction Cycle
1. Select parents for the mating pool
	1. Size of pool = population size
2. Shuffle the mating pool
3. For each consecutive pair, apply crossover with probability Pc, otherwise copy parents
4. For each offspring, apply mutation (bit flip with probability Pm independently for each bit)
5. Replace the whole population with the resulting offspring

#### GA Operators: 1 Point Crossover
- Choose a random point on the two parents
- Split parents at this crossover point
- Create children by exchanging tails (latter section of binary list)
- Pc typically in range (0.6-0.9)
![[Pasted image 20250305154514.png]]

#### GA Operators: Mutation
- Alter each gene independently with a probability Pm
- Pm is known as the **mutation rate**
- typically between 1/pop_size and 1/chromosome_length

#### GA Operators: Selection
- Main idea:
	- Better individuals get a higher chance
	- Chances proportional to fitness
	- Implementation: Roulette wheel technique
		- Assign each individual a part of the roulette wheel
		- Spin the wheel n times to select n individuals

#### Genetic Algorithms: Visualised:
- Digit sequences representing the 8-queens states
- Initial population in (a) is ranked by the fitness function (b)
- This results in the pairs for mating (c) which produces the offspring(d) which are subject to mutation(e)
![[Pasted image 20250305155032.png]]

#### Genetic Algorithms - Pros and Cons:
- Pros:
	- Faster & lower memory requirements than searching very large search space
	- Easy
		- If your candidate representation and fitness function are correct, a solution can be found without explicit analysis

- Cons:
	- Randomised - not optimal or complete
	- Can ger stuck on local maxima (crossover can help mitigate this)
	- It can be hard to work out how best to represent a candidate as a bit string

#### Summary & Examples: 
- Search and Optimisation:
	- assume a state with many variables
	- Assume some function you want to maximise / minimise the value of
		- E.G a utility or happiness function
	- Searching entire space is too complex
		- Cant evaluate every possible combination of variables
		- Function might be too difficult to evaluate analytically

#### [GREEDY] Hill Climbing - Finding a maximum:
- Random starting point
- Repeat:
	- From current state, generate n random steps in random directions
	- Choose one that gives best new value
	- Continue this while a better state is found.
		- Exit the repetition if none of the n steps were better

#### Gradient-descent or Gradient-ascent
- Simple modification to Hill-climbing 
	- Generally assumes a continuous state space
- Idea is to take more intelligent steps:
- Look at local gradient
	- Take the direction of the largest change
	- Take a step in that direction
		- Step size should be proportional to gradient
	- Tends to yield a faster convergence to the maximum

#### Logical Agents:
##### Knowledge:
- Humans know things
- Human knowledge is dynamic
- Humans make decisions inferred from their knowledge
- So far, our agents have had some implicit knowledge
	- The 8 puzzle agent does not know that 2 tiles cannot occupy the same space
	- A pathfinding agent does not know that roads cannot have negative distances
- Logical agents have a knowledge base and an inference mechanism
