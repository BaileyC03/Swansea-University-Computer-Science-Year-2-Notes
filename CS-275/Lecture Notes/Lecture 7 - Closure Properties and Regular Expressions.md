#### Notation:
∧ - And
V - Or
∪ - Union of two sets
∩ - Intersection of two sets

#### A Closure Property:
- Theorem:
	- If L1 and L2 are regular languages:
		- L1 ∩ L2 is a regular language
		- L1 ∪ L2 is also a regular language

#### Concatenation:
L1 ◦ L2 := {uw | u ∈ L1 ∧ w ∈ L2}
- If L1 and L2 are regular languages:
	- L1 ◦ L2 is also a regular language

#### Kleene-Star
- Given a language L
	- let L^0 = {}
	- L^n+1 = LL^n
	- L^* = any combination of Ls
- If L is regular, so is L*

#### Regular Expressions
- Regular expressions are defined as follows: 
	- ∅ is a regular expression
	- ε is a regular expression
	- a is a regular expression for each a ∈ Σ.
	- R|Q is a regular expression if R and Q are.
	- RQ is a regular expression when R and Q are.
	- R* is a regular expression if R is

#### What does the above mean?
 - ∅ denotes the empty language.  
 - ε denotes the language {ε}  
-  a denotes the language {a}  
- R|Q denotes the language given by the union of the	languages denoted by R,Q  
-  RQ denotes the language given by the concatenation of the languages denoted by R,Q  
- R∗ denotes the language given by the Kleene star of the language denoted by R

#### Connection:
- A language is regular iff there is a regular expression denoted by it
	- That regular expressions denote regular languages follows from the closure properties we saw today