
#### Learning Outcomes:
- To identify the difference between task and data parallelism
- To apply data parallelism using the multiverse library for Software Transactional Memory

#### Outline:
 - Data Parallelism
 - Software Transactional Memory
 - A bank account example

#### Approaches for Implementing Concurrency - Recap
- Task Parallelism
	- How to organise threads and their communication without breaking concurrent correctness
	- Using lock-based synchronisation mechanisms
- Data Parallelism
	- A differen way to think about concurrency
	- Shared data is protected by accessing it in a sequential manner

#### Issues with Task Parallelism:
- Complexity
	- It's not always easy to get right
- Composibility
	- Difficult to code from smaller components without alterations
- Forget the Lock
	- Interference may occur
- Too many locks
	- Deadlock may occur
- Restoration
	- If things go wrong, it is not easy to restore to an earlier point
- Testing
	- Difficult to test due to non-determinism

#### Databases & Transactions
- Databases usually handle concurrency in accessing shared data fairly well in the form of transaction handling
- A database transaction symbolises a unit of work performed within the management system against a database, and is treated in a coherent and reliable way independent of other transactions. 

Two Primary Purposes: 
- Reliable units of work
	- Allow correct recovery from failures and keep a database consistent

- Provide Isolation
	- Offers isolation between programmes accessing (potentially concurrently) the database

#### Properties of Database Transactions:
- ACID Properties:
- A - Atomicity
	- All changes of data are performed as if they are a single operation. It's all or nothing here boyyyy
- C - Consistency
	- Data are in a consistent state when a transaction starts and when it ends
- I - Isolation
	- The intermediate state of a transaction is invisible to other transactions
- D - Durability
	- After a transaction is completed successfully, changes to the data persist and are not undone even if the system fails.

#### Software Transactional Memory (STM)
Key Points:
- A pattern to achieve data parallelism
- An extension or library for many standard programming languages
	- This does include Java
- A developer should not worry about concurrency
- The primary mechanism is to access the memory through a level of indirection

STEPS TO FOLLOW 
- Identify data in memory and mark transactions as part of a transactional log
- Make a local copy
- Work on the local copy
- Commit changes back to the memory atomically
	- On conflict -> Throw away all local operations and try again
	- On success -> Mark transactions complete
		- Your copy becomes new master copy

#### Limitations of STM: 
- If you can design out the concurrent issues, that may be preferable depending on the context

In fact, industry still uses the version of concurrency that we've looked at so far.
- Not all operations may be allowed, like sending / recieving over networks
- Potentially run expensive operations many times in case of conflicts as our commits fail and we have to start over
- Difficult to deal with large chunks of memory
- Still have to worry abut priority and contention.

#### Multiverse Library:
Steps to follow:
- Import the libraryes
- Use TxnObject and associated method calls
- Wrap the sequence of actions that are needed to be atomicised

#### A Simple, non-concurrent bank account
```java
public class AccountNonSTM {
	private double balance
	
	AccountNonSTM(double initBalance){
		balance = initBalance
	}

	public double getBalance(){
		return balance;
	}

	public void addBalance(double amount){
		balance = balance + amount;
	}

	public void subtractBalance(double amount){
		balance = balance - amount;
	}

	public void transfer(Account to, double amount){
		subtractBalance(amount);
		to.addBalance(amount);
	}
	
}
```
- In task parallelism, we will have to hold one account and wait for the other to become available before a transfer can occur. 
- We will see how to do data parallelism in this context.

#### Summary:
- STM gives us a different approach
- However there is no "one size fits all solution"
- We need to consider the situation and determine what is the best approach for our context.