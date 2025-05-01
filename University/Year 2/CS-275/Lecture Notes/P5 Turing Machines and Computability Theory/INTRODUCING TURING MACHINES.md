#### The Idea: 
- Imagine a person, equipped with a pen and unlimited amount of paper.
- What kind of calculations could this person perform for you, if you need to fully specify what they ought to do? 

#### Similarities and differences to pushdown automata
- We have a double-linked list as a data structure, as opposed to a stack.
	- We call this list the tape.
- The input is initially written on the tape (rather than being fed from the outside symbol by symbol)
- A Turing machine needs to be explicit about when it is done

#### Turing Machines - A Formal Definition:
- A turing machine with the tape alphabet Σ′ ⊇ Σ ∪ {⊥} is specified by:
	- A set of states Q including 3 special states: q0, qyes, qno
	- A transition function δ : Q × Σ′ → Q × Σ′ × {L, R, S}
	(note:  Σ′ means that the tape alphabet contains every symbol from our input alphabet as long as a special bottom symbol ⊥)
- The idea behind the transition function is that we look at our current state and the symbol at the active position in the list.
- We then move to a new state, and change the current list position to a new symbol.
- We also go left or right on the list, or stay where we are

#### Configurations: 
- A configuration is a snapshot of what the turing machine is doing at a given moment.
- A configuration of a Turing machine is a triple:
	- (q,k,p) [element of] Q x Z x (Σ′)^z
		- q -> the current state of the machine
		- k -> the current position of the machine's head on the tape
		- p -> the current contents of the tape p which tell us what symbol is written at each position
- Initial config:
	- if the input is a string w, the config is:
		- q0, 0, w
			- machine head starting q0
			- head tape starts at position 0
			- tape has input string w starting at position 0, then everywhere else has blank symbol ⊥

#### Configurations - Making a move: 
- If the current configuration is (q,k,p):
	- Machine looks at the symbol currently under the head which is p(k)
	- It checks is transition function to see what to do next
	- δ(q, p(k)) = (q′, x, d)
		- change to state q'
		- write the symbol x at position k on the tape
		- move the head (d = R or L or S)
			- right / left / stay
- Halting:
	- If the machine reaches the state q_yes or q_no, it stops:
		- yes means it accepts the input and outputs yes
		- no means it rejects the input and outputs no