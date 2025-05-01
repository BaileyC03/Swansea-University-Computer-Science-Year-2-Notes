#### QUESTION OF THE DAY (Or of all time?)
- How does undecidability relate to actual programming stuff? 

#### Equivalent TM's and semantic properties:
Definition:
- We say that TM's M1 and M2 are equivalent if, for any input w, either M1 and M2 both don't halt, OR they halt and give the same answer 
Definition:
- We say that a formal language P is a semantic property of Turing Machines. 
- If \<M1> is within P and m1 and m2 are equivalent, M2 is also implied to be eithin P.
	- In words, descriptions of equivalent TMs are either both in P or both not in P.

#### Rice' Theorem:
- A language L is called trivial if L = ∅  or L = Σ*
Theorem(Rice)
- Any non trivial semantic property of TMs is undecidable.
Example: 
- As a consequence, it is undecidable whether executing a given program will erase your hard drive or not

#### Rice' Theorem - Proof: 
- Let P be a non-trivial semantic property
	- We show that the halting problem is Turing reducible to it.
- Let Mnothing be a TM that does nothing, and let Msomething be a TM with \<Mnothing> within P <=> \<Msomething> not within P
- Let I be the TM we recieve as input for the Halting Problem.
- Let IMsomething be "simulate I on an empty tape, surpressing any outputs. If I halts, proceed to simulate Msomething on the input"
- If I halts, then IMsomething is ~= Msomething. If I does not halt, then Imsomething ~= Mnothing.
- So asking our oracle whether \<IMsomething> is within P lets us figure out whether I halts. QED
#### Here's why Programming is hard: 
- We can't decide whether a program is doing something bad (Rice) 
- We can't decide whether a program does what it's supposed to do (Rice).
- We can't decide whether a program is as fast as possible (not rice but similar)
- We can't decide whether a program is the shortest one doing it's job (not rice but similar)
So we must rely on partial cases, heuristics, limited programming languages etc

#### The Recursion Theorem: 
Theorem:
- Let T: Σ* -> Σ* be a computable function.
- Then there is a Turing machine M such that M is equivalent to      T (\<M>)
Corollary:
- Pick an computable transformation of Java programs.
- There is a program that does exactly the same as the transformed version

#### Recursion Theorem -> An Application
Corollary:
- There is a java program that prints its own source code
- Let Print map the input java program P to:
	```java
	class HelloWorld{
	public static void main(String[] args){
		System.out.println(P)
		}
	}
```

#### Erm, what the flip?
- These are called Quines!
- Theyre prolly cool as flip