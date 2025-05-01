#### CONDITIONAL EXPRESSIONS:
Like in most programming languages, functions can be defined through conditional expressions.
	abs :: Int -> Int
	abs  n = if n >= 0 then n 
		else - n
- Note: In haskell, conditionals must always have an else branch. This avoids ambiguity with nested conditionals.

#### GUARDED EQUATIONS:
- An alternative to conditionals. Functions can also be defined via guarded equations.
		abs n | n >= 0 = n 
			| otherwise = -n
- (imagine those 2 lines are in the same column. )

#### PATTERN MATCHING:
- Many functions have a clear definition by using pattern matching on arguments.
	not :: Bool -> Bool
	not False = True
	not True = False

- Functions can be defined in many different ways using pattern matching. For example:
	myAnd :: Bool -> Bool -> Bool (a simulated "and" gate)
	myAnd True True = True
	myAnd True False = False
	myAnd False True = False
	myAnd False False = False
- this can however be simplified to:
	myAnd True True = True
	myAnd _ _ = False

- Please note that ghci checks each case top down so if the two wildcards is at the top, it will ALWAYS return that value.
- Patterns may not repeat variables. This triggers a compilation error:
		myAnd b b = b
		myAnd _ _ = False

#### TUPLE PATTERNS
- For complex types, we can case-analyse the shape of the values. It looks like this:
	fst :: (Int, Bool) -> Int
	fst (x,y) = x
#### LIST PATTERNS:
- Every non empty list can be considered as a spam of the "cons" function ':' like so:
	- [1,2,3,4] = 1:(2:(3:(4:([]))))
	- ^ Note its always appended to an empty list in the beginning
- You can use pattern matching over lists like so:
		isEmpty :: [a] -> Bool
		isEmpty [] = True (if its being called on an empty list, return true)
		isEmpty(x : xs) = False (xs can be empty so its essentially saying if its anything added to xs it cant be empty. x cannot be empty.)


