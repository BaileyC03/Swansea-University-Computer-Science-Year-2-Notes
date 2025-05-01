#### A Grammar:
- We have 2 different kind of symbols now.
	- "Terminal Symbols" correspond to actual outputs.
		- typically a, b, c, ...
	- "Non-terminal symbols " are just for internal workings.
		- typically S,A,B,C,T
			- S is a special non-terminal symbol. (The starting symbol)
- We have a bunch of rewrite rules:
	- S -> aT
	- T -> bSb
	- T -> c

#### Words Over and Alphabet:
- Let Σ be a (finite) set (known as the alphabet) and n ∈ N a natural number. . 
- With Σ^n we denote the set of functions from {0,1,...,n-1} also called words of length 
- E.G:
	- Let Σ = {a,b}. Then
	- Σ^3 ={aaa,aab,aba,abb,baa,bab,bba,bbb} 
		- where aba denotes the function returning a for inputs 0 and 2, and b for input 1.

## The Chomsky Hierarchy
#### Basic Idea:
- Grammars with simpler rules are easier to handle.

#### The hierarchy, an overview:
- Simplest to most complicated: 
- 3 - Regular languages (with right linear grammars)
- 2 - Context free languages (having context-free grammars)
- 1 - Context sensitive languages (w context-sensitive grammars)
- 0 Computably enumerable lanuages (having unrestricted grammars)
- -1 Arbitrary languages (not necessarily describable by a grammar at all)

#### Right-Linear Grammars: 
- A grammar is right-linear if all the rules are of the form:
	- T -> e or
	- T -> aR
	- where R is an element of N and a is an element of Σ
- A grammar is left-linear if all rules are of the form:
	- T -> e or
	- T -> Ra
- Theorem:
	- Right-linear and Left-linear grammars describe the same languages
#### Context-free Grammars
- A grammar is context-free if the left hand of every rule is a single non-terminal

#### Context-Sensitive Grammars
- A grammar is context-sensitive if every rule is of the form:
	- wAu -> wvu where v != e 
	- or is S -> e where S never appears on the right hand of a rule.

- A grammar is monotonic, if for all rules u->w (except maybe S -> e), it holds that |u| <= |w| and S never appears on the right-hand side of a rule.

- There's a theorem in which context sensitive and monotonic grammars describe the same languages




