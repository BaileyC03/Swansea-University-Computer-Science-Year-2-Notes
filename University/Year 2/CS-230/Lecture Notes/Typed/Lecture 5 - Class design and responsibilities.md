In design, don't lump things together.
A class / Object helps you structure your programs and lets you abstract:
- The inner workings
- into a single item

A class is:
- A description of values that can be stored and operations on those values

An instance of a class is:
- An actual piece of memory with concrete values that can be modified
- Operations that work on those instance

Public - Accessible outside of class
Private - Accessible only inside this class
Static - Acting on the class, not the object [no instances needed]
Constructors - Ensures all instances of the class will be valid

#### When do we create a class?

Responsibilities of a class:
- Knowledge maintained by object attributes (variables)
- Actions a class can perform (behaviours and operations)
- Should represent one purpose of the class in the system
- Provides services to the system
- 2 Rough ideas:
	- Information object that store info and allow little manipulation
	- Action objects perform operations on client's code
		- Realistically real classes will be somewhere inbetween
- **All data should be private! (except very few exceptions)** - will lose marks otherwise
- Only public services count
- this isnt about security, it's about abstraction
- What it does, not how ^
- Examine **nouns** in requirements spec. This implies it may be a class
	- or part of one
- Verbs imply behaviours which may turn into methods
- Also walk-through systems.
- Identified responsibilities must be assigned to classes
- Examine context in which responsibility was identified
	- Use requirements spec and class definitions
- Some assignments will be obvious however some need thought
	- State responsibbilities as generall as you can
	- Keep info about one thing in one place (no duplicates)
	- Keep behaviour  with related information
	- Use enums to enforce values as much as you can tbh
- Each class should have 1 main purpose, 1 idea and 1 main responsibility
- **NAMES ARE CRITICAL**
- If many classes have few responsibilities, you may be able to combine them.
	- DONT FEEL OBLIGED TO DO THIS HOWEVER
- Create a new class to take responsibility of managing the information

- Some responsibilities need to be shared between 2+ classes, known as compound responsibilities.
	- Relationships between classes:
		- Composition or aggregation relationships
		- Hierarchical relationships

CRC - Class Responsibility Cards [NEEDED FOR A1] <- Look this up and consider it for our week 1
- Help with the design of classes and theircollaborations
- Responsibilities 
	- Attributes and behaviours / operators for this class
- Collaborators
	- Other classes that it needs to work with


Thought Process:
- Think about what data and operations belong together
	- These are candidate classes
- Draw up CRC cards for these
- Think and reflect on it
	- Too much responsibility on one class? consider dividing it
- When settled, begin a UML design.