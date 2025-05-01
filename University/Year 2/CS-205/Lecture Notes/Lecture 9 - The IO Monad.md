#### RECAP:
So far we have seen:
- How to write types for programs with IO side effects such as:
	- print :: Show a => a -> IO()
	- getLine :: IO String
- How to combine them using bind >>= or the **do** notation
- How to compile haskell programs using ghc

#### AN EXTENDED DO NOTATION?
- .
		doList :: [(Int, Char)]
		doList = do {
					x <- [1..5] ;
					y <- ['a','z'] ;
					return (x , y)}
![[Pasted image 20241219152616.png]]


#### HOW? THE MONAD TYPECLASS!
(>>=) :: Monad m => m a -> (a -> m b) -> m b 
return :: Monad m => a -> m a

- m :: * -> * is a variable, but not for a type.
- Monads consist of a very generic, but useful abstractions.
	- Typical instances:
		- Monad IO, Monad [], Monad Maybe. Monad (Cont r), Monad (State s)
		- Monad (State s) = code "as if" we had mutable variables.

