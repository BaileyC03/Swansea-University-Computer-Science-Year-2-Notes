#### Deadlock Analysis: Primitive Processes
- When we mean to end a programme, the LTSA tool will still report there's a deadlock and we can safely ignore this.
``` LTSA
Process = (start->run->STOP).
```
![[Pasted image 20250309143525.png]]

#### Dining Philosophers - Simplified
- We will now model the dining philosophers problem, with 3 philosophers.
``` LTSA
Fork = (acquire -> release -> Form).
Philosopher = (sit -> right.acquire -> left.acquire -> eat -> left.release -> right.release -> stand -> Philosopher).
||ThreePhil = ({a,b,c}:Philosopher).
||Fork1 = ({a.right, b.left}::Fork).  
||Fork2 = ({b.right, c.left}::Fork).  
||Fork3 = ({c.right, a.left}::Fork).
||Table = (ThreePhil || Fork1 || Fork2 || Fork3).
```
- The deadlock occurs when all 3 philosophers go to pick up the right fork (no one can pick up 2 in order to later release both forks)
||Fork1 = ({a.right, b.left}::Fork).  
||Fork2 = ({b.right, c.left}::Fork).  
||Fork3 = ({c.right, a.left}::Fork).