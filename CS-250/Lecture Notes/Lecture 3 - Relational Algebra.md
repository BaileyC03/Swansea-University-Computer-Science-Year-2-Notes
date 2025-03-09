Previous Lecture [[Lecture 2 - Relational Model]]

### REMOVING REDUNDANCY IS VITAL

#### Choosing a key:
- We need to know it's impossible to create duplicates
	- It's not uncommon to make new attributes to ensure all tuples are unique
		- Think Student ID, for example
- A key is an integrity constraint
- Why not use National Insurance number as a primary key?
	- In the real world, people immigrating to the UK may not have one yet. 
	- Consider what works in theory VS what works in practice

#### Foreign Keys:
- Ensuring a tuple's attributes in one table exist in another.
- This is a referential constraint.


### Relational Model 2: Relational Algebra:
- A database may have many tables.
	- We need to be able to **pull out** specific rows and columns we may want
	- We will also need to be able to combine tables

#### How it Differs From Math Algebra:
- Tables can be considered the operands in which operations act upon
- Operators can be "choose the rows that satisfy X", where X is a predicate
- We use expressions to create our desired table, out of existing ones
	- The inputs and outputs of relational algebra is ALWAYS a table
- Some operators take one operand (root X), some take 2 (x + y)

#### Relational Algebra Operations:
1. Selection - $σp$(T) >> Note the subscript of the σp
	- T is the table the operation is being carried out on
	- p is the predicate that must be satisfied via tuples within T.
		- predicates can be comparisons like >, <, /= etc...
		- many comparisons slammed together with booleans like U, ^, ¬ (And, Or, Not)
	- T' is the output. 
		- T' has the same schema (attributes) as T
		- T' includes all and only the tuples in T satisfying the predicate p
	
2. Projection $∏a$(T) >> Note the subscript again.
	- T is the table the operation is being carried out on
	- a is a set of attributes in T
	- Output T' is a table containing:
		- All of the attributes listed in A, nothing else.
		- No duplicates
		- Note: Not the tuples associated with these values but just the different types / values you can find under said attribute (column)
		
3. Rename $Ps$(T) >> Note the subscript AAAAAAAH
	- T is the table, S is the string.
	- Output T' is the exact same table, just renamed to S
	
4. Union  T$1$ U T$2$
	- T1 and T2 are tables with the **SAME SCHEMA**
	- Output is T' with the same schema and all tuples contained in either.
		- Duplicates are removed.
	
5. Difference T$1$ - T$2$
	- T1 and T2 must have the **SAME SCHEMA**
	- The output is T', where T' contains all the tuples in T1 that are not in T2
	
6. Cartesian Product T$1$ x T$2$
	- Where T1 and T2 are tables
	- The output is T' which is a table that satisfies: 
		- The schema of T' contains all attributes of T1 and T2 
			- if they have the same name but are different, they are treated as different attributes
		- For every tuple t1 in T1 and tuple t2 in T2, T' contains a tuple t whos values are the same as t1 (or t2) on the attributes from T1 (or T2)
		- A.K.A: The output has every combination of tuples from T1 and T2.
![[Pasted image 20241008142215.png]]
PROF X TEACH = 
![[Pasted image 20241008142243.png]] 
If T1 has 5 tuples and T2 has 3, T1xT2 will have 15 tuples (5x3)
Attributes with the same name will be considered as different tuples.
Sometimes it will be like so:
- Professor.pid
- Teach.pid

