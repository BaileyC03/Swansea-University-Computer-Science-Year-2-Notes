SQL contains 3 aspects: 
- Data Manipulation Language (DML)
	- Retrieve, insert and modify database contents
- Data Definition Language (DDL)
	- Add and delete database objects
- Data Control Langage (DCL)
	- Configure security access

### Syntax of a SQL statement:
	select distinct from A1, A2,...An
	from T1, ..., Tm
	where P
^ T1,...,Tm are tables.
^ A1, A2, ..., An are Attributes
^ P is a predicate
- this table is essentially the following: 
	- *ΠA1,...,An (σP (T1 × ... × Tm))*

### Selection σ:
	select *
	from T
	where P
	
		E.g: 
		select *
		from PROF
		where rank = 'asst'
	equates to:
		σrank = “asst”(PROF)

		select *
		from PROF
		where not (rank = 'asst' and dept = 'EE')
	you can use <, <=, =, >=, > and AND, NOT, OR

### Projection Π:
	select distinct A1, ... , An
	from T
	 (above corresponds to ΠA1 ,...,An (T )) <- not part of the sql
	 
	 select distinct dept, rank
	 from PROF
	 (above corresponds to Πdept, rank(PROF)) <- not part of the sql

### Cartesian Product ×:
	select * from T1, T2 
	(above corresponds to T1 X T2)
	select * from T1,...,Tn
	(above correspponds to T1 X ... X Tn)

### Putting Multiple Operators Together:
	select distinct dept
	from PROF, TEACh
	where PROF.pid = TEACH.pid
	(corresponds to (Πdept(σPROF.pid = TEACH.pid(PROF × TEACH)))) <- not SQL

### Rename ρ:
	select...
	from T as S
	where...
	(corresponds to ...ρS (T )...)

### Set Difference −:
	([SQL statement 1])
	minus
	([SQL statement 2])
	(corresponds to T1 - T2 where T1 and T2 are the tables returned by statement 1 and 2 respectively)

### Set Union ∪:
	([SQL statement 1])
	union
	([SQL statement 2])
	(corresponds to T1 U T2 where T1 and T2 are tables returned by statement 1 and 2 respectively)

### Set Intersection ∩:
	([SQL statement 1])
	intersect
	([SQL statement 2])
	(corresponds to T1 ∩ T2 where T1 and T2 are tables returned by statement 1 and 2 respectively)

### Natural Join ⋈:
		select distinct PROF.pid, name, dept, rank, sal, cid, year
		from PROF, TEACH
		where PROF.pid = TEACH.pid
		(corresponds to ΠPROF.pid, name, dept, rank, sal, cid, year(σPROF.pid=TEACH.pid(PROF×TEACH)) which is the longform natural join)

### Division ÷:
	(select pid from T1)
	minus 
	select pid from (
	(select * from (select pid from T1), T2)
	minus
	(select * from T1))
	(It's basically divide, good luck. NOTE HOW AN SQL STATEMENT CAN BE NESTED IN A "FROM" CLAUSE)



![[Pasted image 20241112142324.png]]