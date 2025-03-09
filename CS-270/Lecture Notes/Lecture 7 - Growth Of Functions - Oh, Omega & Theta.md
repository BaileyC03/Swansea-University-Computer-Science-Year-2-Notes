### Growth Of Functions:
Big O - Worst Case (Upper Bound)
Big Omega 𝛀 - Best Case (Lower Bound)
Theta (not big) - Average Case 

O (g(n)) is the set of functions f(n) for which there are constants:
- g(n) is the asymptotic upper bound.
	- T(n) is O(f(n)) if, and only if
	- Tn <= C * f(n)
	- for all n >= n
	- AKA - basically if there is a C constant, you can multiply the function by and it's always above the runtime graph, it's a valid upper bound

𝛀 (g(n)) is the set of functions f(n) for which there are constants:
- c is within R (assuming R is larger than 0)
- n0 is within C0 such that:
- f(n) >= c*g(n) for all n >= N0
- aka the runtime graph should be above the lower bound at all points

𝚯 notation (theta) binds from both sides.
Assuming T(n):
- A good way to do to this is with  trial and error. If N^2 is too high, try N, etc etc.
- Once we find it, lets say N. We say it's bound to linear time.
#### 4 Main Levels of Growth:
In increasing order: 
1. Constant (fn = 𝚯1)
2. Logarithmic (fn = 𝚯(lg(n))
3. Polynomial (fn = n^x)
4. Exponential (fn = x ^ n)