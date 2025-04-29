#### Proving that a language is not context-free
- {a^n b^n c^n | n (element of) N} is not context free
- Nor is {ww | w (element of) Σ* } whenever |Σ| >= 2.
How do we prove this? 
- Pumping Lemma for Context-free Languages! 

#### Quantifiers: 
- ∀x - For all x, it is true such that....
- ∃x - There exists an x in which it is true that...
#### THE LEMMA:
If L is regular and context-free, it is the case that:
- If for all k within N, you can pick a word p within L with |p| >= k
	- aka a section within the word 
- such that however p is written as uvw (and v is not empty)
- you can find a version of repeating v which isnt within your language
- Then L is not regular
#### NOW IN PEOPLE WORDS:
- Pick a word
- Take a chunk out the middle
- Spam it a bunch of times
- If there's ever an instance where a certain number of spams isnt in the language, its not regular.
This video slaps: https://youtu.be/Ph7Z9YttM0Q



