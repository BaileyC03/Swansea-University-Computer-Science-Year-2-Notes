#### Similarities and differences to pushdown automata
- We have a double-linked list as a data structure instead of a stack (we call this list tape)
- The input is initially written on the tape (rather than being fed from the outside symbol by symbol)
- A Turing machine needs to be explicit about when it is done

#### Turing Machine - Formal Definition:
A Turing machine with the tape alphabet is specified by a set of states Q with three special states q0, q1, qno, and a transition function. 
- The idea behind the transition function is that we look at our current state and the symbol at the active position in the list. We then move to a new state, and change the current list position to a new symbol. We also go Left or Right on the list, or Stay where we are.
