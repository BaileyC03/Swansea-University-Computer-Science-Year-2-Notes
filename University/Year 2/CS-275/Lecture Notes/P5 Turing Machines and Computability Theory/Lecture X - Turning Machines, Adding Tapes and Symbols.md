#### A single tape can be difficult to use.
- Try describing a TM (one tape) that decides the language {ww | w ∈ Σ∗}
- It's very cumbersome, but possible.
	- It would be much easier, if we have two tapes.

#### Addition of multiple tapes:
- A two -tape Turing Machine has 2 unbounded tapes, each with a unique read/write head.
- Thus, transitions now depend on the current state and 2 symbols.
	- They also yield the new state and 2 symbols to write and 2 directional commands.
- The input is initially on the first tape and the second tape is initially completely blank.
Theorem:
- 1 and 2 tape TMs have the same computational power.

#### Are we not cheating with the alphabet? 
- Proposition:
	- TMs using only Σ ∪ {⊥} as alphabet are as powerful as TMs using a larger alphabet Σ' ⊇ Σ ∪ {⊥}.
- Proof:
	- We can first space out the input such that after eah cell containing an input character, there are k blank cells.
	- Then, we can use binary encoding on those free cells to stand in for 2^k extra symbols.
## Refer back to lecture for understanding on this ^^


