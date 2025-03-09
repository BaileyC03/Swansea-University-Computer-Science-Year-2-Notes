- SQL aka Structured Query Language

SQL Provides:
- Data Manipulation Language (DML)
	- Retrieve insert and modify contents
- Data Definition Language (DDL)
	- Add and delete database objects (like tables)
- Data Control Language (DCL)
	- Configure security access

E.G:
select distinct a1,a2,....., an (a is attributes)
from T1, ... Tm (T is tables)
where P (p is a predicate)

- when analysing an SQL statement, start with "from"


selection: <- Still a tuple filter
	select *
	from T
	where P

to remove duplicates, use "distinct" (like the example above)

Cartesian product: <- this makes a shit ton of tuples
	select *
	from T1,T2 <- This is T1 x T2
	or 
	select *
	from T1,...,T2

Rename 
	select *
	from T as S <- This is the same as ps(T) [the rename operator]
	where...

Set Difference (-) [NOTE: SOME MAY USE "EXCEPT" not minus]
([SQL statement 1]) minus ([SQL statement 2])
- this will automatically remove all duplicates of our results
- make sure schema the sae

Union:
	([SQL statement 1]) union ([SQL statement 2])
	- Make sure the schema  is the same

Intersection
 ([SQL statement 1]) intersct ([SQL statement 2])
 make sure schema is the same

### The rest you gotta slam together fundamental operators into one


Natural join:
select Distinct PROF.pid, name, dept, rank, sal, cid, year
from PROF, TEACH
where PROF.pid = TEACH.pid

Division: <- Note how an SQL statement can be nested within a "from" clause
select pid from T1)  
minus  
select pid from (  
(select * from (select pid from T1), T2)  
minus  
(select * from T1))


### SQL and RA
- Dont use the "Natural Join" keyword. It's cringe and flops on edge cases without telling you. 
	- Also u wont get marks :LiSmile:
- 


