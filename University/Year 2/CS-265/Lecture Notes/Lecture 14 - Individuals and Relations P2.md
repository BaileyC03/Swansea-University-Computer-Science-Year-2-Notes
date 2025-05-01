#### Reasoning with Variables:
- An *instance* of an atom or clause is obtained by uniformly substituting terms for variables
	- every instance of the same variable is replaced by the same term
- A *substitution* is a finite set of the form {V1/t1, ..., Vn/tn}
	- caps are variables
	- lowercase is concrete terms
- The application of a substitution σ = {V1/t1, . . . , Vn/tn} means:
	- Whenever you see V1, substitute it for t1
	- Vn, Tn
- if {X/A, A/e}, them X maps to e

#### Unifiers: 
- Substitution σ is a unifier of e1 and e1 if e1σ = e2σ.
- Substitution σ is a most general unifier (mgu) of e1 and e2 if:
	- σ is a unifier of e1 and e2 and
	- if substitution σ^i also unifies e1 and e2 then eσ^i is an instance of eσ for all atoms e
- The most general unifier is a substitution that makes two expressions identical while being the most general among all possible substitutions.
	- It can be applied to a broader range of clauses compared to other unifiers
	- It is the "least specific way" to unify two expressions by assigning variables with the most general possible values. 
	- For instance, 
		- unifying with X = a is more specific than X = Y as the latter would allow for other substitutions for Y.

- If two atoms have a unifier, they have a most general unifier.
- If there are multiple most general unifiers, they only differ in the names of the variables

#### Logical Consequence:
- Atom g is a logical consequence of KB iff:
	- g is an instance of a fact in KB, or
	- there is an instance of a rule:
		- g <- b1 ^ ... ^ bk
	- in KB such that each bi is a logical consequence of KB.

#### Proofs: 
- A proof is a mechanically derivable demonstration that a formula logically follows from a knowledge base.
- Given a proof provedure, KB |- g means that g can be derived from knowledge base KB.
- Recall KB |= g means g is true in all models of KB.
- A proof procedure is sound if (KB|- g) -> (KB |= g)
- A proof procedure is complete if (KB |= g) -> (KB |- g)

#### Unifiers: Code Example:
![[Pasted image 20250311124453.png]]
- it returns a sigma which is sed to make the two clauses the same:
- unify p(A, b, C , D) and p(X , Y , Z , e)  
	- {A/X , Y /b, C /Z , D/e}

#### Bottom-up Proof Procedure:
![[Pasted image 20250311124845.png]]

