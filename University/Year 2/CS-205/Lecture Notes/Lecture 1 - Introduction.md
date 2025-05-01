
#### Pre-course info:
- Labs are the baseline.
	- Look to recreate 270 algorithms in Haskell to really get a grasp of things.
	- Look to do the lab sessions in the lab sessions (not at home)
	- They can be signed off at the end of the session or the start of the next one.

- Grading Weights:
	- 15% - Labs
	- 15% - Coursework
	- 70% - Written Exam
		- This will cover the theory and implementation of haskell so practice is essential

- Focus on the textbook and documentation for learning.
- Also smash functions together for profit yes yes :LiSmile:
#### What Makes a programming language functional?
- Higher order functions
- Algebraic Datatypes
- Parametric Polymorphism
	- This is when a piece of code can be given a generic type. 
	- Think generics in java < T >
- Recursion, not loops
- Implicit Memory Management
- Static type inference
- Type classes
(Note this is not a definitive list, nor is it mandatory for a functional language to satisfy all of these.)

#### Haskell is strange
- A side effect is where a piece of code does literally anything *other* than reading a value in, and returning a value out. Haskell doesn't let you do side effects.
- E.G: 
	- Reading and writing to files
	- Printing to a screen
	- Changing a value in memory
- A way to get around this in Haskell is to treat the states you want to modify as inputs and output the edited state. 
- There are no mutable variables and there are no loops
- Haskell is also very strongly typed, meaning it kicks up errors a lot due to this. 
	- It also doesn't auto-cast types, in the same way Java does.
- Haskell functions are very similar to mathematical functions
	- Constrained Style
	- No loss of expressiveness due to it being recursive, and not looping
		- Expressiveness is allegedly the amount of code needed to express an abstraction - StackOverflow guy

#### Example Function Definition:
- SumofInverses :: Float -> Float -> Float
	- Float -> Float -> Float means it takes in a float and returns a function which takes in float and returns float. 
		- Its nice to consider it like so: Float -> (Float -> Float)
		- This is considered Currying. It's vital for taking in 2 inputs in Haskell as in theory each method only takes in one variable.

