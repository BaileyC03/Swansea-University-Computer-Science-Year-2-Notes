#### Learning Outcomes
- To apply data parallelism using the Multiverse library for Software Transactional Memory (STM).

#### Outline:
- Advantages / Disadvantages of parallelism - Recap and further emphasis.
- Array element swapping example

#### Concurrency Problems with STM:
- We no longer have the following problems:
	- Condition synchronisation / avoiding race conditions
	- Mutual exclusio public void 
n
	- Deadlocks and avoiding dead ends in exclusion

- We do, however, still have others:
	- Progress / Avoiding Starvation
	- Fairness across processes
	- Ensuring we always get a result

#### Limitations of STM
- Not all operations may be allowed
	- Such as sending or receiving over networks
-  Potentially run expensive operations many times in case of conflicts as our commits fail and we have to start over
- Difficult to deal with large chunks of memory
- Still have to worry about priority and contention

#### Advantages of STM
- LTS Simplifies how we deal with conceptual problems in our code / we don't have to worry about concurrent execution throughout our program.
- We can avoid many safety issues with concurrent programming.

#### Array element wrapping:
- Scenario:
	- We have a simple BinaryArray class
	- We want to create a program where it is possible to concurrently swap elements between two instances of BinaryArray
- In task parallelism, we would have to think about locking the first instance, then the second instance which may lead to a deadlock.
- So we're just gonnth, wa make sure if a Thread instance cant get both, we let go of the first array 

#### Step 1: Importing the library
``` java
import org.multiverse.api.stmUtils;
import org.multiverse.api.reference.*;
```

#### Step 2: Coding the BinaryArray Class
```java
public class BinaryArray
	private TxnBoolean[] array;
	private int length;

	BinaryArray(int length){
		this.length = length;
		this.array = new TxnBoolean[length];
		for (int i = 0; i < length; i++){
			array[i] = StmUtils.newTxnBoolean(false);
		}

	public int getLength(){
		return length;
	}
}
```
- We need a TxnObject for this purpose
	- but there are lots of possibilities in the library
- For new instances, we would use a method from StmUtils

```java

private boolean getStateAtIndex(int Id){
	return array[Id].get();
}

private boolean setStateAtIndex(int Id, boolean value){
	return array[Id].set(value);
}
```
- Internally we can use standard get and set methods from within the class instance.
- Externally however, this will throw errors so we need to use the atomic versions: 
``` java
private boolean atomicGetStateAtIndex(int Id){
	return array[Id].AtomicGet();
}

private boolean atomicSetStateAtIndex(int Id, boolean value){
	return array[Id].atomicSet(value);
}
```
 --- 
 ```java
public void atomicSwap(BinaryArray destination, int originId, int destId){  
StmUtils.atomic(() -> swap(destination, originId, destId));  
}  
private void swap(BinaryArray destination, int originId, int destId){  
boolean currentOrig = getStateAtIndex(originId);  
boolean currentDest = destination.getStateAtIndex(destId);  
setStateAtIndex(originId, currentDest);  
destination.setStateAtIndex(destId, currentOrig);  
}  
```
- AtomicSwap is the method that will be called by Thread instances.
- The structure we will follow is: 
	- StmUtils.atomic(() -> function(parameters))
- Swap method just contains the set of steps we need to perform atomically

#### Step 3: Coding the Swapper Class:
```java
public class Swapper implements Runnable{
	private BinaryArray one;
	private BinaryArray two;
	private int length;
	private String name;

	Swapper(String name, BinaryArray one, BinaryArray two){
		this.name = name;
		this.one = one;
		this.two = two;
		this.length = one.getLength();
	}
}
```
- The swapper models our threads that will independently swap things around
- It has a couple of BinaryArrays on which it performs the swap operations
- Now we can make the run method woahhhhh! :o 

``` java
@override
public void run(){
	Random random = new Random();
	while (true){
		int randO = random.nextInt(length);
		int randD = random.nextInt(length);
		one.atomicSwap(two, randO, randD);
		System.out.println(name + "Swapped");
		try{
			Thread.sleep(100);
		} catch (InterruptedException ex) {
			System.out.println(name + " interrupted!")
			break;
		}
	}
		
}
```

---
#### Step 4: Coding the Main Methods:
``` java
// It's threadin time
Swapper s1 = new Swapper ("s1", a, b);
Thread t1 = new Thread(s1);

Swapper s1 = new Swapper ("s2", a, b);
Thread t2 = new Thread(s2);

t1.start();
t2.start();

Thread.sleep(2000);

t1.join();
t2.join();
```
- Then, we generate a couple of independent threads and let them perform swapping on the arrays.

#### Summary
- STM gives us a different approach
- However, there is no one-size fits all solution.
	- We have to consider the situation and determine what is the best approach for out context.