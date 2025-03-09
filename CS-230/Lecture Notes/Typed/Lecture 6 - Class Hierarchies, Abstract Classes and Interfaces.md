- We know about responsibilities
- Sometimes, responsibilities can be shared
	- However duplication is our enemy
- The solution? Class hierarchies! 

#### CLASS HIERARCHIES:
- Previous steps (classes, responsibilities) yield a preliminary design.
- To maximise the benefits of an OOP approach we design class hierarchies.
	- Represents essence of OOP approach
	- Provide most potential benefits
- A global view of the design can help us understand and improve the hierarchy
- Inheritance also helps us avoid repetition.

#### INHERITANCE
- "Is-a" relationship
	- A mammal is an animal
	- A bird is a(n) animal
	- A car is a vehicle
	- An aeroplane is a vehicle
- In these "is-a" relationships:
	- Animal, vehicle are superclasses
	- Mammal, bird, car, aeroplane are subclasses (specific versions of superclasses)
	- All subclasses are TYPES OF superclasses.
		- Aka. Specialisations

#### SUPERCLASS
- Provides attributes and operations common to all superclasses
- Substitution Principle
	- An instance of a subclass can be used when an instance of a superclass is expected.
	- Variables declared of a superclass type can store references to instances of subclasses
	- E.G: if we have a method calling type Animal, we can pass in a Bird or Mammal.
- Methods implement default behaviours unless overridden by subclass
- Prevents re-implementation of common functionality in subclasses

#### SUBCLASS
- A more specific type of the superclass
- Inherits the methods and attributes of the subclass
- Additional methods and attributes can be added to the subclass
- Methods in the superclass can be overridden
	- by providing methods with the exact same name and parameters

#### EXAMPLE INHERITANCE IN UML:
![[Pasted image 20250102121052.png]]
- Simply UML hierarchy of a Vehicle and Bicycle
- Bicycle can do everything a vehicle can do *and more*
	- Does not repeat inherited attributes or operations in subclasses in Class Diagram
- Hollow arrow goes from subclass to superclass
- In UML we use the words SPECIALISATION and GENERALISATION instead of inheritance

#### COMPLICATED / LARGE UML DIAGRAMS:
![[Pasted image 20250102121311.png]]
- A model can have multiple diagrams
	- Not all details must be present on each one
	- Here, we only show the hierarchy for example
	- The details however (attributes / operatios) need to be shown on other diagrams.
	- Arrows can be individual or bunched
#### ABSTRACT METHODS AND CLASSES:
- Sometimes, a method will have different implementations dependin on which subclass inherits it.
- This is hard to implement in a concrete manner.
- If you want to require this method is implemented in all subclasses however, you can make it abstract!
- If a class contains an abstract method, the whole class must be abstract.
- Abstract classes can have normal methods too

#### THE POINT OF ABSTRACT CLASSES
- The compiler will not let us instantiate abstract classes
	- Compile-time error
- All subclasses must either implement the abstract methods, or be abstract themselves.
- Classes with full implementations are known as concrete classes.
- This setup ensures concrete classes will always have the required methods
- Good practice: 
	- Abstract classes are never children of complete ones

#### ABSTRACT IN UML CLASS DIAGRAMS:
- We represent abstract class in UML by making the class name italic 
- We also represent abstract operations in UML by making the operation name italic
![[Pasted image 20250102123003.png]]

#### DESIGNING GOOD CLASS HIERARCHIES:
- Drawing out inheritance hierarchies can help identify how good it is
- Guidelines:
	- Model is-kind-of hierarchies
	- Factor common responsibilities as high as possible
		- If many classes support a responsibility, they inherit it from a common parent
	- Dont allow abstract classes to inherit from concrete ones
	- Eliminate non functional classes
- Make good use of abstract classes:
	- Likely result in simplification, design and code sharing
	- Design on abstract classes can involve speculation on future extensions and modifications
	- One shared responsibility is often enough to justify an abstract class
	- Need 2+ children (concrete) otherwise it's difficult to identify a good generic description of the responsibilities
#### HIERARCHY REFINEMENT EXAMPLE
-  design a system in which the user can use lines, elipses rectangles and groups of objects to make a drawing. 
- Here's the first example, with some issues:
![[Pasted image 20250102125956.png]]
ISSUES:
- Repeated attributes, operations

Changes:
- DrawingElement is abstract because of abstract draw operation
	- Want to enforce all operations can draw byt cant provide good concrete implementation in drawingelement
SOLUTION:
![[Pasted image 20250102131010.png]]

#### HOW TO REFINE YOUR HIERARCHY:
- Classes that add no new functionality are normally eliminated.
	- A class can have no new responsibilities but still add functionality
	- Responsibilities represent only public services
	- Responsibilities are inherited by children, but assigned to parent
	- But if a child implements the parent responsibility in a different way, then it adds functionality

#### INTERFACES:
- Sometimes inheritance isnt the play.  Sometimes you cant form inheritances as the classes arent related naturallt but you still want you enforce that classes have certain operations/
- In come Interfaces!
- These are just a bunch of public abstract method declarations.
- They cant have attributes
- Classes can implement multiple interfaces
	- Keyword: Implements
	- By a class declaring it, it implements an interface, it is stating it obeys the contract.
	- It must provide an implementation for each method in the interface

#### INTERFACES: UML EXAMPLE:
![[Pasted image 20250102135846.png]]
- Here we have an interface of teacher. It's an interface not a class indicated by the < < interface > > stuff.
- It has one operation, teach.
- There are two classes which implement the interface (dashed arrows)
- These classes MUST provide and implement the method teach

#### INHERITANCE IN JAVA:
- Keyword "Extends" is used to specify inheritence in java.
- A subclass cannoy access any private methods or attributes of Vehicle.
- Bicycle can access any of the superclass' public or protected methods and attributes
	- in UML indivated with + / # 
- If a method is overriden:
	- References to Bicycle objects use Bicycle method
	- References to Vehicle use Vehicle method
	- If a bicycle reference is stored in a variable declared to hold vehicle references, the Bicycle method is used.
	- AKA DYNAMIC METHOD DISPATCH and the SUBSTITUTION PRINCIPLE