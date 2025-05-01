#### RECURSION:
- An important method of programming in Prolog is recursion. 
	- We've seen it so far in Haskell and Java.
- Below is the factorial program. Note how it looks different to what we're used to when it comes to recursion. This is due to it being formulated using *relations* (instead of functions).
![[Pasted image 20241220151532.png]]
- Note, the above program requires arithmetic and the "is" predicate. [Arithmetic comes later dw, just know for now "?- X is 5 + 3" returns "X=8".]

#### EXAMPLE:
	isDigesting(X,Y) :- justAte(X,Y).
	isDigesting(X,Y) :- justAte(X,Z), isDigesting(Z,Y).
	
	justAte(mosquito, blood(john)).
	justAte(frog,mosquito).
	justAte(stork,frog).
- From the above example, you could note that the stork is digesting the frog, the mosquito and the blood. 
- The frog is digesting the mosquito, the blood
- The mosquito is digesting the blood

#### THE SHORTEST RECURSIVE PROGRAM:
p :- p
- Programs with recursive calls always need a second goal or rule to terminate.