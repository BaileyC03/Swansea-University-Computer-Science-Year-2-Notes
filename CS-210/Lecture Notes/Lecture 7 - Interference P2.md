#### Ornamental Garden Problem Slides:
![[Pasted image 20250217091043.png]]
![[Pasted image 20250217091054.png]]
![[Pasted image 20250217091159.png]]
(The "go" method is optional, but limits the threads to the use case here. It acts as a wrapper [or at least I think this is a wrapper? the fuck is a wrapper?])

#### WHAT IF WE DONT USE JOIN?
- The thread starts
- The code finishes
- Fuck knows what else.
	- join waits for the thread to die for predictable behaviour.

#### About The Above Code:
- The simulate class simulates user interactions (like the scan.nextInt() within a while loop) and is only for demonstration purposes
- A similar argument can be made for Thread.sleep (what?)
- Please note, the above code has 3 threads (2  for "go", 1 for the PVSM method to start stuff)

#### ORNAMENTAL GARDEN PROBLEM: EVENT FLOW:
![[Pasted image 20250217092953.png]]
- The main thread creates threads for west and east turnstiles and invokes the respective run methods
- The run methods in the threads are executed in parallel
	- We must check if shared counters cause any issues

#### Race Conditions:
The turnstiles are unaware of eachother, and their job is to look at the score and add one. 
If one turnstile looks first, then prepares to add one - then the other also looks and prepares to add one. The result is n+1 instead of n+1+1 because the "reading" element happened before the other one wrote.


#### Modelling the Ornamental Garden:
- Actions:
	- Arrive
	- Read
	- Write
	- Go
	- Reset
	- Return
- Processes]
	- Memory (counter)
	- Turnstile
	- Garden

#### FSP For the Ornamental Garden:
const N = 2  
range T = 0..N  
MEMORY = MEMORY[0],  
MEMORY[u:T] = (read[u] -> MEMORY[u] | write[v:T] ->  
MEMORY[v]).

#### Thinking back to the sequence of events in "go":
Event Flow:
- Reset everything (like writing 0 in memory)
- Then, at every "arrive" event, read a value and increment by adding 1 to it
	- Inside the incremebt method of the counter class

#### Modelling the Ornamental Garden:
Processes -> Alphabet:
east:TURNSTILE → east.{{arrive,go}, {read,write}[0..2]}  
west:TURNSTILE → west.{{arrive,go}, {read,write}[0..2]}  
{east, west}::MEMORY → {east, west}.{read, write}[0..2]
To Note: 
- Arrive should be different for each process
- Go should be common
- Read/Write are independent actions, except from:
	- write[0] is common (resets memory)
	- read[N] if we have written up to N we can return.

#### Modelling the Ornamental Garden - Code:
||GARDEN = (east:TURNSTILE || west:TURNSTILE  
|| {east, west}::MEMORY)/{reset/{east, west}.write[0],  
go/{east, west}.go, east.return/east.read[N],  
west.return/west.read[N]}.

#### Figuring out the Test Condition:
- A faulty trace of actions will always need more writes (i.e. 3) for a result (i.e. incrementing twice) due to lost increments bc of race conditions 🙁
- ERROR is a keyword in FSP:
	- It represents a state with the label -1 
	- ERROR is automatically generated when an index exceeds a specified range

