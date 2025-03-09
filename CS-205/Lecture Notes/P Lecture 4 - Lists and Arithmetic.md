	#### LISTS IN PROLOG:
- Definition: A list is a finite sequence of elements.
- Examples:
	- [mia, vincent, jules, yolanda]
	- [mia, robber(honeybunny), X, 2, mia]
	- [] (an empty list)
	- [ [ ],dead(z), [2,[2,B]] ]
- Head - the first element of a list
- Tail - the remaining elements of the list (all but the head)

#### THE BUILT-IN OPERATOR |
- Prolog has a special built-in operator | which can be used to decompose a list into its head and tail.
- The | operator is vital for making predicates revolving around prolog list manipulation.
	?- [Head | Tail] = [mia, vincent, jules, yolanda]
	Head = mia
	Tail = [vincent, jules, yolanda]
	yes

#### THE MEMBER PREDICATE:
- We need to know if an element is a member of a list 
- We can create a predicate in which, when given a term X and list L, tells us if X is within L.
- Usually itll be known as member/2 
			