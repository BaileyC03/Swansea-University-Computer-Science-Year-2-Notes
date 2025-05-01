- We can use the relational model to visualise data, we have keys too.
- This is building on top of the fundamental, relational model.
- Make sure you know the difference between cartesian product and natural join


A tuple in relational Calculus:
{t | P(t)} <- This is the set of all tuples t such that predicate P is true for t
- t is a tuple variable 
- t[A] denotes the value of tuple t on attribute A
- t ∈ r means tuple t is in relation r
- P is a formula that evaluates to true or false 

Predicate Calculus formulae:
- Set of attributes and constants
- Set of comparison operators {<, ≤, =, /=, ≥, >}
- Set of connectives {and (∧), or (∨), not (¬)}
- Implication (⇒): x ⇒ y , if x is true, then y is true
- Set of quantifiers:  
	- ∃t ∈ r (Q(t)): ”there exists (∃)” a tuple t in relation r such  
		that predicate Q(t) is true.  
	- ∀t ∈ r (Q(t)): Q is true ”for all (∀)” tuples t in relation r.

E.G.:
![[Pasted image 20241021131417.png]]
Relational Algebra: σ amount>1200 (loan)
Relational Calculus: {t | t ∈ loan (t[amount] > 1200)}
- t | <- the output is table t, such that...:
- t ∈ loan <- t is a subset of loan and...
- (t[amount] > 1200) <- for every tuples in t, the "amount" attribute of t is greater than 1200

E.G: 
![[Pasted image 20241021132005.png]]
Relational Algebra: Πloan-number (σ amount>1200 (loan))
Relational Calculus: ![[Pasted image 20241021132050.png]]
- t | <- the output table is t, such that
- Ǝs ∈ loan <- There exists a tuple s in such that the following predicate is true (all below)
- (t[loan-number]) <- t is a tuple that contains one attribute [loan number]
- which is equal to table s which is all loan-numbers where their amounts are ALSO over 1200

E.G: 
![[Pasted image 20241021132555.png]]
Relational Algebra: Πcust-name (borrower) ∪ Πcust-name (depositor)
Relational Calculus: ![[Pasted image 20241021132753.png]]
- the output table is t such that
- there exists a tuple s in borrower such that the output table's cust_name = the tuple s' cust name 
- OR
- there exists a tuple u in depositor such that the output table's cust_name = the tuple u's cust name
**Basically this just applies an "or" operator to both the "cust-name" attributes**

E.G: 
![[Pasted image 20241021134647.png]]
Relational Algebra: Πcust-name (σ branch-name=‘neath’ (loan ⋈borrower))
Relational Calculus: 
![[Pasted image 20241021134729.png]]
idk wtf this means so gl lmao:
![[Pasted image 20241021135438.png]]



Assignment:
T <- [Expression] (DONT USE AN EQUALS, USE AN ARROW OR U LOSE MARKS)
expression is a relational algebra expression and T is a table variable
This stores in T the table output of Expression

Assignment 2:
T'(s1,......,sn) <- [Expression]
- Lets you name all of the attributes of the new relation (not nexessarilly the same name they would get from Expression)
^ note this must be a new temporary variable, and not one of the existing ones.
^ This helps you break long relational algebra into steps instead of stupidly long equations
- How small you wanna break shit down is up to you.

![[Pasted image 20241017133417.png]]

#### Building Complex Expressions:
- These can be composed recursively, like in math
- Parenthesis and precedence rules (like BIDMAS) also exist
- The rules are:
![[Pasted image 20241017133521.png]]
But honestly you can just spam brackets to make shit work
Consider if they have common attributes & if you can even do this 

Complex nested expressions can be hard to read so make sure to:
- Check attributes that should match will be made to match and
- attributes that will be made to match should match

Break that MF down:
- Use good names for new relations
- Names the attributes on the LHS each time so you dont forget what you have
- Comment to explain what the relation 

SQL is not based on sets: 
- Even if relational model is
- Reason - getting rid of duplicates is expensive
- SQL is based on "bags" or "mulisets"


Relational Algebra is Procedural (step by step by step)
Relational Calculus is declarative 
^ they both have the same expressive power


