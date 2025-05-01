## CHAPTER 1:
**FEATURES OF HASKELL:**
- Concise programs
	- Usually 2-10x shorter line-wise than other languages. 
	- This is because it is specialised for a few use cases, and so has few keywords.
- Powerful Type System
	- A better type system than many other languages
	- Automatic polymorphism and overloading in some situations
- List Comprehensions
	- List-based functions can be carried out without recursion 
- Recursive Functions
	- Haskell loops through recursion
	- Recursive functions - Functions which are defined in terms of themselves
- High-Order functions
	- Functions can take functions as arguments and return functions as results.
	- this means you can have a function that is actually 2 functions slapped together
- Effectful Functions
	- Functions in Haskell are pure functions that take all their inputs as arguments and produce all their outputs as results
	- Many programs have a "side effect" that also happens during the function's runtime. 
		- Haskell allows this, without compromising purity, via the use of monads and applicatives
- Generic Functions
	- Most languages allow generic functions which take in a range of simple types. 
	- Haskell generics are able to take in much more. Any type that is either:
			- Functorial
			- Applicative
			- Monadic
			- Foldable
			- Traversable
- Lazy Evaluation
	- Haskell programs use "lazy evaluation"
		- No computation should be performed until the result is actually needed
- Equational Reasoning
	- Haskell programs are pure functions. 
		- This means equational reasioning techniques can be used to execute, transform or prove given properties of said program.
		- You can also calculate the entire program from the specifications and the intended behaviour mathematically
			- This can be used alongside induction to reason about recursive functions

**CHAPTER 1 EXERCISES**
- Give another possible calculation for the result of double (double 2)
	- double(2) + double(2)
	- (2+2) + double (2)
	- (2 + 2) + (2 + 2)
	- (4) + (2+2)
	- 4+4
	- 8
- Show that sum[x] = x for any number x
	- sum[] = 0
	- Sum[l : ln] = l + sum[ln]
	- sum [x] = sum[x:]
	- sum[x] = x + sum[]
	- sum[x] = x + 0
	- = x
- How should the definition of the function qsort be modified so that it produces a rverse sorted function of a list?
	- Change smaller and larger to be the other ways around
	- qsort larger ++ [x] ++ qsort smaller
- What would the effect of replacing <= with < be on the qsort algorithm?
	- The equal numbers would not be sorted into a list and would cause issues
## CHAPTER 2:
**STANDARD PRELUDE:**
 - Haskell has some built-in functions in a library file known as the standard prelude
 - It has functions like +, -, / etc and also a lot of list functions
 - Lists are defined in haskell by [] 
 - Some common library functions:
	 - Select the first element of a non-empty list:
		 - head [1,2,3,4,5]
	- Remove the first element from a non empty list
		- tail[1,2,3,4,5]
	- Select the nth element of a list (index from 0)
		- [1,2,3,4,5] !! 2 
	- Select the first n elements of a list:
		- take 3 [1,2,3,4,5]
	- Remove the first n elements of a list:
		- drop 3 [1,2,3,4,5]
	- Calculate the length of a list:
		- length[1,2,3,4,5]
	- Calculate the sum of a list of numbers:
		- sum[1,2,3,4,5]
	- Calculate the product of a list of numbers:
		- product[1,2,3,4,5]
	- Append 2 lists: 
		- [1,2,3,4,5] ++ [6,7,8]
	- Reverse a list: 
		- reverse[1,2,3,4,5
		- ]
**FUNCTION APPLICATION:**
	- In math, function application words by denoting the arguments in () while multiplication is denoted silently, such as - f(a,b) + cd
		- In haskell, this would be f a b + c * d
	- Function application has higher priority than any other operator.  a + b is (f a)+b

| Math       | Haskell   |
| ---------- | --------- |
| f(x)       | f x       |
| f (x,y)    | f x y     |
| f (g(x))   | f (g x)   |
| f (x,g(y)) | f x (g y) |
| f(x)g(y)   | f x * g y |

