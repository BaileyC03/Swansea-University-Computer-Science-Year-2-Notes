#### INTRODUCTION:
- A function is considered higher order if it takes a function as an argument or returns a function as a result.
	twice :: (a -> a) -> a -> a 
	twice f x = f (f x)

#### E.G: THE MAP FUNCTION:
map :: (a -> b) -> [a] -> [b]
- the above map applies a function to every element of a list [a]
- e,g: map (+1) [1,2,3]
- [2,3,4]
- The function is defined as:
	map f [] = []
		map f (x:xs) = f x : map f xs

#### THE FILTER FUNCTION:
- Filter selects every element from a list that satisfies a given predicate
	filter :: (a -> Bool) -> [a] -> [a]

- e.g: 
	filter even [1..10]
	[2,4,6,8,10]

- filter can be defined as:
	filter p []  = []
	filter p (x:xs)
		| p x = x : filter p xs
		| otherwise filter p xs

#### THE FOLDR FUNCTION:
- A number of functions on lists can be defined using a simple recursion pattern
	f [] = v
	f (x : xs) = x (something) f xs

#### LAMBDA EXPRESSIONS:
- Functions can be constructed without a name by using lambda expressions.
	λx -> x + x
- Note:
	- the symbol **λ** is the greek letter lambda and is typed as a backslash
	- in math, nameless functions are usually denoted as |->, as in x |-> x + x


#### SECTIONS:
- An operator written between two arguments can be converted into a curried function by using parenthesis as such:
	1 + 2
	or 
	(+) 1 2

