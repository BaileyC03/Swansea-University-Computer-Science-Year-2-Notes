#### LAZY EVALUATION
- With functional programming languages, there are two popular evaluation strategies:
	- Eager / CBV - Evaluate arguments first
		- (λx → x + x) (1 + 2) -> 
		- (λx → x + x) 3 -> 
		- 3 + 3 ->
		- 6
	- Lazy / CBN - Substitute arguments in the function body first
		- (λx → x + x) (1 + 2) -> 
		- (1 + 2) + (1 + 2) ->
		- 3 + (1+2) ->
		- 3 + 3 ->
		- 6

- In pure functional programming languages, the type of evaluation doesnt matter.
	- Haskell is lazy however

#### PROS / CONS OF LAZINESS
Pros:
- Call-by-need can save some shared computation at low intellectual cost.
	- Good for rapid prototyping of complex code.
- Nice idiosyncratic applications (covered later)

Cons:
- Harder to reason about complexity
- Counter-intuitive
- More complicated runtime, thinking is neccessary
- unsafePerformIO has hard to predict behaviours
- Laziness can be emulated in other languages

#### IDIOSYNCRATIC APPLICATIONS
- Infinite values can be used easily in the language
	allNats :: [Int]
	allNats = 0 : map (+1) allNats


#### OPTED NOT TO FINISH AS IT DOESNT COME UP IN "TOPICS FOR REVISION"