**HASKELL SCRIPTS:**
	- You can also define your own functions. They're defined in a script.
		- Script: text file with a sequence of definitions
		- Haskell scripts usually end in .hs
	- Its worth having 2 windows open when developing in haskell
		- One with text editor
		- One with the GHCi
	 - If you update the .hs file, you must do :reload in the GHCi in order to execute any new definitions. All of the below must begin with a colon (:)
		- load name
			- load script name
		- reload
			- reload current script
		- set editor name
			- set editor to name
		- edit name
			- edit script name
		- edit
			- edit current script
		- type expr
			- show type of expression
		- ?
			- Show all commands
		- quit
			- quit GHCI

**NAMING REQUIREMENTS:**
	- When defining a new function, the names of the functions and arguments must begin with lowercase letters. Anything after that (letters, numbers) are optional and can be caps. The following cannot be used however:
		- case
		- class
		- data
		- default
		- deriving
		- do 
		- else
		- foreign
		- if
		- import
		- in
		- infix
		- infixl 
		- infixr
		- instance
		- let 
		- module 
		- newtype
		- of
		- then
		- type
		- where
	- Arguments in haskell will have the suffix (s) on their name to indicate they may take multiple values. Dimensionality of a list may be denoted by the number of suffix S
		- css (2 dimensonal list)
		- Within a script, each definition within the same level must begin in the same column. This allows it to be possible to determine definitions' grouping by their indentation level.
			- Eg:
				- a = b + c
					- where
					- b = 1
					- c = 2
				- d = a * 2
**COMMENTS:**
- Scripts can also contain comments. Comments can be done like so:
	- -- This is a comment
	- {-
		this is a multi line comment
		-}
## CHAPTER 3:
**BASIC CONCEPTS:**
 - A type is a collection of related values (bool, int, float)
 - Bool has 3 values (True, False)
 - Bool -> Bool contains all functions that map arguments from Bool to results from Bool
	 - Such as "not" as a function
	- We use the notation v :: T to say that v is a value of type T
		- E.g: False :: Bool
		- E.g: True :: Bool
		- E.g: Not :: Bool -> Bool
	- It can also be used to describe the type that will be returned from an expression such as: 
		- not False :: Bool
	- In Haskell, every expression must have a type which is calculated prior to evaluating the expression.
		- This is done by something called type interference.
		- If f is a function that maps types A to results of type B. If e is of type a, then f e is type B 
	- Haskell Programs are type safe, meaning type errors can never occur during evaluation. 
		- In practice, haskell detects a very large class of program errors due to type interference
**BASIC TYPES:**
- Haskell provides a number of basic types, there are the main ones: 
	- Bool - Logical values
		- True, False
	- Char - Single Characters
		- All single characters in the unicode system
		- Alongside some things such as \n and \t 
		- Must be in single quotes
	- String - String of characters
		- Contains all of the sequences of characters. Strings must be in double quotes.
	- Int - Fixed precision integers
		- Type contains integers (-100, 1, 0, 999).
		- - 2^63 to 2^63
	- Integer - Arbitrary precision integers:
		- Type contains all integers, with as much memory as necessary being used for their storage. No limits on how large or small you can go. These are usually processed slower as most computers have native support for "Int" but not these
	- Float - Single precision floating point numbers
		- Numbers with a decimal point
	- Double - double precision floating point numbers
		- Similar to float, but has 2x as much data available to increase precision.
**LIST TYPES:**
-  A list is a sequence of elements of the same type, with the elements being enclosed in square brackets - []. We write [T] for the type of all lists whose elements have type T.
	- [False, True, False] :: [Bool]
	- ['a','b','c','d',] :: [Char]
- Due to lazy evaluation, lists can be infinitely sized and that is both natural and practical :)

**TUPLE TYPES:**
- A tuple is a finite sequence of components of possibly different types, held in brackets ()
- We write (T1, T2, T3) to define their types:
	- (False, True) :: (Bool, Bool)
	- (False, 1, True) :: (Bool, Int, Bool)
- The number of components in a tuple is known as its arity (Note: This is not a typo, its actually arity, not parity or some other shit.) 
	- Arity 0 - The empty tuple
	- Arity 2 - Pairs
	- Arity 3 - Triples
	- etc etc
