#### RECAP:
- A turing machine has an unbounded tape
	- i.e. a double linked list
- and a finite control
	- a finite automaton
- At any moment, one position on the tape is active and can be read and written to (often considered read/write head).
- The turing machine continues to run until it reaches a special halting state; there is one for answering yes and one for "no".

#### OMG LOOK ITS A TURING MACHINE
![[Pasted image 20250423160540.png]]
This one is for {a^n b^n : n (element of) N}
#### A single tape is difficult to use
- Try describing a TM (with a single tape) that decides the language {ww | w (element of) input alphabet}
- This is much easier with 2 tapes

#### Multiple tapes: 
- A two tape TM has 2 unbounded tapes, with each having an independent read/write head.
- Thus, transitions now depend on the current state and 2 symbols. 
	- They yield the new state, 2 symbols to write and 2 directional commands
- The input is initially on the first tape, and the second tape starts completely blank.

In theory, 1 and 2 tape TMs have the same computational power

#### Are we cheating with the alphabet? 
- Proposition:
	- TMs using only Σ ∪ {⊥} are as powerful as TMs using a larger alphabet Σ' superset of Σ ∪ {⊥}
- Proof:
	- We can first space out the input such that after each cell containing an input character, there are k blank cells. Then we can use binary encoding on those free cells to stand in for 2^k extra symbols
- 