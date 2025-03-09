#### TYPE DECLARATIONS:
- In Haskell, a new name for an existing type can be defined using type declaration.
	type String = [Char]
- Type Declarations can also be used to make other types easier to read. For example:
	type Pos = (Int, Int)
	- we can define
	origin :: Pos
	origin = (0,0)
	 
	left :: Pos -> Pos
	left (x,y) = (x-1,y)

- Like function definitions, type declarations can also have parameters. E.G: 
	type Pair a = (a,a)
- from the one above, we can define:
	mult :: Pair Int -> Int
	mult (m,n) = m*n
	 
	copy :: a -> Pair a
	copy x = (x,x)

- Type declarations can be nested
	type Pos = (Int, Int)
	type Trans  = Pos -> Pos

- But cannot be recursive
	type Tree = (Int, [Tree]) <- THIS WONT WORK


#### DATA DECLARATIONS:
- Completely new types can be defined by specifying its values via a data declaration.
	data Bool = False | True
- False and True are considered constructors for type Bool
- Constructor and Type names must be uppercase starts
	data Answer = Yes | No | Unknown
- or
	data Shape = Circle Float
				| Rect Float Float
- which allows us to define:
	square :: Float -> Shape
	square n = Rect n n 
	
	area :: Shape -> Float
	area (Circle r) = pi * r^2
	area (Rect x y) = x * y

#### RECURSIVE TYPES:
- New types can be declared in terms of themselves.
	data Nat = Zero | Succ Nat
- A value of type Nat is either Zero (a Nat) or a form succ n where n is a Nat
- Therefore nat contains an infinite sequence of values like:
	- Zero (0)
	- Succ Zero (1)
	- Succ (Succ Zero) (2)
	- Succ (Succ(Succ Zero)) (3)
	- ...
- Converting between Nat and Int:
	nat2int :: Nat -> Int
	nat2int Zero = 0
	nat2int (Succ n) = 1 + nat2int n
	.
	int2nat :: Int -> Nat
	int2nat 0 = Zero
	nat2int n = Succ(int2nat (n-1)

#### ARITHMETIC EXPRESSIONS:
- Consider a simple form of expressions build up from integers using addition and multiplication:
![[Pasted image 20241218151847.png]]
- Using recursion, a suitable new type to represent such expressions can be declared by:
	data Expr = Val Int
		| Add Expr Expr
		| Mul Expr Expr
- For example the above tree would be:
	Add(Val 1) (Mul(Val 2) (Val 3))
- Using recursion, it is now easy to define functions that process expressions like so:
	size :: Expr -> Int
	size (Val n) = 1
	size (Add x y) = size x + size y
	size (Mul x y) = size x + size y
	.
	eval :: Expr -> Int
	eval (Val n) = n
	eval (Add x y) = eval x + eval y
	eval (Mul x y) = eval x * eval y
- Please note the 3 constructors have different types:
	- Val :: Int -> Expr
	- Add :: Expr -> Expr -> Expr
	- Mul :: Expr -> Expr -> Expr

#### BINARY TREES
- In computing, a useful way of storing data is in a two way branching structure known as a binary tree
![[Pasted image 20241218154301.png]]
- Using recursion, we can create a new type to represent binary trees like so:
	data Tree = Leaf Int
			| Node Tree Int Tree
- E.G, the previous diagram would be represented as such:
	Node (Node(Leaf 1) 3 (Leaf 4))
	5
	Node (Node (Leaf 6) 7 (Leaf 9))

- From the above, we are also able to define if a given integer occurs in a binary tree.
	occurs :: Int -> Tree -> Bool
	occurs m (leaf n) = m == n
	occurs m (node l n r) = m == n
					| occurs m l
					| occurs m r
	- The worst case of this is that it checks the entire tree without finding the integer.

#### SEARCH TREES:
- Consider the function "Flatten".  It returns all the integers contained in a tree.
	flatten :: Tree -> [Int]
	flatten (Leaf n) = [n]
	flatten (Node l n r) = flatten l ++ [n] ++ flatten r
- A tree is a search tree if, when flattened, it flattens to an ordered list.
- Search trees have the important property that when youre looking to find a value in a tree, youre able to know which subtree to check. (Think binary search).
	occurs m (leaf n) = m == n
	occurs m (node l n r) | m == n = True
					| m < n = occurs m l
					| m > n = occurs m r
- This definition is WAY more efficient as it only traverses the one path of the tree.