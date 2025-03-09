-- Remember! Behavioural = what happens at runtime
^ this is one of the most marked down reasons, forgetting this meaning

#### Sad Truth:
Understanding every line of code is unreasonable

#### Fortunately:
We dont have to, we just need to know how to interact with classes / interfaces
- We divide our code into parts
	- This makes your code modular for debugging and readability too
- Specify how they work

#### Design -> After requirements
- How software fulfills requirements
- We deal with the functions and the composition for design
- Strongly related to mathematical functions

ADTs - AbstractData Types: 
- Specify data to be stored (not actual data, but what "type" we store and how)
- the operations we can perform on that data
- Abstract implementation details
- Sometimes this is  a collection of classes
	- AKA subsystem

Object Oriented Design:
- What data is stored (Attributes)
- What operations (Methods)
- Group of methods for object (Behaviour)

### AVOID DUPLICATION OF DATA AT ALL COSTS

Approach:
- Determine your system requirements precisely
- Identity Classes needed
- Identify responsibility of the class
	- Attributes and methods

Encapsulation: The grouping of data and operations together to hide the details from the rest of the system.

Class diagrams specify the structure of a class
- Not how it works


- Look to minimise the public interfact as much as possible
- Static methods and attributes should be underlined in UML
- Use associations to represent class relationships
- Most of the work in software development is in the design :LiSmile:
