#### Relations:
- 1 Normal Form (1NF) - All data values atomic
- 2 Normal Form (2NF) - 1NF **and** every non-key attribute is fully functionally dependent.
- 3 Normal Form (3NF) - 2NF **and** no transitive dependency - functional dependency.
- Boyce-codd Normal Form (BCNF) - for every FD:A->B either:
	- B is contained in A (FD is trivial) or
	- A contains a candidate key of the relation

Decomposition of relations is lossless if we can recover the original relation through a join.

Lossy decomposition loses information, not tuples. 

Decomposing R into R1, R2 is lossless if X contains a candidate key of R1 or R2.
