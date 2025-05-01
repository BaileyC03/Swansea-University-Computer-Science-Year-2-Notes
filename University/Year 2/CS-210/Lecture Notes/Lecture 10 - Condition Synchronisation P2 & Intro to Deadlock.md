> Note: Check the panopto videos on these as apparently there is more info

// Do Slides 1-14 Before this
#### Semaphores
- A semaphore is one of the first concepts proposed to deal with interprocess synchronication
- It's essentially just a variable
![[Pasted image 20250225090720.png]]
![[Pasted image 20250225091509.png]]
^ Code example
- While this reduces the things you need to synchronise, you do still need to synchronise some things.
- Synchronise only the things you need to synchronise

#### Deadlock
- Any situation in which no member in a group of entities can proceed because each member is waiting on another member (including itself) to do something. Commonly, releasing a lock is that "something"

#### Necessary and Sufficient Conditions:
A Deadlock state exists when all four conditions occur:
- **Mutual exclusion**
	- Processes involved shared resources that they use under mutual exclusion
- **Incremental acquisition**
	- Processes hold in resources already allocated to them while waiting to acquire additional resources
- **No preemption**
	- Once acquired by a process, resources can't be preempted (forcibly withdrawn), but are only released voluntarily
- **Wait-for-cycle**
	- a circular chain (or cycle) of processes holds a resource that its successor in the cycle is waiting to acquire
While a deadlock state exists, you may not necessarily enter the deadlock state as it is non deterministic.


