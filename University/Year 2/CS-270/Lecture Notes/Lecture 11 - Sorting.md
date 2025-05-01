#### FIRST PROPERTY:  LEVEL-COMPLETENESS
- BINARY TREES:
	- These are rooted trees in which each inner node has one parent, a left child, a right child or both (root does not have a parent)
	- In data structures they should be as "balanced" as possible (the height should be as small as possible for the given number of nodes)
	- Recall height ht(T) of a rooted tree is the max distance between the root and any leaf
	- Perfect binary trees have exactly ((2^(h+1)) - 1) nodes
	- Level-complete binary trees are close to perfect
		- Can partition the nodes of a binary tree based on their distance from the root
		- we have levels K = 0,1,..., ht(T)
		- In general, level k has 1 to 2k nodes
		- If all levels except maybe the last one are full (have exactly 2k nodes in them) we say its level complete

#### THE HEIGHT OF LEVEL-COMPLETE BINARY TREES
- For a level complete binary tree T we have:
	- ht(T) = (floor(lg(#nds(T))))
	- where #nds(T) is the number of nodes on T
	- that the height T is the binary logarithm of the number of notes T after removing a fractional part.
- Balanced (good) trees should have:
	- ht(T) ~ lg(#nds(T))
- level complete binary trees definitely fulfill such.
	- Binary tree operations are often linear in the height of the tree, thus the height should be as small as possible.

#### SECOND PROPERTY: COMPLETENESS
- To have simple and efficient access to the nodes of the tree, the nodes of the last layer are better to not be placed in random order.
- Best is if they fill the positions left to right without gaps.
- A level-complete binary tree without gaps in the last layer is known as a COMPLETE TREE

#### THIRD PROPERTY: HEAP PROPERTY
- It would be too expensive to have this property (all nodes to the left <=, all nodes to the right <=) together with the completeness property
- However we have another property related to order (not just the structure of the tree) : The value of every node below it is not less than the value of any of its successors (nodes below it)
- In other words, all nodes below (to the left and right) are <=.
- This is considered the HEAP PROPERTY
- or also the MAX HEAP PROPERTY
- BINARY HEAP - a binary tree which is complete and has the heap property
	- We have binary max heaps
	- binary min heaps also :o 

#### FOURTH PROPERTY: EFFICIENT INDEX COMPUTATION
- Considering the numbering (not values) of nodes in a hypothetical example:
	- This numbering follows the layers - beginning with the first layer and going from left to right
	- Due to completeness property these numbers easily yield relations between a parent and its children
	- If the node has number p, the left child has number 2p an the right child 2p+1
	- Henceforth the parent has floor(p/2)

#### EFFICIENT ARRAY IMPLEMENTATION
- For binary search trees we needed full fledged trees.
	- We needed nodes with 3 pointers (parent, child L, child R)
	- However now, given complete binary trees we can use a more efficient array implementation using numbering for array indices.
- So a binary heap with m nodes is represented by an array of size m.
	- for such an index 0 <= i < m, the index of the left child is 2i + 1 and the index of the right child is 2i+2
	- while the index of the parent is floor((i-1)/2)

#### THE IDEA OF HEAPIFICATION
- The input is an array A and index i into A
- It is assumed that the binary trees rooted at the left and right of the child of i are binary heaps but we dont assume anything on A[i]
- After the heapification, the values of the binary tree rooted at i have been rearranged so that it is a binary max heap now.
- For this, the algorithm proceeds as follows:
	- First, the largest of A[i], A[l] and A[r] is determined where l = 2i and r = 2i+1 (2 children)
	- if A[i] is largest then we are done
	- Otherwise A[i] is swapped with the largest element and we call the procedure recursively on the changed subtree.


#### ANALYSING HEAPIFICATION
- We go down from the node to a leaf (in the worst case) and thus the worst case running time of heapification is linear in the height h of the subtree. O(h) and Theta(n)
- This is O(lg n) where n is the number of nodes in the subtree (due to height = log n)
- and again Theta(lg n)
	- For both of these one needs to make examples to show that the upper bound (given by the O) cant be improved

#### THE IDEA OF BUILDING A BINARY HEAP:
- One starts with an arbitrary array A of length n, which can be rearranged into a binary heap. E.G:
	  A = (4,1,3,2,16,9,10,14,8,7)
- We repair (heapify) the binary trees bottom-up
	- The leaves are already binary heaps on their own.
	- For all the other nodes (right to left) we simpl.y call the heapify procedure.

#### ANALYSING BUILDING A HEAP:
- Roughly we have O(n * log n) many operations:
	- However it pays off to consider most subtrees are small
	- So then we get runtime O(n)
- So building a heap is linear in the number of elements
#### THE IDEA OF HEAP-SORT:
- Now the task is to sort an array A of length n:
	- First, make a binary max heap out of A
	- Then repeat the following until n = 1:
		- The max element is now A[1] - swap that with the last element A[n] and remove that last element, i.e., set n = n - 1
		- Now perform heapification for the root, i.e, i = 1. We have a binary heap again (of one length less)
- The runtime is O(n * log n) and since its comparison based, also Theta(n * log n)
#### REMARK ON SELECTION-SORT:
- We see that HEAP-SORT is an intelligent form of SELECTION-SORT (where we move from right ot left, not left to right):
	- We extract the largest element, the 2nd largest etc... as does selection sort
	- However we support the search by the binary heap data structure
	- Thus each search only takes Theta(lg n) and O(lg n) where n is the number of remaining elements whereas SELECTION-SORT takes Theta(n) for a search

#### ALL BASIC OPERATIONS ARE (NEARLY) THERE
- A priority queue has the operations:
	- Maximum
	- Delete Maximum
	- Insertion
- We use an array A containing a binary (max)heap (the task is just to maintain the max heap property)
- The maximum is A[1]
- For deleting the max element, we put the last elemenet A[n] into A[1], decrease the length by 1 then heapify the root
- Add new element by adding to the end of  current array and heapifying all of its predecessors up on the way to the root.

#### ANALYSIS:
- MAXIMUM is a constant time operation
- DELETE-MAX is one application of heapification so needs O(lg n) 
- INSERTION invokes up to the current height, many applications of heapification so its O((lg n)^2)

#### THE IDEA OF QUICK-SORT:
- Remember MERGE-SORT
	- Divide and conquer alorithm for sorting an array in worst-case time (Theta(n * log n))
	- The array is split in half, the two parts sorted recursively (via merge sort) then the two half arrays are merged to the sorted (full) array
- Now we split along an element x of the array:
	- We partition into elements <=x and > x (2 arrays)
	- Then we sort the sub arrays recursively
	- Done. Great success :)

#### AVERAGE CASE:
- If we actually achieve that both subarrays are at least a constant fraction a of the whole array, then we get:
	T(n) = T(a x n) + T((1 - a)x n) + (theta)(n).
	which is basically the second case of the master theorem and so we get:
		T(n) = Theta(n * log n).

- And we actually get that:
	- For the non-randomised version (choosing always the last element as pivot), when averaging over all possible input sequences (without repetitions).
	- For the randomised version (random pivot) when averaging over all INTERNAL random choices, here we do not have to assume something on the inputs, except all values are different

#### WORST CASE
- The worst case runtime of QUICKSORT is Theta(N^2) for both version
- This can be repaired, making also the worst case runtime Theta(n * logn).
- For example by using median computation in linear time for the choice of the pivot.
- In practice, introsort is used which starts with a quick sort then switches to heap-sort if recursion depth becomes too big. When the array is small enough, insertion sort is used.
- When pointers are to be handled, then Timsort is preferable which is derived from merge-sort and insertion sort.

Note:
Heap sort doesnt take advantage of any existing sorting.

#### SIMPLIFYING INSERTION:
- When discussing insertion into a max-priority queue implemented via a binary (max) heapp, we used a general addition of one element into an existing heap.
	- The insertion procedure used heapification up on the path to the root.
	- Now actually we have always special cases of heapification 
		- This special case is the new element only goes up, swapping with its parent which then already has its place, until the new element has found its place.

