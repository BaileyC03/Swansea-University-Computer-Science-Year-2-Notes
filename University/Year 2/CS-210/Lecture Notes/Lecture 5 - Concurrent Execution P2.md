#### Process Scheduling (Interleaving) Simulation
- Single process running on one processor
	- No problems, runs as you would expect.
- Multiple Processes running in parallel
	- Must consider how to use the processors.
	- There are various algorithms (like first come first serve)
	- Scheduling Criteria:
		- CPU Utilisation
			- Is the CPU busy at least most of the time
		- Throughput:
			- What is the number of processes completed per unit of time?
		- Turnaround time:
			- How much time does a particular process take to complete?
		- Waiting time:
			- How long does a process wait for its turn?
		- Response time:
			- How long does it take to handle interactions

#### Modelling Concurrency:
- How should we model process execution speed?
	- Arbitrarily. We abstract away time and want to model independently of the number of processes or scheduling strategy
- How do we model concurrency?
	- An arbitrary relative order of actions from different processes' interleaving but preservation of each process order.
- What is the result:
	- General model independent of scheduling. Asynchronous model of execution

#### Parallel Composition
- If P and Q are processes, (P || Q) represents the concurrent execution of P and Q. "||" is the parallel composition operator
- This operator is commutative and associative
	- Commutative
		- (P || Q) = (Q || P)
	- Associative
		- ((P || Q) || R) = (P || (Q || R )) = (P || Q || R

#### Instances:
- a:P creates an instance of the process P and prefixes each action label in the alphabet of P with an a.
- E.G: An Array of Switches:
		SWITCH1 = (on -> off -> SWITCH1)
		|| SWITCH1(N=3) = forall[i:1..N] s\[i]:SWITCH1

#### Sharing Between Processes:
- Simple rules for understanding the nature of sharing:
	- Action:
		- Common behaviour between processes
			- What the process does
			- You cannot perform a common action until all pre-requisite actions by all sharers have been performed.
	- Resources:
		- Common property between processes
			- Has a / Uses a / Controls a type relationship
			- E.G: Multiple users in a household share a toaster

#### Summary:
- We use (P || Q) for the parallel composition of processes P and Q.
- We can model shared actions

