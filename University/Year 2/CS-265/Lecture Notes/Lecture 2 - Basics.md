#### WHY NOT ONLY STUDY ML?
- some problems dont require ML
- Require a sound explanation of the result
- Can be solved more efficiently without ML

#### AGENTS:
- Something (entity) that acts within an environment
- Consists of a body and a controller
	- Interacts within the environment with a body
	- Controller receives percepts from the body and sends commands to the body
- Body includes:
	- Sensors that convert stimuli into percepts
	- Actuators (effectors), converts commands into actions into environment
- Embodied agents have physical bodies
- Robot is an artificial purposive embodied agent, sometimes agents that only act in a digital space can also be considered bots or robots

#### RATIONAL AGENTS:
- Entity which:
	- Percieves environment 
	- Acts according to some rules
	- To achieve its goals
- Caveat - Computational limitations make perfect rationality unachieveable.
	- Design best program for given machine resources

#### AGENTS AND ENVIRONMENTS
- Include humans, robots, softbots, thermostats etc
- Agent function maps from percept histories to actions
	- f: P* -> A
- Agent program runs on the physical architecture to produce f.

#### EXAMPLE: AUTONOMOUS DELIVERY AND HELP ROBOT
- Has wheels, ability to pick up / put down and manipulate objects.
- Sensing capabilities let it recognise objects and avoid obstacles
- "Listens" to orders in natural laguage and obeys them, making reasonable choices about what to do with conflicting goals
- Capabilities: Deliver packages / coffee in office, clean a home / put things in appropriate place, help caregivers in hospital.

#### EXAMPLE: SIMPLE CLEANING ROBOT:
- Percepts: Location, state of location (A1, Dirty)
- Actions: MoveLeft, MoveRight, Vacuum, DoNothing

#### RATIONALITY:
- Rational agent chooses whichever action maximises the expected value of a given performance measurement given the percept sequence to date.
	- Rational != Omniscient
		- Percept may not supply all relevant information
	- Rational != Clairvoyant
		- Action outcomes may not be as expected
	- **Therefore, rational != successful**

#### AGENTS AND MULTI AGENT SYSTEMS:
- Agents:
	- Have goals
	- Percieve environment
	- Act according to rules
	- Communicate
	- Form coalitions
	- Negotiate
	- Require resources
	- Compete for resources
	- (Maybe) learn

#### RATIONALITY HAS MANY FACETS:
- Definition could require:
	- Information gathering / exploration
	- Learning from percepts
	- Agent autonomy

#### DESIGNING RATIONAL AGENTS: PEAS
- In order to design a rational agent we must specify the task environment
- Consider the task of designing an automatic taxi:
	- What is the measure of performance
	- What environments
	- What actuators
	- What sensors
- P - Performance Measure
	- Profits? Safety? Legality? Comfort?
- E - Environment(s)
	- Streets, Traffic, Pedestrians, Weather
- A - Actuators
	- Steering, Accelerator, Brake, Horn, Speaker, HUD
- S - Sensors
	- Video, Accelerometer, Gauges, Engine Sensors, GPS

#### TYPES OF ENVIRONMENT:
- Is it:
	- Observable
	- Deterministic
		- Will the result always be the same depending on input
	- Episodic
	- Static
	- Discrete
	- Single-agent?

#### RATIONALITY AND ITS LIMITS:
- Computational limits determine if an agent has:
	- Perfect rationality - Agent reasons about best action without taking into consideration computational resources
	- Bounded rationality - Agent decides on best action it can find given limitations.

#### PROGRAMMING AGENTS:
- Agent types
	- Simple Reflex Agents
	- Reflex Agents with State
	- Goal-based agents
	- Utility based agents
- All of which can be turned into learning agents

#### SIMPLE REFLEX AGENTS:
- Select action on the basis of only the current percept
- Large reduction on possible percept/action situations
- Implemented through condition-action rules
	- If dirty, then vacuum
#### REFLEX AGENTS WITH STATE
- Tackles partially observable environments
	- Maintain the internal state
- Over time, updates state using world knowledge
	- How does the world change
	- How do actions affect world

#### GOAL-BASED AGENTS
- Agent needs a goal to know which situations are desirable
	- Things become difficult when long sequences of actions are needed in order to achieve a goal
- Typically investigated in search and planning research
- Major difference: The future is taken into account
- Is more flexible as knowledge is represented explicitly and can thus be manipulated

#### BDI - BELIEF, DESIRES, INTENTIONS:
- Beliefs 
	- represent information the agent has about its environment
- Plans
	-  Coded by developer offline, in advance
	- Give the agent info about:
		- How to respond to events
		- How to achieve goals
	- Plan structure:
		- Event
		- Context
		- Body

#### DYNAMICS AND BDI AGENTS
- Agents operate a reasoning cycle involving:
	- Perception
	- Goal selection
	- Rule selection
	- Execution
- Each action has the following flags:
	- Active
	- Suspended
	- Aborted

![[Pasted image 20250128132317.png]]

#### UTILITY-BASED AGENTS
- Certain goals can be reached in different ways
	- Some are better (have higher utility)
- Utility function maps 1+ states to a real number
- Improves on goals
	- Selecting between conflicting goals
	- Select appropriately between many goals based on likelihood of success

#### LEARNING AGENTS:
- Learning agents explain the origins of other agent programs
- You teach them instead of instructing them
- Advantage is the robustness of the program towards initially unknown environments
- Learning element - introduce improvements in performance element
	- Critic provides feedback on agents performance based on fixed performance standard
- Performance element - selecting actions based on percepts
	- Corresponds to previous agent programs
- Problem generator - suggests actions that will lead to new and informative experiences
	- Explorations vs exploitation

