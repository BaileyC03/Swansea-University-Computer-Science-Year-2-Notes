#### Function Application:
- In maths, function application is denoted by parenthesis and multiplication is denoted by a space like so:
	- f(a,b) + c d
		- aka f applied to (a,b) added to c*d
- In Haskell, function application is denoted b space and multiplication is denoted by an asterisk:
	- f a b + c`*`d
- Moreover, function application is assumed to have higher priority than other operators.
	- f a + b is the same as (f a) + b

#### Haskell Scripts:
- There are functions in the standard library with Haskell.
- You can also define your own functions within a script (a text file with a bunch of definitions)
- Haskell scripts usually have a .hs ending (this isnt mandatory though)
- E.G:
	 dividefst :: [Int] -> [Int]
		dividefst xs = a : a : ys 
				where h = head xs
				ys = tail xs
				a = h `div` 2
	- Note: 'div' is in backquotes, not normal quotes. This lets you put args on either side instad of both on one side.

#### Haskell Naming Requirements: 
- Function and argument names must start with a lowercase like so:
	- myArgument
	- myargument
	- myargument_2
	- x'
- List arguments usually have an 's' at the end of their name. Like so:
	- xs
	- ns
	- nss (list of ns lists.)

#### Layout Rule:
- In a sequence of definitions, each definition *must* begin in the same column like so:
- ![[Pasted image 20241218121632.png]]
- This avoids the need for explicit grouping (which would be denoted in {} curly braces)

#### USEFUL GHCI COMMANDS:
:load name (load script of type name)
:reload (reload current script)
:edit name (edit script called 'name')
:edit (edit current script)
:type expr (return the type of the expression expr)
:? (show all commands)
:quid (quid GHCI)

#### WHAT IS A TYPE?:
- A type is a name for a collection of values. Think like datatypes in other languages.
- E.G: Type "Bool" has 2 logical values:
	- True
	- False

We can say that False has type Bool (or false is an inhabitant of bool)

#### TYPE ERRORS:
- Usually functions only work on specific types. 
- Applying a function to the wrong type returns a type error.

#### BASIC TYPES:
Bool - Logical Values
Char - Single Characters
String - List of Characters
Int - Fixed precision integers
Integer - Arbitrary precision integers
Float - Floating point numbers

#### Lists: 
A list is a sequence of values of the same type.
	[False, False, True] :: [Bool]
	['a','b','c'] :: [Char]
- Note: The type of a list doesnt specify its length 

#### TUPLES: 
A tuple is a sequence of values of DIFFERENT types.
	(False, True) :: (Bool, Bool)
	(False, 'a', True) :: (Bool, Char, Bool)
- Note: The type of a tuple does represent its size.

#### FUNCTION TYPES: 
- A function is a mapping from values of one type to values of another type.
		not :: Bool -> Bool
		isDigit :: Char -> Bool
- In General:
	- t1 -> t2 is the type of functions that map values of type t1 to values of type t2

#### CURRIED FUNCTIONS:
- Functions with multiple arguments are possible by returning functions as results. Consider it this way:
	add' :: Int -> (Int -> Int)
	add' x y = x + y
- ^ This function takes an integer x and returns a function add'x. Then, it takes the integer y and applies the function add'x to it.
- These functions that take one argument at a time are known as curried functions. MMmmm curry :o 
- Functions with >2 arguments can also be curried by returning nested functions like so;
	mult :: Int -> (Int -> (Int -> Int))
	mult x y z = x * y * z

#### USES FOR CURRYING:
- Curried functions are more flexible than usual functions on tuples as useful functions can often be made by PARTIALLY APPLYING a curried function.
- To avoid a ton of brackets, we assume some things about curried functions:
	- The arrow always associates to the right so:
		- Int -> Int -> Int ->Int is the same as
		- Int -> (Int -> (Int -> Int))
	- Functions associate to the left so:
		- mult x y z is the same as
		- ((mult x ) y ) z


#### POLYMORPHIC FUNCTIONS:
- A function is considered polymorphic ('Of many forms') if its type contains 1+ type variables. For example:
		length :: [a] -> Int

#### TYPECLASS CONSTRAINTS:
- A polymorphic function is overloaded if its type contains one or more typeclass constraints.
		sum :: Num a => [a] -> a
		(for any numeric type, it maps type [a] into type a.)
		

