#### Learning Outcomes:
- Apply safety properties in FSP model development and analyse the system
- Apply modeling techniques to identify progress issues.
- Devise appropriate ways to eliminate progress issues.

#### The Single Lane Bridge Problem
Definition:
- A bridge over a river is only wide enough to permit a single lane of traffic. 
- Consequently, ars can only move concurrently if they are moving in the same direction.
- A safety violation occurs if two cars moving in different directions enter the bridge at the same time.
Modelling:
- Actions -> Enter & Exit
- Processes:
	- Active -> Car, Convoy, Cars
	- Passive -> Bridge
- Safety properties:
	- EntranceORder
	- ExitOrder
	- CarsFromOneDirection

``` FSP
Car = (enter -> exit -> STOP)
```
![[Pasted image 20250428100049.png]]
- It just enters and exits a bridge. 
	- Note this is only the building block for Convoy and Cars.

A convoy is a queue of cars:
``` FSP
const N = 2
range T = 0..N
range ID = 1..N //lower ID is for first car in queue
Car = (enter -> exit -> STOP).
|| Convoy = ([ID]:Car). //composing multiple cars with IDs.
```
![[Pasted image 20250428100241.png]]
- This violates the order of entrance and exit >:(
	- E.G: going from states 0 -> 1 -> 5 -> 6 -> 4
- To fix this, we introduce a couple of safety properties for entrance and exit:
```FSP
property EntranceOrder = EntranceOrder[1]
EntranceOrder[id:ID] = ([id].enter -> EntranceOrder[id%N+1]).

property ExitOrder = ExitOrder[1]
ExitOrder[id:ID] = ([id].exit -> ExitOrder[id%N+1])

|| CheckConvoy = (Convoy || EntranceOrder || ExitOrder)
```
- This means that any invalid sequences of actions leads to ERROR.
![[Pasted image 20250428100719.png]]
- While composing CheckConvoy, we will see an example trace to ERROR. 
- Note that the deadlock here is simply the end of the program so there's nothing to worry about
![[Pasted image 20250428100928.png]]
The LTS for CheckConvoy clearly shows where the issue is:
![[Pasted image 20250428101044.png]]
- So now we can create a couple of processes that allow us to model entrance and exit and associated order of events
``` FSP
Entrance = Entrance[1]
Entrance[i:ID] = ([i].enter -> Entrance[i%N+1])

Exit = Exit[1]
Exit[i:ID] = ([i].exit -> Exit[i%N+1]).

|| FixedConvoy = (ID:Car || Entrance || Exit).
|| CheckFixedConboy = (FixedConvoy || EntranceOrder || ExitOrder)

||Cars = ({west,east}:FixedConvoy) // Creating Cars
```
![[Pasted image 20250428102018.png]]

#### Creating Direction Properties
- Now we can create the property to check that there are only cars coming from one direction
``` FSP
property CarsFromOneDirection = (
	west[ID].enter -> CountWest[1] | east[ID].enter >CountEast[1]),

	CountWest[i:ID] = (west[ID].enter -> CountWest[i-1])
	| when i > 1 west[ID].exit -> CountWest[i-1]
	| when i == 1 west[ID].exit -> CarsFromOneDirection,

	CountEast[i:ID] = (east[ID].enter -> CountEast[i+1])
	| when i > 1 east[ID].exit -> CountEast[i-1]
	| when i < 1 east[ID].exit-> CarsFromOneDirection
)

|| CheckCars = (Cars || CarsFromOneDirection)
```
The LTS spit out from there shows that once we allow east cars to proceed, any west cars entering will generate an error and vice versa: 
![[Pasted image 20250428103801.png]]

#### OK GAMERS IT IS TIME TO MODEL THE BRIDGE
``` FSP
Bridge = Bridge[0][0],
Bridge[nWest:T][nEast:T] = (
	when (nWest == 0 && nEast<N) east[ID].enter -> Bridge[nWest][nWest+1]
	| when (nEast>0) east[ID].exit -> Bridge[nWest][nEast-1]
	| when (nEast==0 && nWest<N) west[ID].enter -> Bridge[nWest+1][nEast]
	| when (nWest>0) west[ID].exit -> Bridge[nWest-1][nEast]
).

|| SingleLaneBridge = (Cars || Bridge).
|| CheckSingleLane = (SingleLaneBridge || CarsFromOneDirection).

```
![[Pasted image 20250428104415.png]]
^ Bridge btw

#### NOW WE MUST CODE THE BRIDGE!
``` java
public class Bridge {
	private int westCount = 0;
	private int eastCount = 0;
	public synchronized void westEnter() throws InterruptedException {
	while (eastCount > 0) wait();
	westCount +=1;
	}
	public synchronized void westExit(){
		westCount -= 1;
		notifyAll();
	}
	public synchronized void eastEnter() throws InterruptedException {
	while (westCount > 0) wait();
	eastCount += 1;
	}
	public synchronized void eastExit(){
	eastCount -= 1;
	notifyall();
	}
}
```
^ This is a simple bridge class without queues for cars from the west and east, only using simple counters.
If we want to improve this and use more accurate queues, we can like so:
``` java
public class BridgeQueue {
	private Queue<Integer> westQueue;
	private Queue<Integer> eastQueue;
	private int westCount;
	private int eastCount;
	
	bridgeQueue(){
	westQueue = new LinkedList<Integer>();
	eastQueue = new LinkedList<Integer>();
	westCount = 0;
	eastCount = 0;
	}

	public synchronized void westEnter() throws InterruptedException {
	while (eastCount > 0) wait();
	westCount += 1;
	westQueue.add(westCount);
	System.out.println("Added to the west queue: " + westCount);
	}

	public synchronized void westExit(){
	System.out.println("Removed from the west queue: " + westCount);
	westCount -= 1;
	westQueue.remove()
	notifyAll();
	}

	// ETC ETC
}
```

#### Implementing cars:
- Cars are coming from the west and the east, so we are going to implement each west and east as Threads. Here, we have the West car implementation. It has the shared BridgeQueue instance and also a name.
``` java
public class WestCar implements Runnable {
	private BridgeQueue bridge;
	private String name;

	WestCar(String name, BridgeQueue bridge){
		this.bridge = bridge;
		this.name = name;
	}
}
```

#### How does a car run? 
``` java
@override
public void run(){
	Random random = new Random();
	int randomInt = 0;
	while (true){
		try{
			System.out.println(name + " is adding to west");
			bridge.westEnter();
			randomInt = random.nextInt(1000);
			Thread.sleep(randomInt);
			bridge.westExit();
			System.out.println(name + "removed from west")
			Thread.sleep(randomInt)
		} catch (InterruptedException ex) {
			System.out.println(name + " was interrupted");
			break;
		}
	}
}
```
- When this WestCar is run, it randomly queues up a card and waits for a while before removing it from the queue.
- Eastcar is the same but works on the shared Eastqueue not WestQueue

#### Finally - The Main Method:
``` java
public static void main (String[] args) throws InterruptedException{
	BridgeQueue bridge = new BridgeQueue();
	WestCar westCarA = new WestCar("WA", bridge);
	WestCar westCarB = new WestCar("WB", bridge);
	EastCar eastCarA = new EastCar("EA", bridge);
	EastCar eastCarA = new EastCar("EB", bridge);

	Thread twa = new Thread(westCarA)
	Thread twb = new Thread(westCarB)
	Thread tea = new Thread(eastCarA)
	Thread teb = new Thread(eastCarB)

	twa.start();
	twb.start();
	tea.start();
	teb.start();
	Thread.sleep(5000);
	
	twa.interrupt();
	twb.interrupt();
	tea.interrupt();
	teb.interrupt();

	twa.join();
	twb.join();
	tea.join();
	teb.join();

	System.out.println("Program has ended.");
}
```
- In the main program, we simply create the BridgeQueue and four different threads to work on it

#### LOOKING AT THE OUTPUT: 
![[Pasted image 20250428113829.png]]
- What the flip? Only WA and WB get to go through?
- This is called STARVATION!
	- Some of the threads never get to do anything and keep waiting for others.

#### Summary:
- Fairness and Progress are important properties through which we can ensure the liveness of a system.
- It is important to identify these and design out such subtle issues.