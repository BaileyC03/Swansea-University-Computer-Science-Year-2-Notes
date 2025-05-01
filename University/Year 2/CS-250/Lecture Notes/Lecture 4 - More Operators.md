### 4 NEW OPERATIONS!
- These are actually made up of combinations of the 6 previous fundamental operators
	- They are considered their own operators however to save time.
	- A.K.A: Shortcuts

1. Natural Join
	- Cartesian Product can introduce nonsense doubles
	- This is different to cartesian product.
	- Denoted by a ⋈ sign. (T1 ⋈ T2)
	- The output, T' is formed by:
		- Taking the cartesian product
		- Selecting all tuples in which the same attributes have the same value (e.g. both pid the same)
		- Projecting it to make it a set, meaning all duplicate attributes are removed.
	- If no tuples match on their duplicate attriubutes, the output is an empty table
	- If there are no common attributes, the result is the same as cartesian product

2. Intersection:
	- In order for this to work, the operands must have the same schema.
	- T1 **∩** T2 = T1 - (T1 - T2)
	- Basically returning only the overlap of a venn diagram

3. Division:
	- T1 ÷ T2
	- T2 MUST be a subset of T1
	- Essentially, you return all attribute values of T1 which, themselves, have tuples containing all tuples of T2 [If you dont get it look this up visually, visualisation helps]
	- If you see "all" - consider division
![[Pasted image 20241017134238.png]]