Syntax of an Aggregate Query

**select A1,...,At, agg1(B1). ..., Agg m(Bm)**
**from T1, ..., Tn**
**where P**
**group by C1, ..., Cg**
**Having H**

T1.,..,Tn are Tables
A1,...,A5, B1,...,Bm, C1,...,Cg are Attributes
B1,...,Bm are called aggregate attributes
C1,...,Cg are called Group-by attributes
Each of A1,..,At must be a group-by attribute (each Aj is identical to Cj were j is a subset of [1,t])
P is a tuple predicate and H is a group predicate
agg1, ..., Aggm are aggregate functions

Aggregate Function:
Agg = count : return the number of the values in A
agg = sum : return the sum of the alues in A
agg = min : return min value
agg = max : return max value
agg = avg : return avg value

agg(distinct A)
	- Changes "values" to  DISTINCT values

If you do a "select" then a "group by", the attribute you "select" MUST be in the "group by"
^^ comes up in MCQ in exam

Having:
- Carries out the following:
	- Divide T into groups where each group consists of all the tuples that are identical on all C1, ... , Cn
	- "H" is a set of aggregate functions

Where: <- Tuple filter 🗣
- Performs a selection T on 

Tuple Predicate VS Group Predicate
- Tuple predicate has the form A op V while a comparison in H has


P1 | 2 
	-

SQL 3 - Nesting in Where and Having: 

In - Membership Test
(A1,...,An) in ([an SQL Statement]) -> Remember anything returned by SQL is a set
returns True if tuple A1,...An appears in T
	   False otherwise
Not in -> The opposite :LiSmile:

Some:
A > some ([an SQL Statement])
returns true if A is greater than at least 1 of the members returned by the SQL statement

All:
A > all ([an SQL Statement])
returns true if A is greater than ALL members of the set returned by the SQL statement


Emptiness Test:
exists([an SQL Statement])
- True if SQL statement returns a table with at least one tuple
- false, otherwise

not exists([an SQL statement]) <- This is dynamic, there's basically a for loop
- True if an SQL statement returns an empty table
- false, otherwise

