#### SET COMPREHENSIONS:
- In mathematics, the *comprehension* notation can be used to construct new sets from old sets.
	{x^2 | x ∈  {1...5}} (The set {1,4,9,16,25} or x squared such that x is within 1-5.)

#### LIST COMPREHENSIONS:
- In Haskell, a similar notation can be used to construct new lists from old lists
	[x^2 | x <- [1..5]]
	- Note:
		- x <-[1..5] is known as a generator. States how to generate values for x.
		- Comprehensions can have multiple generators split by a comma.
			- [(x,y) | x <- [1,2,3], y <- [4,5]] gives us (below)
			- [(1,4), (1,5), (2,4), (2,5), (3,4), (3,5)]
		- Changing the order of the generators changes the order of the elements in the final list. 

#### DEPENDANT GENERATORS:
- Later generators can depend on the variables introduced by earlier generators.
	[(x,y) | x <- [1..3], y <- [x..3]]
	[(1,1),(1,2),(1,3),(2,2),(2,3),(3,3))]

#### GUARDS
- List comprehensions can also use guards to restrict the values produced by earlier generators
	[x | x <- [1..2], even x]
- Using a guard, we can define a function which maps a positive integer to a list of factors.
	factors :: Int -> [Int]
	factors n =
		[x | x <- [1..n], n 'mod' x == 0]
- Then we can extend this to figure out if a number is prime or not.
	prime :: Int -> Bool
	prime n = factors n == [1,n]

- We can now define a function using these which returns all prime numbers up to a given limit.
	primes :: Int -> [Int]
	primes n = [x | x <- [2..n], prime x]
	
