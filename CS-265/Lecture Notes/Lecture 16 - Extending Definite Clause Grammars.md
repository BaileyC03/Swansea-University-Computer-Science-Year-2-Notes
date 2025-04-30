#### DCGs - Extra Arguments
- DCGs allow us to specify extra arguments which we can use for many purposes.

#### Extending the Grammar:
- Consider this grammar from the last notes page:
``` DCG
s --> np, vp.  
np --> det, n.  
vp --> v, np.  
vp --> v.  
det --> [the].  
det --> [a].  
n --> [woman].  
n --> [man].  
v --> [shoots].
```
suppose we want to also contain pronouns like:
- she shoots *him*
- he shoots *her*
what can we do? 
- Add RULES FOR PRONOUNS!
- Add a rule saying noun phrases can be pronouns?
	- This is not right because "her shoots she" works now.
	- This is considered overgeneration where the grammar recognised stinky strings. 

#### Whats wrong with this? 
- It ignores some basic facts about english
	- "she" and "he" are subject pronouns and cannot be used in the object position.
	- "her" and "him" are object pronouns and cannot be used in the subject position.
- So now we've gotta extend the DCG with this information!
	- ok but how?

#### One (naive?) way
``` DCG
s --> np_subject, vp.  
np_subject --> det, n. np_object --> det, n.  
np_subject --> pro_subject. np_object --> pro_object.  
vp --> v, np_object.  
vp --> v.  
det --> [the].  
det --> [a].  
n --> [woman].  
n --> [man].  
v --> [shoots].  
pro_subject --> [he].  
pro_subject --> [she].  
pro_object --> [him].  
pro_object --> [her].
```
- Note the creation of NPs for subjects and objects.
- We also need S and VP rules.

#### A nicer way!
```DCG
s --> np(subject), vp.  
np(_) --> det, n.  
np(X) --> pro(X).  
vp --> v, np(object).  
vp --> v.  
det --> [the].  
det --> [a].  
n --> [woman].  
n --> [man].  
v --> [shoots].  
pro(subject) --> [he].  
pro(subject) --> [she].  
pro(object) --> [him].  
pro(object) --> [her].
```
- Note we have introduced only one new NP rule for pronouns. 
- The NP rules take an extra argument which is an argument for subject or object.
- In the first NP rule, this feature can be either "subject" or "object" as it doesnt matter in the body.

#### What da flip is goin on?
- Recall the rule:
	- s -> np, bp
- is just syntactic sugar for:
	- a(A,B) :- np(A,C), vp(C,B).

#### General Observation:
- While focusing on grammars for natual language, the form of CFG is general Backus-naur-form which is used to define programming languages or other formal structures.

#### Building Parse Trees:
- The programs we have discussed so far have been able to recognise grammatical structure of sentences.
- But it would also be ice if we can have a program that gives us analysis of their structure.
- In particular, we would like to see the trees the grammar assigns to sentences.
- E.G: 
![[Pasted image 20250430131502.png]]
- Or the parse tree in Prolog:
```prolog
s(np(det(the),n(woman)),  
vp(v(shoots),np(det(a),n(man)))))
```

#### OMG WE CAN MAKE A DCG THAT BUILDS A PARSE TREE!
```prolog
s --> np(subject), vp.  
np(_) --> det, n.  
np(X) --> pro(X).  
vp --> v, np(object).  
vp --> v.  
det --> [the].  
det --> [a].  
n --> [woman].  
n --> [man].  
v --> [shoots].  
pro(subject) --> [he].  
pro(subject) --> [she].  
pro(object) --> [him].  
pro(object) --> [her].
```

#### Beyond Context-free languages
- In the previous lecture we presented DCGs as a useful tool for working with context free grammars.
- However, DCGs can deal with a lot more than just context free grammars.
- The extra arguments gives us the tools for coping with any computable language
- We can illustrate this by looking at the formal language:
	- a^nb^nc^n\\{e}

#### DCG for a^nb^nc^n\\\{e}:
```DCG
s(Count) --> as(Count), bs(Count), cs(Count).  
as(0) --> [].  
as(succ(Count)) --> [a], as(Count).  
bs(0) --> [].  
bs(succ(Count)) --> [b], bs(Count).  
cs(0) --> [].  
cs(succ(Count)) --> [c], cs(Count).
```

#### Extra Goals:
- Any DCG rule is really syntactic structure for an ordinary Prolog rule.
- So its not really surprising we can call any prolog predicate from the right hand side of a DCG rule.
- This is done using curly brackets {}

#### Separating Rules and Lexicon:
- A classic application of the extra goals of DCGs in computational linguistics is separating the grammar rules from the lexicon.
- What does this actually mean brev?
	- Remove all mention of individual words in the DCG
	- Record all information about individual words in a separate lexicon

#### Concluding Remarks:
- DCGs are a simple tool to encode context free grammars
- But infact DCGs are a full programming language and can be used for many different purposes.
- For linguistic purposes, DCGs have drawbacks
	- Left-recursive rules not allowed
	- DCGs are interpreted top-down