#### THE CUT:
- Backtracking is a feature of Prolog
- Backtracking can make things inefficient however
	- Prolog can inefficiently waste time exploring paths that may lead to nowhere.
- WE CAN HAVE CONTROL! (:o wow)
	- the cut predicate !/0 lets us control backtracking

#### CUT in Practice:
- The cut is a predicate, so we can add it to the rules of the body
- e.G:
	p(X) :- b(X), c(X), !, d(X), e(X).
- cut is a goal that ALWAYS succeeds.
- Ensures prolog can pick from the choices offered BEFORE the parent goal was called.

#### GREEN CUTS:
- Cuts that don't change the meaning of a predicate are known as green cuts..
	- This essentially just makes the code more efficient 

#### RED CUTS:
- Cuts that DO change the meaning of a predicate are known as red cuts.
- Programs containing red cuts are:
	- Not fully declarative
	- Hard to read
	- able to lead to subtle programming mistakes