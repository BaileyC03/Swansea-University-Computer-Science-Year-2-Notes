#### The Derivation Relation
- Definition
	- Consider a grammar G specified by terminals Σ, non-terminals N, start symbol S and set rules R.
	- The one-step derivation relation on (Σ U N)* is defined as: 
		-> := {(uvw, uv'w) | u,v,w,v' (elements of) (Σ U N)* (v, v') (element of) R}
	- The derivation relation →>:=,→+ is defined as the transitive closure of the one-step derivation relation

#### Infix notation
- We typically use infix notation for the one step derivation relation. 
	- i.e. we write u → w for (u,w) [element of] -> and u ->> w for
	- (u,w) [element of] ->>
- It's the same as us writing n/m for n divides m and x=y rather than (x,y) [element of] =, etc...
#### The Language Defined by a Grammar:
- The language defined by a grammar G is: 
	- L(G) := {w [element of] Σ* | S ->> w}
- 