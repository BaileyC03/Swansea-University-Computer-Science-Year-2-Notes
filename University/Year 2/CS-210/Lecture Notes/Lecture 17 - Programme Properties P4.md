#### Recap:
- Washing Machine
	- Example of safety property
- Tossing Coins
	- Progress Properties

#### Learning Outcomes: 
- To apply modelling techniques to identify progress issues.
- To device appropriate ways to eliminate progress issues.
- To start to identify the different between task and data parallelism

#### Outline: 
- Terminal sets & progress priority
	- Revising the tossing coin example
	- Revising the two-coin example
- Liveness
	- Fixing single-lane bridge
- Intro to data parallelism

#### Progress: Tossing a Coin:
- A fair coin
![[Pasted image 20250428123828.png]]
- An unfair coin
![[Pasted image 20250428123911.png]]
On tossing an unfair coin:
![[Pasted image 20250428123939.png]]

#### Graph Theory: Strong Connections
- Strong Connections
	- Two nodes m and n are said to be strongly connected if, and only if, there is a path from m to n and vice versa
- Strongly connected set
	- A set of nodes in a graph is said to be a strongly connected set if, and only if, every pair of nodes in the set is strongly connected
![[Pasted image 20250428124223.png]]
(the strongly connected parts are in the boxes) 

#### Terminal Sets
- A terminal set is a strongly connected set from whih there are no links out of the set.
- We can use this as an example:
![[Pasted image 20250428124724.png]]
There are three strongly connected sets here:
- {Q0}: A single node with links out of it -> Not terminal
- {Q1, Q2}: No links out -> Terminal
- {Q3, Q4, Q5}: No links out -> Terminal
- 
The central concept for checking progress violation:
- Identify terminal sets and check if at least one action from the progress set appears in these sets
From this we can denote that the TwoCoin process is clearly unfair to the tails action.

#### Revisiting the FairCoin - is it really fair? 
![[Pasted image 20250428125135.png]]
- No progress violation but what's really happenin? 

#### Priorities in a Process: 
Let's investigate what happens if we add priority to a certain action (and the priority action is picked all the time)
- High priority in process P:
	- Actions {a1, ..., an} are preferred over others in a choice caee
		P << {a1, ..., an}
- Low priority in process P:
	- In a choice case, prefer other actions over {b1, ... bn}
		P >> {b1, ..., bn}
We use this to uncover potential progress problems by selecting traces that may be problematic
``` FSA - New Fair Coin
FairCoin = (tossA -> heads -> FairCoin | tossB -> tails -> FairCoin).

progress Heads = {heads}
progress Tails = {tails}
progress HeadsOrTails = {heads, tails}
```
![[Pasted image 20250428125520.png]]
- To differentiate between the tossing actions we've renamed them tossA and tossB, no logic changes and no progress violations :D

 Let's add some priority!
 ``` FSP
 FairCoin = (tossA -> heads -> FairCoin | tossB -> tails -> FairCoin).

||TestPriority = FairCoin << {tossA} // PRIORITY

progress Heads = {heads}
progress Tails = {tails}
progress HeadsOrTails = {heads, tails}
```
- We've imposed that tossA is chosen over tossB, meaning we will cycle between Q0 and Q2 forever. This violates the heads property!
- If the << was instead a >>, we would prioritise tossB meaning it violates the tails property! 

#### Liveness on the Single Lane Bridge
- in previous lectures, we saw that the lack of fairness in the design of the single-lane bridge was creating liveness problems and was not detected by the LTSA due to the assumption of uniform fairness in the choices. 
Recall - bridge model:
``` FSP
Bridge = Bridge[0][0],  
Bridge[nWest:T][nEast:T] = (  
when (nWest == 0 && nEast<N) east[ID].enter -> Bridge[nWest][nEast + 1]  
| when (nEast>0) east[ID].exit -> Bridge[nWest][nEast-1]  
| when (nEast==0 && nWest<N) west[ID].enter -> Bridge[nWest+1][nEast]  
| when (nWest>0) west[ID].exit -> Bridge[nWest-1][nEast]  
).  
||SingleLane = (Cars || Bridge).  
||CheckSingleLane = (SingleLane || SingleCarOnBridge).
```
![[Pasted image 20250428130057.png]]

#### Modifying this bihh
- To get rid of unnecessary deadlock warnings, we can first modify the car process
	Car = (enter -> exit -> Car) as opposed to enter -> exit -> STOP

- Now we define two of the progress properties that ensure both sides get a go
``` FSP
progress WestCross = {west[ID].enter}
progress EastCross = {east[ID].enter}
|| CongestedBridge = (SingleLane) >> {west[ID].exit, east[ID].exit}.
```
- Both progress properties are violated!!
	- WestCross only has east[ID] actions 
	- EastCross only has west[ID] actions
![[Pasted image 20250428132825.png]]
Due to the priority, once we perform one of east[ID].enter, or west[ID].enter, we get stuck in the respective terminal set.
How can we fix this?
- Politeness, dont enter if a car is on the other side
	- May deadlock if 2 cars are waiting simultaneously
- Strict Ordering: let N cars pass from one side at a time
	- We let one car pass then wait for a car to come on the other side, if no car comes on the other side we're sat there waiting like a mug
The real way to do it is to use strict ordering only if there are cars waiting on the other side!

#### FIXING THE JAVA CODE! :o 
``` java
public class BridgeQueueFixed{
	private Queue<Integer> westQueue;
	private Queue<Integer> eastQueue;
	private int westCount; // West car on bridge
	private int eastCount; // East car on bridge
	private int westWaitCount; // West car waiting
	private int eastWaitCount; // East car waiting
	private boolean isWestTurn; //whos turn is it?

	bridgeQueueFixed(){
		westQueue = new LinkedList<Integer>();
		eastQueue = new LinkedList<Integer>();
		westCount = 0;
		eastCount = 0;
		westWaitCount = 0;
		eastWaitCount = 0;
		isWestTurn = true;
	}
}

	public synchronized void westEnter() throws InterruptedException {
		westWaitCount += 1;
		while (eastCount > 0 || (eastWaitCount > 0 && !isWestTurn)) 
			wait();
		westCount += 1;
		westWaitCount +=1;
		westQueue.add(westCount);
		System.out.println("Added to west queue" + westCount)
		notifyAll()
	}

	public synchronized void westExit(){
		System.out.println("Removed from west queue " + westCount)
		westCount -= 1;
		westQueue.remove()
		isWestTurn = false; // let east use bridge
		notifyAll
	}

}
```

#### Readers-Writers Problem
- The single lane bridge is similar to readers-writers problem

Context: 
- Access and update of the database.
- Several reader and writer processes.
- Simultaneous access where possible
	- Multiple readers, but only one writer.

Challenges:
- Avoid interference and deadlock
- Ensure fairness and progress

*Here we can analyse the system and find a good solution. There are other alternatives, for instance, Software Transactional Memory (STM) which is the next topic*

#### Approaches For Implementing Concurency:
Task Parallelism:
- What we have thought of so far.
- How to organise multiple threads and their communication without breaking concurrent correctness using lock-based (maybe conditional) synchronisation mechanisms

Data Parallelism:
- A different way to think about concurrency.
- Shared data are protected by accessing it in a sequential matter

*Software Transactional Memory is a pattern for simplifying concurrent programming and is an option to achieve data parallelism, inspired by work in databases*

#### SUMMARY:
- Fairness and Progress are important properties through which we can ensure liveness of a system
- It is important to identify these and then design out such subtle issues
	- Priority mechanisms are available in FSP