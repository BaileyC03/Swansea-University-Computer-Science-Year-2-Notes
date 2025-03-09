## Active and Passive Processes:

#### Looking back at the Ornamental Garden Problem:
- Two turnstiles (West, East) allowing people to enter the garden
- The turnstiles run concurrently and share a single counter in which they can increment it 100 times each
	- Ideal way to generate a race condition

- We've identified three processes:
	- West turnstile
		- ACTIVE - People enter through this
	- East turnstile
		- ACTIVE - People enter through this
	- Counter
		- PASSIVE - Incremented as a consequence

#### Active VS Passive: 
- Active process initiates an action
	- Implemented as a Thread in Java
- Passive processes are processes which respond to actions
	- Implemented as a Monitor class in Java


#### Conditional Access to Resources
- Scenario:
	-  Car park with one entrance, one exit, n spaces.
	- Controller only allows a car to enter if there is 1+ spaces left. 
	- Controller only allows a car to leave if there is 1+ cars in the car park
- Actions:
	- Enter
	- Leave
- Active Initiators:
	- Entrance
	- Exit
- Passive Responder:
	- Controller
		- The resource "spaces" will be an attribute of the this class and will be accessed by the Entrance and Exit threads according to the two conditions.

#### Entrance Process - Model and Code:
``` LTSA
Entrance = (enter -> Entrance).
```

Or in Java:
![[Pasted image 20250309141537.png]]
- As an active process, Entrance will be a Thread implementing Runnable
- Why do we prefer runnable?
	- Composition is preferred over inheritance, it allows you to make the active process inherit from another class instead of thread.
And this is how we run it:
![[Pasted image 20250309141658.png]]

#### Exit Process - Model and Code: 
``` LTSA
Exit = (leave -> Exit).
```
And in Java:
![[Pasted image 20250309141747.png]]
And this is how we run it:
![[Pasted image 20250309141817.png]]

#### Controller Model:
- The controller monitor allows access to the spaces based on two conditions:
	- If 1+ space left, allow enter action
	- If there is 1+ cars, allow leave action
``` LTSA
Controller(Capacity=4) = Spaces[Capacity],  
Spaces[spacesLeft:0..Capacity] = (when  
spacesLeft>0 enter -> Spaces[spacesLeft-1] | when  
spacesLeft<Capacity leave -> Spaces[spacesLeft+1]).
```
![[Pasted image 20250309141923.png]]
This is how it looks in Java: 
![[Pasted image 20250309141950.png]]
- Remember youll have methods like "public synchronized void enter(){
	 ...}"

- We have chosen to use synchronised here which means only one thread gets access to this method and the shared resource spacesLeft
- This is not sufficient because there is no condition to not let in another car when it is full.
	- Slam an "if" statement in there too.
- So now we have a condtion that checks we only increment when there is at least one space. 
	- This is condition  synchronisation in practice. Access is dependent on meeting a condition.
- In reality though, we may want a car to "wait" until a space becomes available where a simple IF statement wont do that

#### Waiting and Notifying in Java:
- Typically a thread T1 enters the critical section, manipulates the data within the monitor, and then releases the lock for others to capture.
![[Pasted image 20250309142309.png]]

- The waiting mechanism:
	-  When a thread in a critical section cannot progress futher without satisfying a condition, it enters the arbitrary waiting queue for its chance to come back, make progress and release the monitor lock.
	- Meanwhile, other threads can acquire the monitor lock to use that or another critical section that may change the state of the monitor. 
	- The state change might generate a notification signal that wakes up one of the waiting threads in the queue

- Java Methods:
	- wait()
		- Causes the thread to exit the monitor, permitting others to enter.
		- Use it to wait in a queue for condition synchronisation
	- notify()
		- Notifies a single thread
		- Use it when there is only one condition on which a queue of threads is potentially waiting.
	- notifyAll()
		- Notifies all threads that the state of the monitor has changed
		- Safer option to use

#### Back to Implementing Controller:
![[Pasted image 20250309142706.png]]
- We used wait() which can throw an InterruptedException and notifyAll() to ensure all other threads recieve a nudge.
![[Pasted image 20250309142807.png]]

#### Car Park Model:
``` LTSA
|| CarPark = (Entrance || Controller || Exit)
```
![[Pasted image 20250309142901.png]]

#### Summary:
- Active processes should be implemented as Thread Instances
- Passive Processes will contain shared resources as attributes, and should be a monitor  - controlling access
- In Java, "wait" and "notify" allow us to implement condition synchronisation.

#### Homework Maybe:
A bounded buffer has a fixed number of slots. There is a producer process, e.g. a keyboard, that puts integer numbers into the  buffer array, and a consumer process, e.g. a display, that gets numbers from the buffer
- Model this in FSP
- Write down the Java code for the monitor
