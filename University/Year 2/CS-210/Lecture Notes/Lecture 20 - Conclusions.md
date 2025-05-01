#### Outline:
- Overview of the covered topics
- Unit testing for concurrent programs
- Assessment Information

#### What was this module about? 
- Understanding concurrency and developing concurrent programs.

- Deconstruct (Requirement analysis)
	- Actors, properties and actions of interest
- Model
	- Actions?
	- Active and Passive Processes?
	- Variables? 
	- Logic and FSP syntax? 
	- Analyse scenarios and identify problems.
- Implement in Java
	- Identify and apply appropriate tools.

#### Covered Topics:
- Lecture 1:
	- Definitions of concurrency
	- Real world examples
	- Benefits
	- Issues and implications

- Lectures 2/3/4.1
	- Abstractions, Generalisation and Models
	- Design & Implementation workflow
	- Modelling Processes in FSP:
		- Process declaration
		- Choices
		- Indexed processes and actions
		- Guarded actions
	- Threads in Java
		- Implementation techniques
			- Thread
			- Runnable
		- Thread Lifecycle

- Lectures 4.2 / 5 / 6.1
	- Execution of a concurrent process
	- Process scheduling simulations
	- FSP:
		- Parallel composition
		- Process instances & labelling
		- Action relabelling & hiding
		- Sharing between processes
			- Actions & Resources
		- Action synchronisation

- Lectures 6.2 / 7 / 8
	- Ornamental garden
		- Naive model & Code
	- Testing for interference.
	- Fixed model and code
	- Synchronized keyword and modelling locks.
	- Atomic actions and variables

- Lectures 9 / 10
	- Active and Passive Processes
	- Conditional access to shared resources
		- Car park model / code
	- Wait-notify-notifyAll in Java
	- Semaphore
		- Allowing multiple access

- Lectures 11/12/13.1
	- Dining Philosophers Problem
	- Coffman conditions
	- Deadlock Handling
		- Ignorance (do nothin)
		- Prevention
		- Avoidance
		- Detection and Recovery
	- Dynamic detection & recovery
	- Resource Allocations Graphs

- Lectures 13.2 / 14.1
	- Original and optimised execution time
	- Derivation of gain
		- Proportion between original and optimised
		- Applications in decision-making

- Lectures 14.2 / 15 / 16/ 17
	- Safety
		- Deadlock Free
		- Mutual Exlusion
	- Liveness
		- Progress
		- Fairness
		- Result
	- Single lane bridge:
		- Model & Code

- Lectures 18 / 19
	- Data parallelism (instead of task parallelism)
	- Properties of database transactions
	- Workflow for STM
	- Limitations
	- Java Multiverse library
	- Examples:
		- Bank account
		- Binary Array Swapper

#### UNIT TESTING! 
- An issue with testing concurrent programs is that most programs are non-deterministic and precise interleaving is unknown to the programmer.
- The more threads, the more possibilities exponentially.
- How do we tackle this?
	- Weed out concurrent issues by design
	- Isolate concurrent parts as much as you can and test non-concurrent parts
	- Use concurrent testing tools

And that, ladies and gentlemen is concurrency.

#### ASSESSED TOPICS:
▶ Introduction ✓
▶ Processes and Threads ✓  
▶ Concurrent Execution ✓  
▶ Interference ✓  
▶ Condition Synchronisation ✓  
▶ Deadlock ✓  
▶ Amdahl’s Law ✓  
▶ Properties ✓  
▶ Software Transactional Memory ✓