#### INTRODUCTION:
- As previously seen, functions can be defined in terms of other functions. Like so:
	factorial :: Int -> Int
	factorial n = product [1..n]

#### RECURSIVE FUNCTIONS:
- Functions can also be defined in terms of themselves. These are recursive.
	factorial :: Int -> Int
	factorial 0 = 1
	factorial n = n * factorial (n-1)
- This runs the following
	- factorial 3
	- 3 * factorial 2
	- 3 * 2 * (factorial 1)
	- 3 * 2 * 1 * (factorial 0)
	- 3 * (2 * (1 * 1))
	- 3 * 2 
	- 6
- Note that on negative integers this will cause a stack overflow as the base case is never reached.


#### USES FOR RECURSION;
- Some functions are naturally defined in terms of themselves. 
- THAT AND THERE ARE NO LOOPS IN HASKELL [omg wtf wow :o]

#### RECURSION ON LISTS:
- You can do recursion on lists. Checkit out
	product :: [Int] -> Int
	product [] = 1
	product (x:xs) = x * product xs

	length [a] -> Int
	length [] = 0
	length (x : xs) = 1 + length xs

	reverse [a] -> [a]
	reverse [] = []
	reverse (x : xs) = reverse xs ++ [x]
	(consider the call stack with this)

#### MULTIPLE ARGUMENTS:
- Functions with more than oen argument can be defined using recursion too.
	zip :: [a] -> [b] -> [(a,b)]
	zip [] = []
	zip _ [] = []
	zip (x : xs) (y : ys) = (x,y) : zip xs ys 
- note (x:xs) and (y:ys) indicate a non empty list.

#### MULTIPLE RECURSIVE CALLS
gray :: Int -> [Int]
gray (-1) = []
gray n = gray (n-1) ++ [n] ++ gray(n-1)