- Tuples of arity 1 are not allowed as they conflict with the use of parenthesis to define the evaluation order (1+3)*2
- The type of a tuple conveys its arity
	- (Bool,Char) contains all pairs comprising a Bool 1st component, Char 2nd
	- No limit to what can be a component of a tuple. you can have tuples of tuples, tuples of lists, lists of turples yaddah yaddah 
	Tuples must have a finite arity, to ensure they can always be inferred prior to evaluation

**FUNCTION TYPES:**
- A function is a mapping from arguments of one type to results of another type. 
	- We write T1 -> T2 for the type of all functions that map arguments of type T1 to T2
	- not :: Bool -> Bool
	- even :: Int -> Bool
	- add :: (int, int) -> int
-  No restriction that functions must be (total) on their argument type
	- Some arguments, a result may not be defined (e.g: "head" on an empty list)

**CURRIED FUNCTIONS:** (REVISE ME)
- Functions with multiple arguments may also be handled in another, less obvious way
	- Instead of taking them both at the same time, take them one at a time.
			- (There is a thought process here in which every function only takes in 1 argument may return just another function or an end result) - This is the case in Haskell)
				- Personal note. This almost "2 dimensional typing" is because we only refer to the function f on its first argument. It returns a function (denoted in brackets sometimes) and takes an argument.
	- exploiting the fact that functions may return a function as a result
	Observe:
		add' :: Int -> (Int -> Int)
		add' x y = x+y
			- This type states that add' is a function that takes an argument of type Int and returns a result that is a fuction of type Int -> Int. The definition itself states that add' produces the same final result as last add but takes its two arguments one at a time
			 ![[Pasted image 20240820211251.png]]

**POLYMORPHIC TYPES:**
- Library function length calculates the length of a list regardless of size. 
	- To work on any type, use a type variable like so:
		- length :: [a] -> int
			- a must be lowercase and are usually named a,b,c
	- A type that contains 1 or more variables is considered polymorphic
	- 
**OVERLOADED TYPES:**
- + calculates the sum of any 2 numbers.
- The idea that this can be applied to any numeric type is made precise in its type by a class constraint
		- Class constraints are written C a where C is the class and a is the type variable. 
		- (+) :: Num a => a -> (a -> a)
			- for any type a that is an instance of class Num, the function (+) has type a-> a-> a
				- Putting a function in parenthesis curries it, seen in chapter 4.
			- A type that contains one or more class constraints is considered to be overloaded
			- Numbers themselves are overloaded
		
**BASIC CLASSES:**
- A type is a collection of related values.
- A class is a collection of types that support overloaded operations (known as methods)
	- Haskell provides some basic classes which are built into the language. Basic ones:
		- Eq - Equality Types:
			- Types that can be compared for equality and inequality (== or \=)
			- Bool, Char, String, Int, Integer, Float, Double, list, tuples are all Eq
			
		- Ord - Ordered types
			- Contains types that are within equality types, but also those whos values are (linearly) ordered and can be compared with < , <=
				- Bool, Char, String, Int, Integer, Float, Double, list and tuple (assuming their elements are also elements)
				
		- Show - Showable types
			- Class contains values which can be turned into strings of characters using the following method:
				- show :: a -> String
				- Bool, Char, String, Int, Integer, Float, Double are all instances of such
				- Lists and tuples also are, assuming their elements are also showable types
				
		- Read - Readable types
			- Class is types whos values can be converted FROM strings:
				- show :: String -> a
				- Bool, Char, String, Int, Integer, Float, Double are all instances of such
				 Lists and tuples also are, assuming their elements are also showable types
				 - read "[1,2,3]" :: [Int]
					 [1,2,3]
					^ The use of :: i this resolves the type of the result which could not be infered y the interpreter. 
			
		- Num - Numeric Types
			- Types whos values are numerc and can be processed with +,-,*, negate,abs
			- Note: negative numbers must be parenthesised when used as arguments to functions.
			
		- Integral - Integral Types
			- Class contains instances of numeric class num, but who are also integers and support integer division and integer remaintder:
				- div :: a -> a -> a
					- aka div :: a -> (a -> a)
				- mod :: a -> a -> a
			- Integer and Int are integral types
			
		- Fractional - Fractional types
			- Contains types of numeric class Num, but also those who are non-integral
				- They will therefore support the methods of fractional division and reciprocation
				- (/) :: a -> (a -> a)
				- recip :: a -> a
			- Types Float and Double are fractional types

