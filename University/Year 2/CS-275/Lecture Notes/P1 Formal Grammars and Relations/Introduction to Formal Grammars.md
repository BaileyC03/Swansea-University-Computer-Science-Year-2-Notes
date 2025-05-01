#### Defining Formal Grammars:
- We have:
	- an alphabet Σ
	- the elements of which we call terminal symbols {a,b,c,...}
	- A disjoint set of symbols N which we call non-terminal symbols
	- a special start symbol, S
- A grammar is a finite list of pairs (u,w) where:
	- both u and w are within the alphabet or non terminal symbols
	- It is often written as u -> w

#### How formal grammars define languages: 
- Definition
	- A grammar G defines a language L(G) by saying that a given t is within our language if we can reach t through the following processes:
		- Start at node S
		- Write our current word as v0uv1 and pick a rule (u,w). then replace the current word by v0wv1
		- If the current word is t, stop. Otherwise, repeat the step above
	- What does this mean? I dont know. But basically if you can follow the arrows in a way which forms your word then it's part of ur language

#### A "Real" Grammar:
- Example:
	- Let Σ be {the, dog, cat, eats, sleeps}
	- The rules are:
		  S -> NP VP
		  NP -> the NOUN
		  NOUN -> cat
		  NOUN -> dog
		  VP -> INTRANS-VERB
		  VP -> TRANS-VERB NP
		  TRANS-VERB -> eats
		  INTRANS-VERB -> sleeps
		  INTRANS-VERB -> eats
	- let's say we have to find all words belonging to the language of this grammar (or sentences in this case but we still consider them words)

#### Outlook
- Without restrictions on how words may look, it can be time consuming to show a word belongs to a language
- And it can be impossible to show a word does not belong to the language
- We can formalise the derivation process a little more by introducing the transitive closure of a relation.
	- This is brought up more in another lecture