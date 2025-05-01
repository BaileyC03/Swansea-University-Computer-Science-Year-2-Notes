#### COLLABORATIONS: 
- Collaborations represent client object request to a server object.
	- Client may now be able to fulfill its responsibility by utilising server responsibility
	- May need additional help from more than one server (i.e. other classes)
- Server provides service representing its own responsibilities
	- A collaboration is normally one way - from client to server.
- This doesnt mean the info only flows in one direction however.
	- Each collaboration addresses a server and client responsibility.
	- A client responsibility may need many collaborations.


#### COLLABORATION: AN EXAMPLE
- Lets say we have a class called Notifier which provides the ability to NotifyUser
- It wants to be abele to do this in 2 ways - via twitter and email
- Now this class cant talk to twitter or email but other classes can (TwitterSender and EmailSender)
- In this scenario, notifier is the client and TwitterSender (or the email one) are the servers
- Notifier can now fulfil its resonsibility and offer it to the world by usnng the services of Twittersender

#### FINDING COLLABORATIONS:
- Look for dependencies among responsibilities
- For each responsibility of each class:
	- Is this class capable of fulfilling the responsibility itself? What does it need?
	- From what classes can it acquire the data / functionality
	- Shared responsibilities can define collaborations
- For each class:
	- What data does this class store and services does it provide?
	- What other classes need these services and information?
	- If no interactions, can class be eliminated? Only do so after thorough walkthroughs and evaluations.

- Has-Knowledge-Of Relationship:
	- If class A has knowledge of B, usually implies a collaboration.
		- Typically A collaborates with B (Asks  for a service) though the server may also need information from the client also
- Is-Part-Of Relationship:
	- Defines a whole-part relationship between 2 classes. One class is a composite object and the other is a component.
	- Composite objects usually have responsibility for maintaining information about its components.

#### UML: CLASS DIAGRAMS : BASIC RELATIONSHIPS
![[Pasted image 20250102150402.png]]
- These are basic associations
- The model reads:
	- There are 3 classes
		- Professor
		- Book
		- Student
	- Each Professor wrote books, each student owns books
- The small black arrow tells you which way round to read the name of the association (so you know a book doesnt own students for example)

#### MULTIPLE BASIC RELATIONSHIPS:
![[Pasted image 20250102150921.png]]
- You can have multiple associations between classes
- In addition to students owning books, we can also keep track of books borrowed by students
	- Each arrow is read independently, A book need not be owned and borrowed but it could be
	- The intention is that different books are owned and borrowed but we cant specify that sadly
#### RELATIONSHIPS ARE NOT ACTIONS:
Rule of thumb: 
- Relationships represent the current state (dont use verbs)
- Verbs represent actions, behaviours that change the current state

#### UML : CLASS DIAGRAMS : MULTIPLICITIES
- We can specify the number of objects involved in the relationships using multiplicities.
![[Pasted image 20250102151626.png]]
This means:
- Each professor writes between 0 and * (many) books
- Each book is written by an unspecified number of professors
- Each book is owned by exactly 1 student
- Each student owns 1 or more books
Leaving off the multiplicity means the decision is open and is left as a design choice for the program. 
Note: Normally its hard to enforce a lower bound of anything but 0

#### UML: CLASS DIAGRAMS: NAVIGABILITY
- Associations can also show which classes know about the relationship (the direction we can navigate)
- Each end of an association can be marked:
	- Navigable (>) 
	- Not navigable (X)
	- Unspecified (absence of)
![[Pasted image 20250102151926.png]]

#### UML: CLASS DIAGRAMS: ROLES:
![[Pasted image 20250102153137.png]]
- Here it shows that the people the manager manages are known as the manager's employees.
- This is important if you want to specify the name of the attributes that will be used when translating to code.

#### OTHER COLLABORATIONS / RELATIONSHIPS BETWEEN CLASSES:
- Is-a-kind-of (Inheritance hierarchy)
- is-made-up-of / is-part-of (Aggregation)
- owns-a (Composition)

#### AGGREGATION
![[Pasted image 20250102153911.png]]
- Allows assemblies and structures to be modelled
- Shown by the unfilled diamond (-<>)
- Collar is made up of bell, belt and buckle for example

#### COMPOSITION
- Similar to aggregation
- Is shown by a filled diamond however, and it read as "owns a"
- Composition - made up of components that cannot exist independently of the parent.
![[Pasted image 20250102154038.png]]
