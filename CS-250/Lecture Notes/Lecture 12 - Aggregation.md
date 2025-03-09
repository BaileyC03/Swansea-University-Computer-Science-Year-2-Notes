SQL offers more constructs to let users write more powerful queries. This lecture considers a lot of the ones used for statistical analysis.

### Syntax of an Aggregate Query:
	select A1, ..., At agg1(B1), ..., aggm(Bm)
	from T1, ..., Tn
	where P
	group by C1, ..., Cg
	having H

- T1, ..., Tn are tables
- A1, ..., At and B1, ..., Bm and C1, ..., Cg are all attributes
- B1, ..., Bm are aggregate attributes
- C1, ..., Cg are group-by attributes
- Each of A1, ..., At must be a group-by attribute (each Ai is identical to some Cj where j is between 1 and the size of the table)
- P is a tuple predicate. H is a group predicate
- agg1, aggm are aggregate functions

Right what does this mean?

### Aggregate Functions:
agg (A)
- agg = count: returns the number of values in A
- agg = sum: returns the sum of the values in A
- agg = min: returns the minimum value in A
- agg = max: returns the maximum value in A
- agg = avg: returns the average of the values in A
(note, A must be numeric for sum, min, max and avg)

agg(distinct A)
- agg = count: return the number of distinct values in A
- agg = sum: returns the sum of distinct values in A
- agg = avg: return the average of the distinct values in A
(distinct doesnt change the output of min and max)


### Group By:
	select A1, ..., At , agg 1(B1), ..., agg m(Bm)  
	from T  
	group by C1, ..., Cg
- The above statement carries out the following steps:
	- Divide T into groups  where each group consists of the tuples that are identical on all C1, ..., Cg.
	- Execute the select clause on each group
	*select max(sal) from PROF  
	group by dept*
	- Here, prof is divided into groups based on their department. 

### Having:
	select A1, ..., At , agg 1(B1), ..., agg m(Bm)  
	from T  
	group by C1, ..., Cg  
	having H
This statement carries out the following steps:
- Divide T into groups where each group consists on tuples that are identical on all C1,...,Cg.
- Eliminate the groups that do not satisfy H (group predicate)
- Execute the select clause on all **remaining** groups

### Where: 
