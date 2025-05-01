#### From Deciding to Computing: 
- So far we have used automata to answer questions of "does this word belong to this language?"
	- AKA Yes/No questions.
- We can make an automaton do more complex things like computing a function Σ∗ → Σ∗ if we turn them into transducers.

#### Transducers - Basics:
- We have an input alphabet Σ and an output alphabet Γ
- We want an automaton to compute a function f:Σ*-> Γ*.
- Each transition gets a label x : y where:
	- x ∈ Σ ∪ {ε}
	- y ∈ Γ ∪ {ε}
	- This means if you read X, take this transition and write a Y

#### Some Potential Issues:
- Non-deterministic transducers usually would compute relations / multifunctions. We only discuss deterministic transducers here.
- When does the transducer stop?
	- We forbid loops with ε : y -transitions only.

#### From transducers to control mechanisms: 
- Idea: An automaton interacting with the real world.
- Potential sensor inputs form the input alphabet
- Potential actuator commands form the output alphabet
- CS-368 continues this line of thought.

