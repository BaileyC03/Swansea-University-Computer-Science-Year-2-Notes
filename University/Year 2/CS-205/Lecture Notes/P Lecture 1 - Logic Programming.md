Declarative programming focuses on what a function should do, not how it does it.
Usually based on mathematical functions
#### 3 Basic Construct in Prolog:
1. Facts
	1. woman(mia). <- this is a fact
2. Rules
3. Queries
	1. ? - woman(mia). *and* ? - woman(X) <- These are queries
		1. The uppercase X is a variable in prolog, this one returns all variables of X that satisfies the predicate.

	:- <- This is an "if"
	playsAirGuitar(mia) :- listensToMusic(mia)
	**note:** - This is a 2 way relation, if this then that and vice versa.
	**note:** - All words starting with an uppercase letter are variables.

- A collection of facts and rules is known as a knowledge base.


#### Prolog Syntax:
- Atoms:
	- Sequence of characters of uppercase letters, lowercase letters, digits or underscores.
	- An arbitrary sequence of characters enclosed in single quotes
	- A sequence of special characters

- Numbers:
	- Integers: -10, 10, 34 22342
	- Floats: 3456.2234, 585.42

- Variables: 
	- A sequence of characters of upper and lower case, underscore or digits starting with either a capital letter or underscore.

- Terms - Basic data structure in Prolog
	- Terms are defined inductively from:
		- Basic terms (Atoms, numbers and Variables) or
		- A functor applied directly to a sequence of terms like man(bill) or father(father(bill)).
			- The functors must be an atom
			- The Arity of a functor f is the number of arguments
			- An n-ary functor is denoted f/n (Usually used when a predicate)
	Terms are very flexible data structures and are essentially flat representations of trees.
