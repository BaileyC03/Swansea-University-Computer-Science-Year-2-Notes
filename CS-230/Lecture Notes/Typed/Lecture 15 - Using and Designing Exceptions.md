#### EXCEPTIONS:
- Exceptions are used to model errors or bad situations
- When a bad situation is detected, an exception is created and thrown
- This stops the current execution and allows an exception handler to handle (catch) the error.
- Most library methods throw exceptions

#### HOW DO WE USE THE EXCEPTIONS:
- EASY PART: DETECTING EXCEPTIONS 
	- Write code to test variables, if an issue - throw an error
- HARD PART: HANDLING ERRORS
	- We need to catch all exceptions to resolve any problems
	- Only catch an error in a class or method in which we are able to handle it

#### WHAT HAPPENS TO THROWN EXCEPTIONS:b
- If a method throws an exception:
	- If the code is in a try block, the catch block deals with it
	- If not, the control flows down the call stack until it finds a catch block
	- If it doesnt find any catch blocks, crashes

#### WHEN TO CATCH?
- Only catch when you are in a position to handle it PROPERLY

#### THROW ERRORS EARLY, CATCH ERRORS LATE.
### DONT SQUELCH ERRORS, IMPOSSIBLE TO DEBUG
