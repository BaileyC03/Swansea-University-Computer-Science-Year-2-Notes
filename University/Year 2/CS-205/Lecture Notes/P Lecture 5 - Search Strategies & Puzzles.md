#### SEARCH STRATEGIES:
- One of prolog's notable features is it's built-in search mechanism.
	- In the best-case, it means its able to specify a problem by a list of program clauses. Prolog will then automatically search for solutions and find them if they exist.

- In many cases, the search can be split into 2 phases:
	- Generating Phase - one specifies the potential solutions in such a way that Prolog will find or generate all potential solutions
	- Testing Phrase - where the potential solutions are tested to check if theyre actually solutions. (this involves the arithmetic)


#### DECLARATIVE VS PROCEDURAL PROGRAMS:
- In a purely declarative logic program, the generating phase and testing phase are separated (strictly) and somethin somethin "generate-and-test" logic program.
- These are usually short, elegant and easily understood.
	- They may be inefficient however, as too many solutions are generated - which may not be actual solutions.

- In order to obtain better efficiency, you can try to combine the two phases to remove the failed potental solutions at an early stage - limiting useless shit. These have a more procedural vibe.