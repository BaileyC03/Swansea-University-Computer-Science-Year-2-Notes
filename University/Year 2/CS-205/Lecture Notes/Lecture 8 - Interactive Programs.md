#### INTRODUCTION:
- Haskell traditionally does not let us use keyboard input / have output as haskell is side effect free. 
- We can, however, get around this by using types to distinguish pure expressions from impure **ACTIONS** that may have side effects.
	IO a  <- The type of actions that return a value of type a
- E.G:
	IO Char <- Returns a character
	IO () <- This is just side effecting actions without a return value. A tuple with no components.

#### BASIC ACTIONS:
- The standard library provides a number of actions - including the three primitives:
	- getChar - reads a character from the keyboard, echoes it and returns the char as its return value.
		- getChar :: IO Char
	
	- putChar c - writes the character c to the screen, and returns no result value.
		- putChar :: Char -> IO()

	- return v - returns the value v without any interaction
		- return :: a -> IO a

#### SEQUENCING:
- A sequence of actions can be combined as a single, composite action using combinator
	(>>=) :: IO a -> (a -> IO b) -> IO b
	- Aka perform an action, take a result and perform another.
	- E.G:
		main = getChar >>= putChar
	- Or, if you dont care about the result of your first computation:
		(>>=) :: IO a -> IO b -> IO b
		a >> b = a >>= \_ -> b

#### COMPILING AND RUNNING:
- E.G:
	main :: IO()
	main = getChar >>= \c ->
		putChar (toUpper c) >> 
		putChar '\n'
- main :: IO() will be the entry point
- "ghc fileName.hs -o program" tocompile and produce the executable "program".

#### SEQUENCING 2
- Syntactic Sugar - the  do notation
- E.g: 
	main :: IO()
	main = do {
			x <- getChar ;
			putChar (toUpper x) ; 
			putChar '\n'
			}

#### DERIVED PRIMITIVES
- Reading a string from a keyboard:
	getLine :: IO String
	getLine = do {
				x <- getChar ;
					if x = '\n'
					then return []
					else do{
							xs <- getLine ; 
							return (x:xs)
						 }
				}

- Writing a string to the screen:
	putStr :: String -> IO()
	putStr[] = return ()
	putStr(x:xs) = do { putChar x; 
					putStr xs }

- Writing a string and moving to a new line:
	putStrLn :: String -> IO ()
	putStrLn xs  = do { putStr xs ;
					putChar '\n' }

- We can now define a function that prompts for a string to be entered and displays its length:
		strlen :: IO()
		strlen :: do {
				putStr "Enter a string: " ;
				xs <- getLine ;
				PutStr "The string has " ;
				putStr (show(length xs)) ;
				putStr " characters."
		  			}
- Note: Evaluating an action executes its side effects, with the final result being discarded.
