#### Games VS Search Problems:
- Unpredictable opponent
	- Solution is a strategy specifying a move for every possible opponent reply
- Time limits
	- Unlikely to find goal, must approximate

#### Types of Games:
- Perfect Information & Deterministic
	- Chess
	- Checkers
	- Go
	- Othello
- Perfect Information & Chance
	- Backgammon
	- Monopoly
- Imperfect Information & Deterministic
	- Battleships
	- Blind tictactoe
- Imperfect Information & Chance
	- Bridge
	- Poker
	- Scrabble
	- Nuclear War

#### Deterministic Games
- Many possible formalisations, one is: 
	- States: S (Start at S0)
	- Players: P = {1, ..., N} (Usually take turns)
	- Actions: A (may depend on player / state)
	- Transition Functions: S x A -> A
	- Terminal Test or Goal Test: S -> {true, false}
	- Terminal Utilities: S X P -> R (reward value)
- Solution for a player is a policy / strategy S -> A


#### Zero-Sum Games:
- Zero Sum Games 
	- Agents have opposite utilities (values on outcomes)
	- Let us think of a single value that one maximises and one minimises
	- Adversarial, pure competition
- General Games
	- Agents have independent utilities (values on outcomes)
	- Cooperation, indifference, competition and more are all possible.

#### Adversarial Search:
- Search based on zero-sum games
- Mathematical representation in game theory where the result is an advantage for one side and an equivalent loss for another.
- Net Zero

#### Adversarial Search (minimax)
- Deterministic, Zero sum games
	- Tic-tac-toe, chess, checkers
	- One player maximises results
	- The other minimises results
- Minimax Search:
	- A state-space search tree
	- Players alternate turns
	- Compute each node's minimax value 
		- the best achieveable utility against a rational adversary