**CHAPTER 3 EXERCISES:**
1..
['a','b','c'] :: [Char]
('a','b','c',) :: (Char)
[(False, 'O'), (True,'1')] :: [(Bool, Char)]
([False, True], ['0','1']) :: ([Bool],[Char])
2.
A definition wiith the type bools :: [Bool]



## CHAPTER 4:
**DEFINING FUNCTIONS:**
- New From old
	- Combining 1 or more existing functions
	- E.G. "even" is using the mod function
- Conditional Expressions
	- Haskell lets you define functions which choose from a number of possivle results
		- Known as conditional expressions. They use a condition (logical expression ><) to choose between 2 results of the same type. If true, one is chosen, if false the other. 
		- abs, for example:
			- abs :: Int -> Int
			- abs n = if n >= 0 then n else -n
	- Conditional expressions may be nested (they can contain other conditional expressions)
	- Conditional expressions in Haskell must ALWAYS have an "else" branch to avoid the "dangling else" problem.
- Guarded Equations
	- An alternative to conditional expressions.
	- A sequence of logical expressions (AKA Guards) choose between the two potential outputs. It looks like so:
		- abs n | n >= 0 = n
			-   | otherwise = -n
	- The | is read as "such that" like in CS170 
	- Otherwise in his case is not mandatory but is good practice and helps handle all cases.
	- Guarded equations are better than conditional expressions when you have an expression with multiple guards as its easier to read.
	
**PATTERN MATCHING:**
- Many functions have a simple and intuitive definition using pattern matching
	- A sequence of syntactic expressions (patterns) chooses from a sequence of results of same type. 
	- Consider it like "If this, then that"
	- If the first pattern is "matched", the first result is chosen etc etc... 2nd 3rd etc
	- E.G. ;
		- not :: Bool -> Bool
		- not False = True
		- not True = False
	- Functions with 1+ argument can also be defined via pattern matching where, in each case, the patterns are matched in order for each equation. E.G: 
		- ![[Pasted image 20240821130615.png]]
		- which can be simplified by turning the last 3 equations into
		- _ && _ = False
			- This uses the wildcard pattern of \_, which matches any value
			- This also is beneficial as (due to lazy evaluation), it knows if the first argument is "False", it will always be "False" as an output.

**TUPLE PATTERNS:** (Revise)
- A pattern which matches any tuple of the same arity whos components match the corresponding patterns in order. 
- E.G: 
	- fst :: (a,b) -> a
	- fst(x,\_) = x

**LIST PATTERNS:** (Revise)
- Similarly a list of patterns is itself a pattern
	- Matches any list of the same length whose elements match the corresponding patterns in order.
-  E.G: Tests if a list contains 3 characters, the first being "a"
	- test :: [Char] -> Bool
	- test ['a',_,_] = True
	- test \_ = False
- Lists in Haskell are actually not primitive types and are created via the cons operator
-  cons constructs a new list by prepending the new element to the start of an an existing list.
- [1,2,3] is just a shortened way of expressing:
	- 1 : (2 : (3 : []))
- Each element is prepended (added to front)
- Cons can also be used to construct patterns which match non-empty lists whos first + remaining elements all match corresponding patterns.

**LAMBDA EXPRESSIONS:**
- Alternative to functions using equations, functions can also be expressed via lambda expressions
	- Compromise a pattern for each of the arguments.
		- Body - Specifies how the result can be calculated in terms of its arguments
		- Does not give a name for thee function. They are nameless / anonymous
		- E.G: nameless function that takes x as its argument and doubles it
			-  \\\\x ->  x + x
			- The symbol \\represents lambda. Functions without a name can be used the same way as any other function.
				- (\\\x -> x + x) 2
				-  4
			- Lambda expressions can be used to formalise the meaning of a curried function. E.G: 
				- add :: Int -> Int -> Int 
				- add x y = x + y
			- can be understood as
				- add :: Int -> Int -> Int
				- add x y = add \\x -> (\y -> x + y)

