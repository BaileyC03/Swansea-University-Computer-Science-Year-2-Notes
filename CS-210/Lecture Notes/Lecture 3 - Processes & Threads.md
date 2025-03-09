#### THREADS IN JAVA
- Thread class is part of the java.lang package
- Instance of Thread class manages a single sequential thread of control
- Instances may be created or deleted dynamically
-  An instance executes the content in the "run" method once the start method is called
- A thread instance **should** be properly shut down through InterruptedException
- The sleep method causes a running thread to suspend for a specified period of time

#### TWO WAYS TO DEFINE A THREAD IN JAVA:
- A "Spontaneous" Approach
	- We define a thread inheriting from the thread class and overriding the run method
	- Extending a Thread class is not good as we may need to inherit from another class (not just the thread) and java doesnt let us inherit from multiple
- A "Robust" Approach:
	- Implementing the "runnable" interface
	- Remember the main application thread should be separate from the worker thread

#### Choices in FSP:
- if X and Y are actions, then (x -> P | y -> Q) describes a process that initially participates in either of the actions x or y.
	- Aka if you do action x, you end up having behaviours described by P (state P)
	- or if you do action y, you end up having behaviours described by Q (state Q)

#### EXAMPLE: CRUISE CONTROL:
- Actions:
	- EngineOff
	- EngineOn
	- CheckSpeed
- SubProcesses:
	- Off
	- CheckSpeed

#### FSP Process Alphabet:
![[Pasted image 20250204143716.png]]
- This one has the issue that if you turn the engine on and off, you can increase speed.
- Sounds stupid and weird

A way to fix it: 
![[Pasted image 20250204143839.png]]
- Adding another state to ensure the action of setting speed is performed after turning on and before turning off.

#### SUMMARY:
- Looking at the traces can show potential issues with a system
- Implementing choices are shown via the following syntax@
	- (x -> P | y -> Q)
