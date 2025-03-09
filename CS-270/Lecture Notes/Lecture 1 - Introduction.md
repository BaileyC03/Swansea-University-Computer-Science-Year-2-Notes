### Pre - Course notes:
- Set yourself a lab time on canvas soon, find one that works for you the best.
- Grading Weights:
	- 10% - CW1
	- 10% - CW2
	- 10% - Labs
	- 70% - Exam
- Each coursework has 6 parts.
	- One big quiz (7.5%)
	- 5 Mini, weekly quizzes (0.5% each)
		- You need 100% on these tests to get the 0.5%, but you can repeat it multiple times so make sure you get the free marks with this.
- In week 1, read chapter 1 + 2.1 + 2.2 of the book.

#### Computational Problems:
- A general description from inputs to outputs.
#### Problem Instance:
- A concrete input (its assumed a problem is in the context of above, where it's a "general problem")

#### Algorithm:
- A computational procedure which acts on the inputs to produce an output. 
- An algorithm *must* work on all problem instances (inputs)
- We want to express these algorithms in the cleanest and most consise way

#### Program:
- NOT AN ALGORITHM
- It's an implementation of an algorithm.


#### Insertion Sort: 
- How it works:
	- Insert a number, in the right spot, in a set of pre sorted numbers.
	- Starting from 0, you assume its sorted. Then the first number goes in. 2nd goes in the right spot, 3rd etc etc.....
- The problem with using an array for this:
	- Arrays are good at random lookup, however are shit at appending in the middle as you have to then push all the numbers following it across by 1.

