#### FINITE AUTOMATON 
-  Something consisting of states
- States - drawn as small little circles
- Automaton must be in one of these states at any given time
	- Starting state defined by arrow from nowhere into starting state
- We must tell the automaton what to do if it reads a given symbol
	- AKA if in state x and reads symbol A, go to state y

#### FINAL / NOT FINAL STATES
- Some states are final, some are not final.
- Final states are dictated as having double rings
- Any states can be final, kinda arbitrary (including starting)
- Using these, we can answer yes or no questions
	- If ending state after all actions is final, return "yes"
	- Otherwise, return "no"
- This is a model of computation, you can visualise how the computation works
- Yes/No questions can actually be expressive enough to build up other stuff.
- The automaton is the visualisation, not the thing behind it

#### AUTOMATON VS LTS
- LTS is the part of an automaton without the answers.
- Automata add the element of providing answers.
- We specify it's reading in symbols and returns yes/no by adding final states

#### READING IN:
- If one arrow is followed with many symbols, write it as a,b for if 
	a and b result in the same resulting state.
- If there is no instruction what to do when reading a symbol (no arrow labelled properly), return no automatically. 

#### WHICH PATH DOES IT PICK?
- If multiple paths both with the same symbol, the automaton will try all, if one version of it returns a "yes", the automaton provides a "yes". If no "yes", then its a no. 

