#### What we want to show today:
- There is a turing machine U (called universal TM) which can recieve an input as a description of a TM M and some word w, and then simulates whatever M would do on input w.

#### What is a description?
- Let the alphabet be {a,b,c,⊥}
- We will use a,b for binary encoding, and c as a separation marker
- There is a lot of flexibility in the enoding, this one is just convenient

- let [n]2 denote the binary encoding of n (subset of) N using a and b as digits. 
	- We can also encode d (element of) {L,R,S} as [d]D andx ∈ {a, b, c, ⊥} as [x]Σ using digits from {a, b}.
- A state qn shall be described by the word: 
		![[Pasted image 20250423162842.png]]
	- where the rules are:
		- "on reading an a (element of) {a,b,c,⊥} write the symbol xa, move in the direction da and go to the ma-th state next.
		- What the fuck does this mean?c