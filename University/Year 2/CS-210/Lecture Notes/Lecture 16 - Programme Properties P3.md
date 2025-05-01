#### Learning Outcomes
- Apply safety properties in FSP model development and analyse the system
- Apply modelling techniques to identify Progress issues
- To devise appropriate ways to eliminate progress issues.

#### Outline:
- Washing machine (example) & safety
- Progress & Fairness
	- Revisiting the single-lane bridge problem
	- Tossing a coin

#### Washing Machine Example & Safety:
The Scenario:
- You can turn it on and then turn it off
- Once on, it has the ClosedDoor which you can open to find the machine empty
- Now you can load it and make it full.
- When full:
	- You can unload it and make it go back to being empty
	- You can close the door and the machine is ready
	- You can now open the door or start it to wash, rinse and subsequently dry.
- At any point durin the washing process you should be able to pause and resume current operation.
There is a safety cycle property:
- Wash must come before rinse.
- Both must happen before dry.

#### Washing Machine - LTS:
![[Pasted image 20250428115155.png]]
And the FSP for it: 
![[Pasted image 20250428115212.png]]
We likely will want a safety property like CycleProperty to make sure we do things in the right order like so:
![[Pasted image 20250428115326.png]]

#### Safety and Liveness Properties: 
- Safety:
	- This property holds in all states -> nothing bad happens
	- E.G:
		- Deadlock Free
		- Mutually Exclusive
- Liveness:
	- This property eventually holds -> Something good happens
		- A result.
		- Fairness.
		- Progress.

#### Single-lane bridge problem, revisited:
 - We modelled and coded the system to guard against the following issues:
	 - Maintains entrance and exit orders
	 - Does not allow face-to-face crashes.
- The output of the program actually revealed that EA and EB never have to cross the bridge and add to the queue as cars keep getting spammed from the west. We call this starvation.
- We get no progress due to a lack of fairness :c 

#### Progress & Fairness
- Progress:
	- An action always eventually gets executed.
- Fairness:
	- If a choice over a set of transitions is made infinitely often, then every transition in the set will be chosen infinitely often.
Progress P = {a1, a2, ... an}
^ this defines a progress property P where at least one of the actions will be executed very often.

#### Progress - Tossing a Coin: 

###### FAIR COIN
``` FSP
// A simple coin process that produces heads or tails
FairCoin = 
(toss -> heads -> FairCoin | toss -> tails -> FairCoin)

// testing that heads can occur infinitely many times
progress Heads = {heads}

// testing that tails can occur infinitely many times
progress Tails = {tails}

// testing at least one of heads / tails occurs infinitely many times
progress HeadsOrTails = {heads,tails}
```
![[Pasted image 20250428122042.png]]

###### UNFAIR COIN
``` FSP
// a simple unfair coin that produces heads only
UnfairCoin = (toss -> heads -> UnfairCoin)

//testing that heads can occur infinitely many times
progress heads = {heads}

//testing that tails can occur infinitely many times
progress tails = {tails}

//testing that 1+ of heads/tails occur infinitely many times
progress HeadsOrTails = {heads, tails}
```
![[Pasted image 20250428122410.png]]

- Note in the above example that tails will not be satisfied

#### What if we put a FairCoin and UnfairCoin together? 
``` FSA
TwoCoin = (pick -> FairCoin | pick -> UnfairCoin),
FairCoin =
(toss -> heads -> FairCoin | toss -> tails -> FairCoin)
UnfairCoin = (toss -> heads -> UnfairCoin)

progress Heads = {heads}
progress Tails = {tails}
progress HeadsOrTails = {heads, tails}
```
Tails is STILL not satisfied as pick leads to a set of states where tails cannot occur.

#### Summary:
- Fairness and Progress are important properties through which we can ensure liveness of a system
- It is important to identify these issues to remove them through careful design