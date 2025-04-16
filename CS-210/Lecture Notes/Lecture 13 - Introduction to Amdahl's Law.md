#### Deadlock Handling: An OS Perspective
- Unlike previously mentioned methods, OS cannot check for deadlocks statistically (by design, scanning and changing software bits)
- Operating Systems try to prevent or detect deadlocks dynamically (processes are always running to check this in your OS)

#### Deadlock Avoidance
- A Dynamic (run-time) scheme:
	- Do not start a process if its demands lead to a deadlock
	- Do not grant an incremental resource request to a process if this allocation may lead to a deadlock
- Essentially, the following apply:
	- Assume we know the maximum resources required
	- Track allocations in real-time
	- When a request is made, only grant if guaranteed no deadlock even if all others take maximum resource.

- Another Dynamic (run-time) scheme:
	- Probe programmes regularly to construct a resource allocation graph and see if there is at least one way to progress.
	- If not, then we are deadlocked.
- Recovery:
	- Once detected, we have the following options:
		- Abort all processes (common in many OS)
		- Back up to a predefined checkpoint
		- Abort processes successively until deadlock no longer exists
- Selection of processes for recovery may be based on processor time consumed, estimated time remaining, amount of output produced so far etc...
#### Resource Allocation Graph (RAG)
- Allows us to see the state of a system and investigate whether a deadlock is a possibility or not.
- A process P1 is holding resource R1 and hopefully it would finish, and simultaneously P2 can hold R1 (two instances) and T2 both, and complete its tasks:
 ![[Pasted image 20250313112217.png]]
 Pi - Process Pi
 Rj. - Resource Rj (one dot - one instance)
 Pk -> Rk.. - Pk is requesting Rk (with 2 instances - 2 dots)
 Pl <- RI - PI is holding RI

#### RAG - How To Determine Cycles:
- No Cycles = No Deadlock.
- If there are cycles:
	- If only one instance per resource type, then deadlock.
	- If several instances per resource type, then possibility of a deadlock.
		- Further analysis required to establish if all processes can complete.

![[Pasted image 20250313112548.png]]
^ Deadlock doesnt occur here because P2 can do its business then give up R2 to P3.
Then p3 can do its business then give R1 to P1

#### Programme Optimisation
- A programme or software optimisation is a process of modifying a software system to make certain aspects of it work more efficiently (execute more rapidly) or to use fewer resources (meomry, energy etc). There is usually a tradeoff between efficiency and resource usage.

- Levels of optimisation:
	- Design
	- Algorithms and Data Structures
	- Source Code
	- Build
	- Compile
	- Assembly
	- Runtime
	- Platform
- We should forget about small efficiencies 97% of the time. Premature optimisation is cringe.
	- That 3% is kinda huge tho
- As only some parts of code are able to be run in parallel, you get diminishing returns very quickly:
![[Pasted image 20250313113015.png]]
X axis - Number of simultaneous processors

#### Amdahl's Law:
- Optimising code (through parallelisation or code improvement) may lead to improving overall execution time of a program however there is a limit to how much performance gain is achieveable:
![[Pasted image 20250313113122.png]]
L - Upper bound of speed up in latency (proportional improvement in execution time)
	k - improvement factor in the sequential part
	n - improvement factor in the parallelisable part
t0 - Optimised execution time
ti - Execution time before improvement
	ti = t0(1,1).
- This helps us compute such theoretical limits for tasks with a **fixed workload**
- Why Bother?
	- We use it to decide what to optimise by determining where the biggest improvements can be made.

#### Amdahl's Law in Practice
![[Pasted image 20250313114053.png]]
- Initial total time for an execution is:
	- ti = serial part(ts) + parallelisable part (tp)
	- therefore:
		- tp = ti - ts (the only one we care about)
		- ts = ti - tp
- With n cores, the exection time for the parallelisable part will be:
	- t'p = (tp / n) = ((tits)/n)
- with a k times improvement, the execution time for the sequential part will simply be:
	- t's = (ts/k)
- Therefore, the combined execution time is:
- t0(k,n) = t's + t'p = (ts/k) + (tp/n)

- now, the speed up bound is given by:
	- L(k,n) <= ti/(t0(k,n))
- and
![[Pasted image 20250313115049.png]]
note:
- ts~ = ts/(ts + tp)
	- This is the proportion of the time spend executing the sequential part
- tp~ = tp(ts+tp)
	- This is the proportion of the time spent executing the parallelisable part in the original programme.
- Thus, tp~ = 1 - ts~
	- 1 is considered the (total) time
- Amdahl's Law => ![[Pasted image 20250313115324.png]]

#### Amdahl's Law -> Important Observations
- What if ts~ = 0?
	![[Pasted image 20250313115409.png]]
	The speed up increase is linear
	![[Pasted image 20250313115443.png]]

#### Summary:
- Resource allocation graphs can help OS programmers detect deadlocks
- Amdahl's law helps us quickly determine the potential performance gain for our optimisation efforts, and this is defined as the proportion between the execution time of the original programme and the execution time of the optimised programme

