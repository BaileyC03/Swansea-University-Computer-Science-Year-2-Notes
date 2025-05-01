#### Ornamental Garden Problem: Looking Back
- Two Turnstiles (West & East) Allowing people to enter the garden
	- No need to let them leave
- The turnstiles run concurrently and share a single counter that they can increment 100 times each
	- Ideal way to generate a race condition

#### Figuring Out the Test Condition
- Faulty execution:
![[Pasted image 20250304113914.png]]
- Faulty trace of actions:
w.read[0] -> e.read[0] -> w.write[1] -> e.write[1]
-> e.read[1]-> e.write[2]-> end
	- ^ Note how you need more writes (3 in this case) to achieve 2 increments. We can count these to verify if something is correct.
- ERROR is a keyword in FSP
	- Represents a state with a label -1.
- If we consider that there must be N "write" actions for the program to complete successfully, we can count it like so:
```FSP
	Range R = 0..N
	TEST = TEST[0]
	TEST[v:R] = (when(v <= N){east,west}.write[u:1..v+1] -> TEST[v+1]  
| when(v <= N) reset -> TEST[0] | when (v>N) wrong -> ERROR).

||TESTGARDEN = (GARDEN || TEST)
```
- From here, in LTSA click on:
	- Check -> Supertrace
	and youll find auto generated faulty traces, if any

#### ATOMIC ACTIONS:
- An atomic action is defined as a statement (or set of statements) that is executed all at once (physically or logically). Such actions cannot be interleaved (for correct operation).

#### SYNCHRONISED KEYWORD:
- Synchronized methods embody critical sections of code
``` Java
public synchronized void increment(){
}
```
- Effects of synchronized:
	- Not possible for two invocations of synchronised methods on the same object to interleave
		- AKA if one is using it, the other suspends actions until the first is done
	- Automatically establishes hierarchical (happens-before) reationships with any subsequent invocation of the method for the same object.

#### SYNCHRONISATION: LOCKS:
``` Java
@override
public synchronized void increment(){
	int temp = value; // read value
	Simulate.HWInterrupt();
	value = temp + 1; // set value
}
```
- Synchronisation uses locks with acquire and release actions to manage access.
	- Once a thread object has access to it, no other thread can access it until the critical section is completed by the key owner.
- You may want to define the value variable as volatile.
	- In a multithreading environment, volatile makes all threads use the main memory of value, rather than a cached copy.
	- This is useful when you are expected to access a variable outside of synchronised blocks.

#### FEATURES OF SYNCHRONIZED:
- two instances of the same class will not be synchornized, each object will have its own lock
- Static methods with static variables are using the lock at the class level.
- Performance Issues / features: 
	- Threads compete against eachother to capture the lock. 
		- Once held by one, the others are suspended or blocked (computationally expensive)
	- If there are multiple synchronized methods in an object, a thread working on one of these methods does not allow others to access the other independent methods.

#### Features of Volatile:
- When does it provide safety?
	- One thread writes and others read
	- Multiple threads write, and the operations are atomic 
		- AKA doesnt depend on previous values (so does not work with increment, decrement or other composite operations).

#### The LOCK Model:
- Modelling  a lock is straightforward, you acquire then release.
``` LTSA
LOCK = (acquire -> release -> LOCK).
```

#### Composition model for LOCK and MEMORY:
- We can compose MEMORY and LOCK together.
	- It does not impost a precedence between the alphabets of LOCK and MEMORY. 
	- We impose that later through the description of TURNSTILE
``` LTSA
||LOCKEDMEM = (LOCK || MEMORY).
```
![[Pasted image 20250309135052.png]]

#### The TURNSTILE model:
- So now we can introduce acqure and release actions to isolate those that were in the method under synchronisation
``` LTSA
TURNSTILE = (go -> write[0] -> RUN),
RUN = (return -> TURNSTILE | acquire -> CRITICAL),
//CRITICAL is the part protected by lock
CRITICAL = (arrive -> INCREMENT | release -> RUN),
INCREMENT = (read[v:0..N-1] -> write[v+1] -> CRITICAL
| read[N] -> CRITICAL).
```
#### The GARDEN model:
``` LTSA
||GARDEN = (east:TURNSTILE || west:TURNSTILE || {east,
west}::LOCKEDMEM) /{reset/{east, west}.write[0],
go/{east, west}.go}.
```

#### Looking at the Code: 
![[Pasted image 20250309135317.png]]
And a boolean flag (below) for switching between faulty and fixed code and an explicit "reset" method:
![[Pasted image 20250309135347.png]]
and the go method (below) now has an additional flipSynchronised method.
![[Pasted image 20250309135412.png]]

#### Atomic Variables:
- Non-blocking code, for example, tries to do something (then if it fails, it retries), rather than waiting on locks. 
	- Can be a good alternative from a performance perspective (for simple counting operatios)
- Atomic variables in JAVA allow non-blocking operations on variables using low-level machine instructions
	- Typical Options:
		- AtomicInteger
		- AtomicLong
		- AtomicBoolean
		- AtomicReference
![[Pasted image 20250309135612.png]]


