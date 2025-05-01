#### SETS:
- Super fundamental notion is that of a set
	- We can possibly detemine the elements of a set
	- We can form sets via a self-defining property
- To bring mathematics to a computer we need to handle:
	- Creation and destruction of objects
	- Handling objects by value or reference
	- Naming (interfaces)
	- order issues (sets arent ordered, but in computing there is always an order.
- So we use the ADT "dynamic sets" - very mindful very demure.

#### ELEMENTS OF DYNAMIC SETS:
A "dynamic set" contains:
- Pointers (Iterators) to objects.
- Or the physical objects themselves (in java only for ints or other primitives, in c++ its every type of object)

Regardless of what the objects within a dynamic set are, access is only possible via pointer (or iterator)
- For insertion into a dynamic set, we must be given:
	- Object itself
	- we obtain back the pointer to the copy of that object in the dynamic set
- For deletion from a dynamic set, we:
	- Have the pointer of an object (already in the dynamic set)
	- We want to delete that very specific object

#### KEYS:
- Besides objects (which become 'elements' once in a set) and pointers, CLRS uses a "key" to identify an object.
- If an object is a list of personal attributes for example, a good key could be an ID number or a name.
- Often these keys can be used for sorting (think 250?)


#### DYNAMIC SETS: ELEMENTSHIP AND SEARCH:
With sets S we can "ask" if x (is an element of) S is true. This is probably the most basic operation we can call on a set.
- The equivalent of tihs on a dynamic set would be the search function. 
	- SEARCH(S,k) for key k and set S. It returns either a pointer to an object in S with key k or NIL if that object doesnt exist.
We do however require the ability to extract the key from an object in S and to compare the keys for equality.
- If we are storing S via an array (or list), searching can be performed in O(|S|) time [linear]
- However it is a goal for us to do it faster than this, think logarithmic.

#### DYNAMIC SETS: MODIFYING OPERATIONS:
- With the following operations, we can build and change dynamic sets:
	- INSERT(S,x) <- insert element x into set S [x is either element or a pointer]
	- DELETE(S,x) <- delete element x from set S [x is always a pointer here]
- Please note:
	- x in delete is different to x in insert. the delete x is always an iterator (or pointer, theyre synonyms)
	- The most important application of insert is for creatin a dynamic set.

#### DYNAMIC SETS: USING ORDER:
- Often it is assumed that a linear order is given on the keys.
	- besides k == k'?
	- we can now ask k <= k' ?
- In practice, using strict orders '<' is more common however this can create technical complications

#### DYNAMIC SETS: FOUR FURTHER OPERATORS:
- MINIMUM(S)
	- returns a pointer to the element with the smallest key
- MAXIMUM(S)
	- returns a pointer to the element with the largest key
- SUCCESSOR(S,x)
	- returns the next element after element with pointer x in set S
- PREDECESSOR(S,x)
	- returns the previous element after element with pointer x in set S

#### USING SORTING ALGORITHMS: STATIC CASE
- Dynamic sets can be realised using sorting, where we need to assume a linear ordering on the keys
- If the set S with n elements is to be built only once, at the beginning, from a sequence of element, then sorting the element in an array and sorting them - using for example MERGE-SORT with a time complexity of O(n*log n) is a good option:
	- SEARCH then takes time O(log n) using binary search
	- while each of MINIMUM, MAXIMUM, SUCCESSOR, PREDECESSOR all take constant time.
- We honestly only give a shit about the dynamic case though where insertions and deletions are used in unpredictable and weird ways.

#### USING SORTING ALGORITHMS: DYNAMIC CASE
- Now, in a dynamic case, INSERTION and DELETION take time O(n) while the others still take log time. 

#### SPECIAL CASES OF DYNAMIC SETS:
- Buffer
	- Only insertion, show-selected-element (like top) and delete-selected element; (special cases are stacks and queues)
- Priority Queue
	- Only insertion, minimum, maximum, delete_min and delete_max are needed
- Dictionary
	- Only insertion, deletion and search (no order requirements)
 
#### DICTIONARIES:
- 3 Operations
	- INSERT(X)
		- Input is pointer to x, an element that must be inserted
	- SEARCH(X)
		- Input is key k, returns a pointer
	- DELETE(X)
		- input is pointer x, an element that must be deleted
- We can use binary search trees (which generalise a binary search algorithm) to realise a dictionary
	- We can get all 7 operations for dynamic sets (assuming the keys are ordered linearly) from binary search trees.
	- Hashing is a technique specialised for dictionaries (doesnt support the four order-related operations)
	- Its usually faster for dictionaries (the  goal is constant time)

#### APPLICATIONS OF DICTIONARIES:
- A compiler! Ez
	- We have a bunch of different "identifiers" such for variables, functions and classes
	- E.G: "BreadthFirst" as a char sequence should be an identifier for a pointer to the data associated with the class
	- The dict translates the identifier into a pointer to the data
#### THE FASTEST IMPLEMENTATION: KEYS AS ARRAY INDECES
- With binary search trees we can achieve worst-case logarithmic time for the three dict operations
	- But what if we want constant time on average?
		- Doable if we provide enough space
	- We can do this by using arrays!
		- We can use the keys as array indeces and are pretty much done.
- HASHING IS THE PROCESS OF HANDLING ARBITRARY KEY SPACES K AS IF THEY WERE ARRAY INDICES.

#### THE BASIC IDEA OF HASHING
- We consider the keyspace K (an arbitrary set) and we can use an array of length m. The idea is to use a hashing functions which translates key-values into indeces.
	- The easiest way is when h is injective (maps different keys to different indeces)
	- injective hash functions are called perfect
	- For that to be the case we need |K| to be <= m *there are at most m different keys*
	- If not, we must handle collisions where 2+ keys map to the same index

#### THE SIMPLEST CASE OF HASHING:
- The simplest case of hashing is when for h we can use the identity, that is,
	- The keys are natural numbers >= 0
	- Within a feasibe range
- This is called a direct address (hash) table.

#### KEY OR NOT? 
- how can we show an element is *not* there? 
- Conceptually simplest is to use pointers where the NIL pointer shows it is not there
	- Alternatively we can use a special singular key-value
	- or a boolean array

#### EXAMPLES IN WHICH SIMPLE TRANSLATION IS NEEDED:
- If K is small, we can usually find a ice injective hash function h.
- If the keys are in a known range just move them
- If the keys are arbitrary images with 20 pixels just use binary encoding etc
- In principle we can ALWAYS use an injective hash function
	- If we have a lot of memory its very fast
	- Usually its not possible though as we need cases where the hash function yields the same index for diff keys

#### GENERAL HASH TABLES:
- The idea of hashing is to use a hash function
	h : K -> {0, ..., m-1}
	> m is the size of the hash table
	> an element with key k hashes to slow h(k)
	> h(k) is the hash value of key k
![[Pasted image 20241228160029.png]]

#### HOW DO WE HANDLE COLLISSIONS?
- In general, |K| is much larger than m
- The hash function should be as random as possible
- That it, it should hash unpredictably
- We should be indepentend of our choices of keys
- and should get as few collissions as possible
	- but we need to handle them regardless
HOW?
- Linked Lists:
	![[Pasted image 20241228161524.png]]
Collision resolution by chaining
	- Put all elements that hash to the same slot into a linked list?
	- slot j contains a pointer to hte head of the list of all stored elements that hash to j
	- if there are no such elements, slot j contains NIL
	- singly linked lists can be used if we dont intend to delete elements

#### ANALYSIS:
- What is the time-complexity of SEARCH?
	- Worst case (when all the n keys hash to the same slot and we end up with just a single list of length n)
		- hence the worst case runtime is theta(n), plus time to complete the hsh funtion
	- Average Case Performance?
		- Assume simple uniform hashing (any element is equally likely to end up in any of the m slots)
		- analysis in terms of the LOAD FACTOR a:= (n/m)
		- we assume the computation of the hash function takes constant time
	- theorem:
		- search takes expected time theta(1+a).
#### WHAT MAKES A GOOD HASH FUNCTION?
- What are the conditions of a good hash function?
	- h must be a function that for the same key, always returns the same hash value
	- Now ideally the hash function also satisfies the assumption of simple uniform hashing

#### USING KNOWLEDGE ABOUT THE KEYS:
- Qualitative information about the distribution of keys may be useful in the design process of a hash function:
	- in the compiler example, closelt related symbols like "pt" and "pts" tend to occur in the same program
	- So a good hash function would minimise the chance these two hash to the same slot
- This general guideline is to compute hash values which is independent of any patterns in the date
- This probably helps with keeping hashes secure? 


#### KEYS AS NATURAL NUMBERS: 
- To obtain a general overview, we assume that keys are natural numbers
- Henceforth, the first step in designing a hash function is to find a way to interpret the keys as natural numbers.
	- We usually use a radix system
	- in a radix system with base b>= 2 we have digits 0, ..., b-1 and a sequence of d1, ..., dn digits
- To get a natural number from the key, for the key space K one has to find a suitable base to allow keys to be interpreted as sequences of digits to base b
- E.G: 
	- Consider the hashing of strings.
	- If we consider an ascii string we have b = 128 and "CLRS" would yield:
		- 67x128^3 + 76x128^2 + 82x128^1 + 83x128^0 
	- We need to be prepared to handle large numbers

#### THE DIVISION METHOD: 
- Now our keys are natural numbers, the easiest hash function is given by h(k) = k mod m
- (m is the modulus)

#### WHAT DO I PICK FOR m?
- It's not just dictated by storage space
- One doesnt care if we have 10kb more or less
- So we can have some space to manoeuvre 
- that space is needed to make the remainder func a good hash func.
- GENERAL ADVICE:
	  Choose a prime number m which isnt "too close" to an exact power of 2
- In general, the remainder function yields a good hash func assuming a prime number is chosen thats unrelated to any patterns in the distribution of the keys
- E.G:
	- consider n=2000 where we want to examine on average 3 elements on an unsuccessful search. So assuming a good hash function, the size of the table should be around (2000/3) = 666.66666....
		- The first prime number greater than this is 673
		- the closest powers of 2 are 512 and 1024
		- So this choice is reasonable. 701 is also reasonable.

#### UNIVERSAL HASHING
- In practice, hashing by division using an appropriate remainder function as a hash tends to perform well however we dont have a guarantee that:
	- Lets say we have someone who wants to fuck with your code and has seen the function in advance. He could choose keys which all hash to the same slot, giving worst case behaviour.
	- To get around this, we can use a different hash function each time. Unless the adversary knows how you randomly choose a hash each time he cant intentionally fuck with your code.
	- NOTE: just because we choose a func randomly doesnt mean its a good hash func. It's good to randomly choose one from a set of predetermined "good" candidates.
		- these schemes exist undr universal hashing
		- They need to use true random bits (which you can get from an OS) but in practice a pseudo-random gen should work

#### PERFECT HASH FUNCTIONS:
- Consider the case where the key-space is the set of strings of length n (using only characters +,-,0)
	- How large is the key space?
		- |K| = 3
		- Can you find a bijective hash function (not only perfect but minimal)
			- 3 ^ n (n being length of strings)

#### HASHING BY CHAINING AND DIVISION:
- Demonstrate what happens when we insert the keys
	5,28,19,15,20,33,12,17,10
	into a hash table with collisions resolved by chaining, using the division method with m=9 for the hash function.
	5 -> 5
	28 -> 1
	19 -> 1
	15 -> 6
	20 -> 2
	33 -> 6
	12 -> 3
	17 -> 8
	10 -> 1
- Under what circumstances does hashing w chaining have constant runtime for all three dictionary operations?
	- Simple uniform hashing + constant load factor

#### DIVISION METHOD:
- Why is it actually bad to choose a power of 2 or a non-prime number a bad choice?
	- It leaves patterns in your data!
		- Choosing primes minimises the chance of hitting an additive pattern.
		- Staying away from ^2 reduces chances of hitting multiplicative patterns

#### GENERAL HASH FUNCTIONS:
- Assume you have a good hash function for strings.
	- Can you derive hash functions for other data types? 
- Poor mans hash function? 
	- Just represent the data via strings