Last Lecture [[100 - Learning/Computer Science/University/Year 2/CS-250/Lecture Notes/Lecture 1 - Introduction|Lecture 1 - Introduction]]
Next Lecture: [[Lecture 3 - Relational Algebra]]

ANSI / Spark Architecture:
- 3 Tiers
	- Internal (system designers)
	- Conceptual (database designer)
	- External (Database user

#### Internal:
- Deals with physical storage of data
- Structure of records on files. pages, blocks
- Used by database system programmers
#### Conceptual: 
- Deals with the organisation of the entire DB's content
- Abstractions used to remove unneccessary detail
- The Database holds metadata

#### External Level: 
- Provides view determined by the user
- Data may be hidden or presented in a suitable form
- Used by users / Application Programmers

#### DBMS - Database Management Software
- Lets users:
	- Store Data
	- Manage Change
	- Organise Data
	- Retrieve Data
	- Retain Privacy
	- AND ALWAYS WORK

#### SQL Comes in 3 Parts:
- Data Definition Language (DDL)
	- Specifying DB Format
- Data Manipulation Language (DML)
	- Specify & Retrieve

### RELATIONAL MODEL 1: Tables & Keys:
- The relational model is standard for databases
	- The format of how to store data
	- Operations on how to query data

#### Data stored in tables
- Each Row is a tuple
- Each column is an attribute
- Relation Schema

#### Optionally, attributes have domains (data type)
Relation - A set of tuples
	- No duplicates
	- Order of tuples + attributes irrelevant


#### Keys:
- Set of attributes or which no 2 tuples (rows) have the same values

#### SuperKey:
 - Superset of other keys
 - Contains attributes in which every tuple' values within the attributes are a unique combination of values assigned to them
 - There may be multiple superkeys 
 - If 2 tuples have the same values on some of the attributes, but not all, then its ok you can add that tuple :)

#### Candidate Key:
- **MINIMAL** set of K attributes, such that no two tuples have the same values listed in the key.
- Subset of SuperKey
- Essentially, a minimal version of the SuperKey.
- There may be multiple Candidate Keys

#### Primary Key:
- One specific candidate key, chosen by the database designer.

#### Foreign Key: 
- Assume T and T' are 2 tables & K is a candidate key in T.
- If T' also contains K, K is a foreign K in T', referencing T.
	- It check "oh is this value of K within T?, if so its accepted :3" <- Real DB Words (joke)
- Consider the following tables:
![[Pasted image 20241008111811.png]]
- Prof has a candidate key {pid}
- Class has a candidate key {cid, year}
- Therefore, {pid} is a foreign key of Teach, referencing Prof.
- {cid, year} is a foreign key of Teach, referencing class
