#### JAVA: THREAD LIFECYCLE:
- NEW - A thread which has not yet begun in this state
- RUNNABLE - A thread which is running in the JVM in this state
- BLOCKED - A thread that is blocked as a result of a monitor lock in this state
- WAITING - A thread that is waiting for another thread to perform a particular action in this state
- TIMED_WAITING - A thread that is waiting for another thread to perform an action for up to a specified waiting time in this state
- TERMINATED - A thread that has existed in this state

#### INDEXED PROCESSES AND ACTIONS:
So on one hand you could do this:
BUFFER = ( store0 -> read0 -> BUFFER
| store1 -> read1 -> BUFFER
| store2 -> read2 -> BUFFER
| store3 -> read3 -> BUFFER).

^ this is kinda tedious. Instead we can do:

BUFFER = (store[i:0..3] -> read [i] -> BUFFER).
or
const N = 3
BUFFER = (store[i:0..n] -> read [i] -> BUFFER).

#### GUARDED ACTIONS:
- The choice (when guard B x -> P | y -> Q) describes a process similar to (x -> P | y -> Q) however x can only be chosen when guard B is true.
- **E.G: This Counter:**
	Counter (N=3) = Counter[0]
	Counter[1 : 0..N] = (when (i<n) increment -> COUNTER[i + 1] 
	| (when (i > 0) increment -> COUNTER[i-1]).

#### EXECUTION OF CONCURRENT PROCESSES:
- The term concurrency means logically simultaneous processing and does not imply multiple processing elements (PEs)
- Parallelism means you actually execute multiple processes in parallel
- Both concurrency and parallelism require controlled access to shared resources
	- So we consider them equivalent in this module teehee :3 

#### MODELLING CONCURRENCY:
- How should we model process execution speed?
	- Arbitrary speed, we abstract away time.
	- We want to model independently of the number of processes or the scheduling strategy.
- How do we model concurrency?
	- Arbitrary relative order of actions from different processes
	- interleaving but preservation of each process order
- What is the result?
	- A general model independent of scheduling; asynchronous (in time) model of execution

#### SUMMARY:
- We can model the lifecycle of a thread using FSP
- We can use indices in the FSP
- We can use guarded actions 
- We can model processes as logically parallel (but in reality they may be interleaved)