**OPERATOR SECTIONS:**
- Functions like + which are between 2 arguments are called operators
- You can turn any function into an operator by surronding it in \`backquotes\`
- You can do the same to turn any operator into a function by surrounding it in ()
	- E.G> :
		- (+) 2 3 
		- 5
- (+) is the addition function
- (1+) is the successor function
- (1/) is the reciprocation function
- (\*2) is the doubling function
- (/2) is the halving function

**CHAPTER 4 EXERCISES:**

## CHAPTER 5:
**BASIC CONCEPTS:**
- In maths,  the comprehension notation can be used to contruct sets from existing sets.. E.G:
	- {x^2 | x (is a member of) {1..5}} (which is the set {1,4,9,16,25}).
- In haskell, it is done like so:
	- [x^2 | x <- [1..5]]
		- | is "Such that"
		- <- is "Drawn from"
		- [1..5] is known as a generator
- This list comprehension can have 1 or more generators, with each generator being split by a comma:
	- [(x,y) | x <- [1,2,3], y <- [4,5]]
		- [(1,4), (1,5),(2,4),(2,5),(3,4),(3,5)] << Note the order
- By changing the order of the generators, the produced set will be in a different order
	- [(x,y), y <- [4,5], x <- [1,2,3]]
		- [(4,1),(4,2),(4,3),(5,1),(5,2),(5,3)]
- in the first example, the y components change more (4,5,4,5,4,5 vs 11,22,33) and the second example its the X components that change more (1,2,3,1,2,3 vs 444,555)
- These behaviours can be understood by considering generators later in the comprehension as more deeply nested (changing their values more frequently than the ones that come before them). 
- Later generators may also rely on previous generators:
	- [(x,y) | x <- [1...3], y <- [x..3]]
		- [(1,1),(1,2),(1,3),(2,2),(2,3),(2,3)]
- A more practical example would be the function concat (concatenator of lists)
	- concat :: \[\[a]] -> \[a]
	- concat xss = [x | xs <- xss, x <- xs]
- The wildcard pattern ('_') is also sometimes useful in generators in order to discard an element from a list. 
-  E.G: A function that selects the first component from a list of pairs:
	- firsts :: [(a,b)] -> [a]
	- firsts ps = [x | (x,_) <- ps]

- E.G: A function that calculates the length of a given list;
	- length [a] -> Int
	- length xs = sum[1 | _  <- xs]
		- In this case, _<- xs serves as a counter to govern the right amount of 1s

**GUARDS:**
- List comprehensions can also use logic expressions (guards) to filter values produced by earlier generators.
	- If the guard is true, then the current values are retained
	- If it is false, it's discarded.
	- E.G.: A factor function to return all factors
		- factors :: Int -> [int]
		- factors n = [x | x <- [1..n], n 'mod' x == 0]
		
		- prime :: Int -> Bool
		- prime n = factors n == [1,n]
	- Note - deciding a number (like 15) is not prime doesnt need to produce all of its factors [lazy evaluation], as soon as any factor other than 1 or n is produced, false is returned.

**ZIP FUNCTION:**
- The library function "zip" produces a list by pairing successive elements from 2 lists until one or both lists are empty. 
	- First index of list 1 and first index of list 2
	- 2nd index of list 1 and 2nd index of list 2
	- etc
- This function can be useful when working with list comprehensions. 
	- E.G, if we want to define a function which returns a list of pairs of adjacent indexes like so:
		- pairs [1,2,3,4]
		- [(1,2),(2,3),(3,4)]
	- which would look like so:
		- pairs :: [a] -> [(a,a)]
		- pairs xs = zip xs (tail xs)

**STRING COMPREHENSIONS:**
- Strings can be considered as lists of characters.
- Because of this, any polymorphic function which can act on a list, can also act on a string
	- this means we can use list comprehension on strings

**CEASAR CIPHER:**
- This chapter ends with an extended programming example.
	- Imagine you must encode a letter using the caeser cipher (3 places accross)
		- "Haskell is fun" would be "kdvnhoo lv ixq"
	- generally though it can be more or less than 3, anything from 1-25 (giving 25 different ways to encode a string)
	
 **CEASAR CIPHER: ENCODING + DECODING:**
 - First, youre gonna need to use a few standard functions on characters. These can be found in a library known as Data.char (which we import like any other lang)
	 - import Data.Char
- We will only encode lower case letters for this example. Upper case and punctuation is unchanged. We must first define a function which will turn the characters a-z into integers 0-25.
	- let2int :: Char -> Int
	- let2int c = ord c - ord 'a'

	- int2let :: Int -> Char
	- int2let n = chr (ord 'a' + n)
- These two functions let you define a new function to shift lower case letters into numbers, adding x (x being the spaces you want to shift them) and then converting it back into numbers again.
	- shiftletter :: Int -> Char -> Char -- shifts individual letters
	- shiftletter n c | isLower c = int2char((char2int c + n `mod` 26))
				 | otherwise = c
- Finally, you can perform shiftletter functions on each char in the string
	- encode :: Int -> String -> String
	- encode n xs = [shiftletter n x | x <- xs]

**CEASAR CIPHER: FREQUENCY TABLES:**
- The key to cracking a ceasar cipher is by noting that some letters in the english alphabet are used more frequently than others. If you analyse a latge amount of text, you can get a table like the one below with approximate percentage frequencies of the letters of the alphabet:
	- table :: [Float]
	- table = [8.1, 1.5, 2.8, 4.2, 12.7, 2.2, 2.0, 6.1, 7.0, 0.2, 0.8, 4.0, 2.4, 6.7, 7.5, 1.9, 0.1, 6.0, 6.3, 9.0, 2.8, 1.0, 2.4, 0.2, 2.0, 0.1]
		- Here, 'e' s the most common (12.7) while 'q' and 'z' are least (0.1)
- Its also worth making a frequency table for any individual string. 
	- First you need to mae a function which calculates the % of a given integer vs another.
		- percent :: Int -> Int -> float
		- percent n m = (fromIntegral n / fromIntegral m) * 100
			- note - fromintegral converts an integer into a floating point number
	- Now you have a percent, you can use a list comprehension alongside the functions 'lowers' and 'count' to define a function which returns a frequency table for any given string: 
		- freqs :: String -> [Float]
		- freqs xs = [percent (count x xs) n | x <- ['a'..'z']]
				- where n = lowers xs

**CESAR CIPHER: CRACKING THE CIPHER:
- A standard method to compare the list of observed frequencies with a list of expected frequencies is via chi-square.
	- ![[Pasted image 20240822210603.png]]
- here, Oi is the observed value and Ei is the expected value. The smaller the value, the better the match between the two frequency lists. 
- using the "zip" function previously mentined alongside list comprehension we can turn the formula into a function definition:
	- chisqr :: [Float] -> [Float] -> [Float]
	- chisqr os es = sum [((o-e)^2)/e | (o,e) <- zip os es]

- Now we need a function which rotates a given element of a list "n" places to the left, and wrapping around to the start of the list. Assume the integer (n) is between 1 and the length of the list.
	- rotate :: Int -> [a] -> [a]
	- rotate n xs = drop n xs ++ take n xs

- Now lets say we are given an encoded string, we can do this by:
	- Producing the frequency table of the encoded string
	- Calculating the chi squared of each possible rotation of the table compared to the expected frequencies listed above
	- The lowest number is most likely the right answer.
- this can be achieved by one final function:
	- crack :: String -> String
	- crack xs = encode(-factor) xs
	- where
		- factor = head (positions (minimum chitab) chitab)
		- chitab = [chisqr (rotate n table') table | n <- [0..25]]
		- table' = freqs xs
## CHAPTER 6:

