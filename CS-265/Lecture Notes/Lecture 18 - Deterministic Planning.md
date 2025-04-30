#### State-space Search & Classical Planning
- Deterministic or Stoachastic dynamics
- Fully observable or partially observable
- Explicit states or features or individuals and relations
- Static or finite stae or indefinite stage or infinite stage
- Goals or complex preferences
- Perfect rationality or bounded rationality
- Flat or modular or hierarchical
- Single agent or multiple agents
- Knowledge is given or knowledge is learned
- Reason offline or reason while interacting with environment

#### Planning:
- Planning is deciding what to do based on:
	- An agent's availability
	- It's goals
	- The state of the world
- Initial assumptions:
	- The world is deterministic
	- The agent knows what state it is in (fully observable)
	- Time progresses dicretely from one state to the next
	- Goals are predicates of states that need to be achieved.
- Planning is finding a sequence of actions from an initial state to a goal

#### Actions:
- A deterministic action is a partial function from states to states
- The preconditions of an action specify when the action can be carried out
- The effect of an action specifies the resulting state

#### Robot Example:
![[Pasted image 20250430135128.png]]
- Features: 
- Rloc -> Rob's location
- RHC -> Rob has coffee
- SWC -> Sam wants coffee
- MW -> Mail is waiting
- RHM -> Rob has mail

- Actions:
- mc -> move clockwise
- mcc -> move counterclockwise
- puc -> pick up coffee
- dc -> deliver coffee
- pum -> pick up mail
- dm -> deliver mail

#### Explicit State-space representation
![[Pasted image 20250430135310.png]]
- What happens if we wanna model the battery charge of the robot too?
	- Every single fucken state needs to represent this additional info.
Theres also redundancy in this representation.

#### STRIPS representation: 
- The state is a function from features into values. 
	- Therefore, it can be represented as a set of feature value pairs.

- For each action:
	- Precondition - a set of feature-value pairs that must be true in order for the action to be carried out
	- Effect - a set of feature-value pairs that are made true by this action.

- STRIPS assumption:
	- Every feature not mentioned in the effect is unaffected by the action.
	- In other words, a STRIPS action just represents what changes. 
	- In other words, this represents inertia.

What are the initial assumptions about the features? 

#### Example STRIPS Representation:
Pick up coffee (puc):
- Precondition {Rloc = cs, RHC = False}
	- The robot location must be coffee shop
	- Robot must not be holding coffee
- Effect {RHC = True}.
	- The robot will be holding coffee once it picks up coffee.
	- Nothing else changes (still at coffee shop)

#### Deterministic Planning:
- Given:
	- A description of preconditions and effects of actions
	- A description of the initial state
	- A goal to achieve
- Find a sequence of actions that is possible and will result in a state satisfying the goal.

#### Forward Planning:
- Idea: Search the state-space graph.
	- The nodes represent the states
	- There is an arc <s, s'> labelled with action A if:
		- A is an action that can be carried out in state s and
		- s' is the state resulting from doing A in state s.
	- A plan is a path from the state representing the initial state to a state that satisfies the goal.

#### Example: State-space graph: 
![[Pasted image 20250430140706.png]]

#### Forward Planning Representation:
- The search graph can be constructed on demand.
	- You only construct reachable states
- If you want a cycle check or multiple path pruning, you need to be able to find repeated states
- There are a number of ways to represent states:
	- As a map from features into their values
	- As a path from the start state

#### Improving Search Efficiency:
- Forward search can use domain-specific knowledge specified as:
	- A heuristic function that estimates the cost from a complete state-description to a goal.
	- Domain specific pruning of neighbours;
		- Don't pick up coffee unless sam wants coffee
		- Unless the goal involves time constraints, dont do a "no move" action
		- Dont go to the coffee shop unless "Sam wants coffee" is part of the goal and Rob doesnt have coffee (maybe not)
