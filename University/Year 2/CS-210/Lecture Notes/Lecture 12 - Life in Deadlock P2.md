#### RECAP: Dining Philosophers Problem Modelled:
``` LTSA
Fork = (acquire -> release -> Fork).  
Philosopher = (sit -> right.acquire -> left.acquire  
-> eat -> left.release -> right.release -> stand ->  
Philosopher).  
||ThreePhil = ({a,b,c}:Philosopher).  
||Fork1 = ({a.right, b.left}::Fork).  
||Fork2 = ({b.right, c.left}::Fork).  
||Fork3 = ({c.right, a.left}::Fork).  
||Table = (ThreePhil || Fork1 || Fork2 || Fork3).
```

#### Code for the Dining Philosophers Problem:
![[Pasted image 20250309145025.png]]
![[Pasted image 20250309145119.png]]
And the running method: 
![[Pasted image 20250309145105.png]]
And finally the main method: 
![[Pasted image 20250309145339.png]]

#### Deadlock Handling: Who is responsible?
- Two groups of devs who should give a shit:
	- OS Developers
	- Application Developers
- Approaches for handling deadlocks:
	- Ignorance is bliss :LiSmile:
	- Prevention - Primarily app dev
	- Avoidance - Primarily OS dev
	- Detection and Recovery - Primarily OS dev
- Many current operating systems cant prevent deadlocks. Different operating systems adopt different strategies to handle potential deadlocks.

#### Deadlock Prevention - Design
How to avoid the 4 requirements for deadlock
- Mutual Exclusion
	- Difficult to eliminate completely, when there are shared resources.
	- We may allow some processes to be non-exclusive (like reading files) but some (file write) need to be exclusive by design.
- Hold-and-wait
	- Request all resources at the beginning, and block processes until requests can be granted. Must know all required resources in advance - which is difficult
- No Pre-emption
	- Design processes such that it lets go of any resources it holds if a request for another resource is denied. 
	- Times waiting on resources
	- Force a required resource to be released by processes (difficult due to priority)
		- Important to consider rollback
- Circular Wait
	- Impose strict ordering between resources for acquisition

#### How can we break the wait-for-cycle of the dining philosophers problem?
- If the even numbered Philosopher takes the right fork while the odd-numbered one takes the left, the cycle is broken.

#### Another semaphore based solution to a dining philosophers:
- Allow only N-1 philosopher to sit down at a time
FSP model:
``` LTSA
const N = 3
set Names = {a,b,c}
Butler(Capacity=N-1) = ChairFull[0]
ChairFull[i:0..Capacity] = (when i<Capacity 
Names.sit -> ChairFull[i+1] | when i>0 Names.sand
-> ChairFull[i-1]).
||ButleredTable = (Butler || Table).
```

#### The butler can be efficiently implemented as a semaphore
![[Pasted image 20250309150312.png]]
- Note that the main application class also has to be adjusted

#### Other Solutions:
- Pick the lower-order fork first.
- Used timed waiting on a fork
- Etc

#### Summary:
- The goal is to always design a deadlock-free system
- Breaking deadlocks require just breaking one condition
- We can introduce constraints or processes to ensure we break deadlocks