#### ABSTRACTION:
- The process of removing details n the study of systems to focus attention to details of greater importance
- This helps to reason about complex systems
#### GENERALISATION:
- Concept A is a generalisation of concept B if and only if every instance of B is also an instance of A
- There may be instances of A that are not B
- Think like A being a superclass of B. (as a comparison)

#### MODELS:
- A model is an abstract and simplified representation of the real world
	- "All models are wrong, but some are useful"
- We use models to gain confidence n the adequacy and validity of a proposed design thorough:
	- Focus on abstraction of concurrency
	- Model animation to visualise behaviour
	- Automated model verification of properties(Safety and progress)
--
#### COMPLEX SYSTEM:
- Composed of smaller activities, each represented as a sequential processes. A process is the execution of a sequential program.
	- Process has a state, defined by variables 
	- A process executes actions to transform its state
- In a class, the attributes make up the state and methods change the state. 

#### TOOLS USED:
- A process is modelled as a state machine and the tools we use are:
- LTS - Labelled Transition System - Graphical Form:
	- Analyse, display and animate
- FSP - Finite State Process - Algebraic Form:
	- Textually describe a model
(We can explore interactions between states using the LTSA tool. Labelled transition analyser tool)

####  DESIGN AND IMPLEMENTATION WORKFLOW:
- 1. Deconstruct
	- Conceptualise the scenario as 1+ processes with attributes (for capturing state) and a sequence of actions (or methods)
- 2. Model:
	- 1. Translate deconstruction to Process Alphabets
	- Describe Finite State Machines using FSP
	- Generate LTS and analyse with LTSA tool
- 3. Implement:
	- Program with Java threads

#### EXAMPLE: A SWITCH
- toggle down, switch is on
- toggle up, switch is off
(This is a sequential system, but if you have 2 switches in a room it can become concurrent)

#### STEP 1: DECONSTRUCT
- Actions: Look for verbs
	- Up
	- Down
- State representation: look for unique states
	- On
	- Off

#### STEP 2: MODEL AND PROCESS ALGEBRA
- BASIC SYNTAC RULES:
	- Uppercase (name of a process, subprocess or state starts with uppercase)
	- Lowercase (name of action)
	- Right arrow (if x is action and p is process, x -> P is a process that takes action x to become process P)
	- Comments (start with //)
	- Period (process definitions end with a .)
	- Comma (splits multiple definitions, used to define processed)

#### EXAMPLE: JOB PROCESS
3 Actions: Arrive, Work, Leave
- FSP:
	- JOB = (arrive -> work -> leave -> JOB)