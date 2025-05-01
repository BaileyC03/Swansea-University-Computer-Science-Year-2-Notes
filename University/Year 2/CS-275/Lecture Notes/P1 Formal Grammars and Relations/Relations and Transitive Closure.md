#### Definition:
A binary relation between sets X,Y is a subset R [subset of] X x Y
A binary relation on X is a subset R [subset of] X x X
- More generally, an n-ary relation is a subset R [subset of] X1 x X2 x ... Xn. Unless specified, we use "relation" to describe binary relation

#### Properties of Relations
- A (binary) relation R on X is:
	- Reflexive if f ∀a ∈ X (a, a) ∈ R
		- AKA for all a within X, (a,a) is within the relation
	- Anti-reflexive if ∀a ∈ X (a, a) /∈ R
		- AKA for all a within X, (a,a) is NOT within the relation
	- Symmetric if ∀a, b ∈ X (a, b) ∈ R ⇒ (b, a) ∈ R
		- AKA for all a and b within X, (a,b) being within R means (b,a) is also within R.
	- Anti-symmetric if ∀a, b ∈ X ((a, b) ∈ R ∧ (b, a) ∈ R) ⇒ a = b
		- AKA for all a and b within X, if (a,b) is within R AND (b,a) is within R, then b and a must be the same.
	- Total if ∀a, b ∈ X (a, b) ∈ R ∨ (b, a) ∈ R
		- AKA for all a and b within X, (a,b) is within R OR (b,a) is within R.
	- Transitive if ∀a, b, c ∈ X ((a, b) ∈ R ∧ (b, c) ∈ R) ⇒ (a, c) ∈ R
		- AKA for all a b and c within X, if (a,b) is within R and (b,c) is within R, then (a,c) is also within R.

#### Examples:
- The relation <= on N is reflexive, anti-symmetrix, total and transitive
- The relation < on N is anti-reflexive, anti-symmetrix and transitive

#### Special Relations:
- Linear Order
	- Reflexive, anti-symmetric, total and transistive
- Equivalence
	- Reflexive, Symmetric and Transitive

#### Composition of Relations:
- Definition:
	- Given R being a subset of X x Y and
	- Q being a subset of Y x Z, let (R o Q) being a subset of X x Z be defined as: 
		- (R ◦ Q) = {(x, z) ∈ X × Z | (∃y ∈ Y )( (x, y) ∈ R ∧ (y, z) ∈ Q )}

#### Transitive Closure:
- Definition:
	- Let R be a relation on X.
	- We define R^1 := R, 
		- and R^(n+1) := R^n o R
		- and then R^+ = Un>=1 R^n 
- Theorem:
	- The relation R^+ is the smallest transitive relation extending R, and thus we cal lit the transitive closure of R.
- E.G: 
	- If S = {(n,n+1) | n (element of) N}.
		- S^+ = < 
- 