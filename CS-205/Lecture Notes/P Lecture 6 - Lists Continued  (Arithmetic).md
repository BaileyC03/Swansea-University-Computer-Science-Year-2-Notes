#### ANONYMOUS VARIABLES:
- There is a nice, simple way to get information we want sometimes. 
- We can use the anonymous variable.
	?- [_, X2, _, X4 | _] = [mia, vincent, marsellus, jody, yolanda]
	X2 = vincent
	X4 = jody
	yes
- The _ is the anonymous variable (underscore)

#### RECURSING DOWN LISTS:
- The member/2 predicate works by recursively working its way down a list
	- Doing something to the head, then recursively doing the same thing to the tail (by affecting the new head each time)
- Its common in prolog so you NEED to master this >:o 

#### ARITHMETIC: 
- Theory:
	- Introduce prologs built-in abilities for performing arithmetic
	- Apply these to simple list-processing problems using accumulators
	- Look at tail-recursive predicates and explain why they're more efficient than non-tail recursive ones.

- Arithmetic in Prolog:
	- Prolog provides a bunch of basic arithmetic tools
	- Integers and real numbrs
![[Pasted image 20241220162047.png]]

#### A CLOSER LOOK:
- Important to know the following DOES NOT carry out arithmetic.
	- + 
	- -
	- /
	- *
- Expressions such as 3+2 are ordinary prolog terms.
	- Functors: +,-,/,*
	- Arity: 2
	- Arguments: Integers

#### THE is/2 PREDICATE:
- To force prolog to actually evaluate arithmetic expressions, we need to use "is".
- Like in our previous example, its an instruction for prolog to actually carry out the calculations.
- Because this isnt a normal prolog predicate, there are some restrictions

#### RESTRICTIONS ON THE USE OF is/2
- We are free to use variables on the right side of "is" 
- But when prolog carries out the evaluation, the variables must be instantiated with a variable-free Prolog term.
-  This prolog term must be an arithmetic expression.

#### NOTATION:
- Last 2 remarks on arithmetic expressions:
	- 3+2, 4/2, 4-5 are just ordinary Prolog terms in a user-friendly notation:  
		- 3+2 is really +(3,2) and so on.
	- Also the "is" predicte is a two-place Prolog predicate.

#### ARITHMETIC AND LISTS:
- How long is a list?
	- The empty list [] has a length of 0
	- A non empty list has length n+1
		- n being the length of its tail. 
			- This allows for recursive definitions of length

#### ACCUMULATORS:
	len([],0).
	len([_|L], N) :-
		len(L,X)
		N is X + 1
- This is a pretty good program. It's:
	- Easy to understand
	- Relatively efficient
- But there is another way of finding the length of a list:
	- Accumulators!
	- They are variables that hold intermeduate results

#### Defining AccLen/3
- The predicate acclen/3 has 3 arguments (/3)
	- List we want to find the length of
	- Length of a list (int)
	- Accumulator, keeps track of intermediate values for the length
		- Initial value is 0
		- Add 1 to the accumulator each time we take the head of the list recursively
		- When we reach the empty list, the accumulator is the length
	![[Pasted image 20241223121750.png]]
- Search Tree:
- ![[Pasted image 20241223121822.png]]


#### TAIL RECURSION
- Why is acclen/3 better than len/2?
	- acclen is tail recursive, len is not.
- Whats the difference?
	- In a tail recursive predicate, the result is fully calculated once we reach the baseclause
	- in non-tail recursive predicates, there are still things on the call stack (excluding our result) when we reach the base clause

#### COMPARING INTEGERS:
- Some prolog predicates actually do carry out arithmetic.
- These are the ones that compare integers (>, <, =:=, =\=, >=)





