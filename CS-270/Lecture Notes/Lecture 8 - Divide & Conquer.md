### Intro:
A general approach to bringing down time-complexity is using the Divide and Conquer paradigm. A good example of how to use this is the Min-max computation. An important way of solving this using Divide and Conquer is the Merge Sort.

### Divide-and-Conquer approach:
There are many ways to design algorithms. For example:
- Insertion-sort is incremental.
- Divide-and-Conquer is another approach.
	- Divide:
		- Divide the problem into a number of subproblem which are easier to compute (smaller instances of the same problem)
	- Conquer
		- Conquer the problems by solving them recursively.
		- Base case: If the problem is small enough, just bruteforce it (any direct approach).
	- Combine
		- Combine the subproblems' solutions to provide the solution to the bigger problem


#### A naive (non D&Q) MinMax Algorithm:
![[Pasted image 20241211090604.png]]
The "for" loop on line 2 makes N-1 comparisons in line 3. The "for" loop on Line 6 also makes N-1 comparisons on line 7. This means we have 2n-2 comparisons.

#### A Divide-and-Conquer MinMax Solution:
As we're dealing with subproblems, we state each subproblem as computing the min and max of a subarray A[p..q]. Initially, p = 1 and q = A.length but these values change as we recurse through each subproblem. 
- **Divide:** by splitting into 2 subarrays:
	- A[p, ..., r] 
	- A[r+1, ..., q]
- **Conquer:** by recursively computing the minimum and maximum of the two previously mentioned subarrays.
	- **Combine:** by computing the overall minimum as the min of the two recursively computed minima (minimums), and do the same for the overall maximum. 

#### A divide-and-conquer MinMax Algorithm:
![[Pasted image 20241211092958.png]]
On line 7, r computes the halfway point of A[p, ..., q]. For Example:
for p = 1, q = n and n = 1,2,3,4,5,6 we get r = 1,1,2,2,3,3
- (n = q - p + 1) is the number of elements from which we compute the min and max
- r = p + 1 = ceil(n/2) is the size of the first (leftmost) subarray.
	- q - r = floor(n/2) is the size of the 2nd (rightmost) subarray.
This one has (3/2)n comparisons.


3/2n < 2n - 2 (in 99.99999999999% of cases)


#### Main Example: Merge Sort.
Merge sort is a sorting algorithm based on the divide-and-conquer paradigm.  The worst case running time has a lower order of growth than insertion sort.
- Again, we're dealing with subproblems that are sorting subarrays. Like last time, the initial array is A[p, ..., q] but this changes as we recurse through subproblems.
- To sort:
	- **DIVIDE:** by splitting the array into 2 equal sized subarrays.
	- **CONQUER:** by recursively sorting the two subarrays
	- **COMBINE:** by merging the two subarrays to produce a single sorted array.
- The recursion bottoms out at 1 element so is trivially sorted.

#### Merge sort algorithm:
![[Pasted image 20241211100341.png]]
This runs in Θ(n) time [:o wow so cool]


#### Stability:
- For many sorting algorithms, there exists a key which provides the criteria for sorting (alongside other data); E.G: the last name as part of an employee record.
- It's common for different objects to have the same key. Often, such arrays are pre-sorted according to other criteria first. 
- The **STABILITY** of a sorting algorithm is now the property that the order of equal elements (according to their keys) is not changed. 
- Merge sort is traditionally stable provided we take the left element in case of equality.
- Insertion sort is also stable. 

#### In-place.
- A sorting algorithm sorts **IN-PLACE** if, aside from the given array and some auxiliary data, it doesn't need more memory.
- This can be important if the size of the array is very large (like size 10^9 or something)
- Insertion sort is in-place, whereas Merge sort is not. Merge sort needs 2n memory cells (n being the size of the array).
- Merge sort can technically be made in-place but is a complicated algorithm and hardly used.
- We use heap sort if we need in-place sorting.

#### Further Properties:
**Already Sorted**
- If the array is already sorted,  then only n-1 comparisons are needed with Merge-sort. Overall however it still needs time (theta)(n log n) because of the swapping and still needs 2n space.
**Combination Cost**
	- The general combination-cost of merge sort (due to swapping) is somewhat higher than what can be achieved with quick-sort. (Quick sort shifts the burden from the combination to the divison step, and that's in-place.) Because of this, quick sort is usually the basis of default sorting algorithms in libraries. (Quick sort is not stable).


#### Example:
- Computing the 2 largest entities in an array. 
- We must develop a Divide and Conquer algorithm which for input A computes:
	- The largest and 2nd Largest entry (x,y).
- To do this we must carry out the following steps:
	- Divide, Compute, Merge. (With some recursion basis)
	- **DIVIDE** the array A into 2 equal parts.
	- **COMPUTE** the largest and 2nd largest entries recursively for both subarrays (giving us 4 numbers)
	- **MERGE** the two sorted lists of length 2 (only 2, no larger) into one sorted list, then take the first two numbers from that list (assuming descending order) [OMG TWO POINTER]
	- **Recursion Basis:** 
		- If A = (x) then return (x, -inf).
		- If A = (x,y) then sort it, then return the result (x', y').
- What's the recurrence?
	- T(n) = 2T(n/2)+1
- Whats the solution?
	- T(n) = (theta)(n)
	- ^ First case of the master theorem