cour#### Expert Systems
- Behaves like an expert in some narrow domain.
	- AKA knowledge based systems (but with more stuff)
- Typical Examples:
	- Medical Diagnosis
	- Adjusting between economy and business class seats for future flights
	- Diagnosing paper problems in rotary printing
- From specific info (input) using reasoning rules to specific info (output)

#### Structure of an Expert System:
3 main modules:
- Knowledge Base
	- Basic facts and rules of the domain
- Inference Engine
	- Part of shell
	- Uses the rules to draw inferences from basic and derived facts
- User Interface 
	- Part of shell
	- input and output wrt the user

#### Features of Expert Systems
- Problem solving in the area of expertise
- Relying heavily on structured domain knowledge
- Interaction with user during and after problem solving
- Explanation: Ability to explain results to the user
	- X because Y, Y because of Z and Z is true.

#### Desirable Features of Rules:
- Modularity
	- Each rule defines a relatively independent piece of knowledge
- Incrementality
	- New rules can be added (relatively independently) of other rules, however its important to check for conflicts and contradiction
- Modifiable and Transparent
	- Can see what specifically goes wrong or needs attention as it has explicit rules
- Can represent uncertainty
- Chaining of rules (fwd / bckwd)
	- Model extensive reasoning
- An advantage of mechanical reasoning:
	- Rich, complex sets of rules are difficult for people to reason through systematically

#### Typical types of explanations for transparency:
- How explanation
	- Answers a users questions of the form: How did you reach this conclusion
- Why explanation
	- Answers a user's questions of the form: Why do you need this information?

#### Expert Systems VS Machine Learning:
- Expert systems are markedly different from statistical / ML approaches.
	- Scale of data
	- Questions asked and answered
	- Inference v classification (though classification can be handled via rules and inference)
	- Representation of human knowledge vs representation of data
	- Development process
- Different tools for different data and purposes
- A good topic for discussion

#### Forward and Backward Chaining (look me up) 
- Backward Chaining
	- Reasoning backwards in the inference network in order to confirm or deny initial or subsidary hypotheses
	- From the head to the body, recursing through the rules until we get to basic facts.
	- Built-in reasoning style for prolog
	- no "new" facts
- Forward Chaining
	- Reason from asserted facts applied in the body of a rule to a conclusion (in a head).
	- Intermediate conclusions, i.1. what is inferred by a rule, must be added to the KB
	- May need to "asset" facts in the KB
	- Can be coded in prolog.

#### Forward Chaining
- More complex than backward as:
	- We need to add to the KB facts which are derived by inference. 
		- This is also why adding the predicates on the previous slides are informative
	- We start from the existing simple facts, composed facts (conjunctive and disjunctive) and derived facts (what follows if the condition of a rule is true).

#### Forward Chaining - An Interpreter
``` Prolog
forward :- new_derived_fact(P), %A new fact
!,
write('Derived: '), write( P), nl,
assert( fact( P)),
forward        %Continue
;
write('No more facts') %All facts derived
```
![[Pasted image 20250325124416.png]]

#### Forward VS Backwards Chaining
- Inference chains connect information that is input  to information that is output
	- data -> goals
	- evidence -> hypothesis
	- findings / observations -> explanations, diagnoses
	- manifestations -> diagnoses, causes
- Backwards Chaining: "Goal driven", from diagnosis to findings.
- Forward chaining: "Data driven", from findings to diagnosis.

- Which is better?
	- Checking a given hypothesis -> Backwards is more natural
	- If there are many possible hypotheses -> Forwards is more natural (e.g. monitoring: data-driven)
-  Expert reasoning is often a combination of the two
	- Observe X, infer to Y
	- not yet definitive, so need to check another premise:
		- Y, check backward Z

#### Generating HOW explanation:
- HOW explanation: How did you find this answer? 
- For example:
	- System - There is leak in the kitchen
	- User - How did you determine this?
- Explanation:
	- Proof tree of the final conclusion

#### WHY explanation:
- Exploring "leak in kitchen" - the system may ask "was there rain?"
- User (unsure) asks "why do you need this?"
- System: "To explore if the water came from outside"
- Why explanation = chain of rules between current goal and original (main) goal.
- Provided during the course of the interaction

#### Example:
![[Pasted image 20250325125112.png]]

#### Interactive Expert System Shell with How and Why Explanation - sketch
- Keep track of proofs
- Asks the user for input about what is / isnt a fact
- Allow asking "why" questions about a proposition
- Answer "why" questions with respect to the "local" rule about the proposition and the higher-level goals that need to be proved with respect to the highest-level goal.
- Track what can be asked about (e.g. if basic facts are true or not. The askables)
	- Askables are generally the leaves of the decision tree
- Print out sensible messages
