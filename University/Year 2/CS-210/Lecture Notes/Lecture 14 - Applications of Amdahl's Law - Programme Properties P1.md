	#### Amdahl's Law Important Observations:
- What if ts~ ∈ (0, 1]?
	- Here we are looking to see how adding cores can affect performance given a certain amount of serial part in a programme.
	![[Pasted image 20250313120118.png]]
	- The benefit diminishes as you add more cores, sepending on how much of the code is ts~ - it may not be beneficial to do this at all.

- What if we have infinite cores? (n -> inf)
	- Here we want to see what is the upper bound of speed up if we have unlimited cores.
	- 1/inf tp~ = 0 tp~ = 0
	- = 1/(1/k) ts~ = k/ts~
	-  therefore, L(k,inf) <= k/ts~

#### Exercises:
- What is the upper bound of speed up due to 12 cores when your programme has 40% of parallelisable part?
- Solution:
	- k = 1
	- n = 12
	- tp~ = 0.4
	- ts = 1 - tp~ = 0.6
	- L(k,n) <= 1 / (ts + 1/n(tp~))
	- L(1,12) <= (1/(0.6+ (1/12)0.4)) = 1.58(ish)

- You come across a programme that has a 20% sequential part. Now you are told any of the following would take the time time and man hours:
	- Double performance for sequential parts and triple performance for parallelisable parts
	- Only quadruple the performance of a parallelisable part
	- Only quadruple the serial part
- The answer is the first option as the 3 options have a gain of:
	- 2.72
	- 2.5
	- 1.18

#### Properties of a Programme: 
- A property is an attribute of a programme that is true for every possible execution of that programme
	- i.e in all possible states
- Properties of interest for concurrent programmes fall into 2 categories:
	- Safety
		- Asserts that nothing bad happens during execution, must be true for all states.
	- Liveness
		- Asserts that something good (fairness, result, no restriction to progress) eventually happens. This is eventually true.

#### Safety and Liveness Properties:
- Safety:
	- Holds in all states - nothing bad happens:
	- Examples:
		- Deadlock Free
		- Mutual Exclusion
- Liveness
	- Eventually holds - something good happens:
	- Examples:
		- A Result
		- Fairness
		- Progress

#### Safety Properties:
- To check the safety property of a process P, we define a deterministic process property Q and do the following:
	- Create a composite process ||R = (P || Q)
	- Check whether R has paths to an error state or not.
		- Much like testing
``` LTSA
Entrance = (enter -> Entrance).  
Exit = (leave -> Exit).  
Controller(Capacity=4) = Spaces[Capacity],  
Spaces[spaceLeft:0..Capacity] = (when spaceLeft>0  
enter -> Spaces[spaceLeft-1] | when spaceLeft<Capacity  
leave -> Spaces[spaceLeft+1]).  
||CarPark = (Entrance || Controller || Exit).  
// Property for checking the number of total cars  
property TotalCars = TotalCars[0],  
TotalCars[i:0..4] = (enter -> TotalCars[i+1] | leave  
-> TotalCars[i-1]).  
||TestCarCount = (CarPark || TotalCars)
```
- This contains guards (the 'when') .
- What happens without guards?
![[Pasted image 20250313122541.png]]

#### Summary:
- The safety property asserts cases that must be true for all states throughout the LTS.
- Explicitly describing these properties helps us to ensure that we are not able to reach a **BAD** state, and LTSA will automatically tell us if we did reach a **BAD** state during compilation.
