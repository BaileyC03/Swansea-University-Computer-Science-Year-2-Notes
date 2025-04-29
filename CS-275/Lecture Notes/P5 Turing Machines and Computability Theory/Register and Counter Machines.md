#### Topic Of Today:
- All models of computation we've considered so far were acting on finite strings.
- We can still use them for computations on numbers, graphs etc via encodings.
- But today we consider models of computations that natively act on natural numbers

#### Introducing - Register Machines!
Idea: 
- Reguster machines have access to infinitely many registers
	- Each register contains a natural number
- They can do arithmetic operations on these registers
	- thus is a powerful model of computation
Definition:
- A configuration of a register machine is specifying for each register Ri it's value - a natural number.
- Initially R1, R2, .... contain the input. Every other register is empty.
- The computation is given by a program (executed line by line) consisting of the following:
	- Addition -> Ri := Rj + Rk
	- Increment -> Ri := Ri + 1
	- Decrement -> Ri := max{(Ri - 1),0}
	- Assignment -> Ri := n
- Direct and indirect addressing:
	- Ri := R(R0)
	- Ri := Rj
- Conditional Branching
	- If (Ri = Rj) then GOTO line l
- if the program reaches it's end, the output is the content of R0

#### E.G: Computing Multiplication
1. If (R2 = R4) GOTO 5
2. R0 = R0 + R1
3. R2 := max(R2 - 1, 0)
4. If (R4 = R4) GOTO 1
5. END

#### Very Robust NOtion
- The definition of register machines is very robust.
- We could add wayyy more functions, remove direct or indirect addressing,
- allowed only for comparison to 0 etc...
- IT STILL HAS THE SAME COMPUTATIONAL POWER :o 
Theorem:
- A function f : N^k -> N is computable iff it is computable by a register machine 

#### Counter Machines
- Let's now make it very simple.
	- How much do we NEED to get all computable functions f : N -> N?

#### 3CM
- We use 3 counters. 
	- The first starting with the input
	- The other 2 ad 0.
- Our commands are: 
	- Ri := Ri + 1
	- If (Ri = 0) GOTO line l
		- else Ri := Ri - 1
- thats it.
- SIDE NOTE:
	- Counter and register means pretty much the same. Word choice depends on the commands we use.

#### 3CMs are mad powerful.
Theorem:
- A function f N -> N is computable iff it is computable by a 3CM
sketch:
- if we have 2 stacks, we can simulate a tape
- if we have an auxhillary counter, a counter can simulate a stack (least significant bit at the top)

#### What if we have 2 counters? 
- Cannot simulate all computable functions
- But we dont know if a 2 counter machine will halt or not