![[Pasted image 20241021143954.png]] 
^ Remember to use explicit join conditions, not natural joins. Thanks! 

This lecture is purely reinforcing lecture 6. Watch youtube videos on natural join and division and theyre muddy points from last year.

#### DIVISION IN SQL:
(select pid from T1)
minus
select pid from (
(select * from (select pid from T1), T2)
minus
(select * from T1))

#### SYNTAX OF AN AGGREGATE QUERY
select A1, ..., At agg1(B1), ..., aggm(Bm)
from T1, ..., Tn
where P
group by C1, ..., Cg
having H

where:
- T1, ...., Tn are tables
- A1, ..., At, B1, ...., Bm, C1, ..., Cg are attributes
- B1, ..., Bm are called aggregate attributes
- C1, ..., Cg are called group-by attributes
- Each of A1, ..., At must be a group by attribute 
	- each Ai is identical to some Cj where j is between 1 and t (length of table)
- P is a tuple predicate and H is a group predicate
- Agg1, ..., aggm are aggregate functions

#### AGGREGATE FUNCTIONS
agg(A)
- agg = count: return the number of values in A
- agg = sum: return the sum of values in A
- agg = min: return the minimum value in A
- agg = max: return the maximum value in A
- agg = avg: return the average of the values in A.
Note: "A" must be numeric for sum, min, max and avg

agg(distinct A)
	agg = count: return the number of distinct values in A
	agg = sum: return the sum of the distinct values in A
	agg = avg: return the average of the distinct values in A

#### EXAMPLE:
![[Pasted image 20250108152338.png]]
![[Pasted image 20250108152352.png]]
Note for the 2nd one: 
- count(A) is equivalent to count( * ) in which it returns the same result no matter which column is used as A. Hence, A can be as well omitted. Note that * cannot be used with "distinct", which must always be accompanied by a concrete attribute.

#### GROUP BY:
![[Pasted image 20250108152652.png]]
This statement does the following:
- Divide T into groups where each group consists of the tuples which are identical on all C1, ..., Cg.
- Execute the select clause on each group

![[Pasted image 20250108153002.png]]

![[Pasted image 20250108153153.png]]
I realise now the count ( * ) returns the count of the given tuple groupings present in the original table (PROF in this example)
![[Pasted image 20250108154019.png]]

#### HAVING 
select A1, ..., At, agg1(B1), ..., aggm(Bm)
from T
group by C1, ..., Cg
having H

Carries out the following steps:
- Divides T into groups where each group consists of the tuples which are identical on C1, ..., Cg
- Eliminate the groups which dont satisfy property H
- Execute the delect clause on the remaining groups

#### GROUP PREDICATE
- H is a set of aggregate comparisons connected by logic operator: AND, OR or NOT where an agg composition has this form:
	- agg(A) op v
		- agg is an aggregate function
		- op can be =, <>, <, <= etc
		- A is an attribute
- E.G:
	- select rank, max(sal) from PROF
	- group by rank
	- having count( * ) >= 2

#### WHERE
select A1, ..., At, agg1(B1), ..., aggm(Bm)
from T
where P
group by C1,...,Cg
having H

Carries out the following:
- Performing a selection on T using P
- execute the group-by, having and select on the result of the selection.

#### TUPLE PREDICATE P vs GROUP PREDICATE H
- A comparison in P has the form A op v whereas H has the form agg(A) op v
- P tuples the filters before the grouping, whereas H filters the groups after

#### EVERYTHING TOGETHER
select A1, ..., At, agg1(B1), ..., aggm(Bm)
from T1, ..., Tn
where P
group by C1, ..., Cg
having H

this statement does the following:
- Perform the cartesian product T1 x ... x Tn
- Execute where, group-by, having and select on the cartesian product.

