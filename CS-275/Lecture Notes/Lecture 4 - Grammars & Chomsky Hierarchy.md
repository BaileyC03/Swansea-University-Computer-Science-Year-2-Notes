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



