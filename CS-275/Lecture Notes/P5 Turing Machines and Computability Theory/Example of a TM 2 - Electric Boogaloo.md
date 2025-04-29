#### A TM COMPUTING X |-> 4X in UNARY
- The input alphabrt is {1}, the tape alphabet is {1,x,⊥}. The folloing TM will compute multiplication by 4 in unary by first looping through the input replacing a 1 with an x, then adding 3 more x to the end of the currently used part of the tape. Once all 1s are gone, the Xs are replaced by 1s and the program halts. 

#### 1. Starting State
- Read 1: Write x, move right, go to state 2
- Read x: Write x, move right, go to state 1
- Read ⊥: Halt (the input was 0 so we output 0)
#### 2. Scanning for the right end
- Read 1: Write 1, move right, go to state 2
- Read x: Write x, move right, go to state 2
- Read ⊥: Write x, move right, go to state 3
#### 3. Writing the second 1
- Read 1: Halt (this shouldnt happen)
- Read x: Halt (this shouldnt happen)
- Read ⊥: Write X, move right, go to state 4
#### 4. Writing the third 1
- Read 1: Halt (Tis shouldnt happen)
- Read x: Halt (This shouldnt happen)
- Read ⊥: Write X, move left, go to state 5
#### 5. Returning to the beginning
- Read 1: Write 1, move left, go to state 5
- Read x: Write x, move left, go to state 5
- Read ⊥: Write ⊥, move right, go to state 6
#### 6. Searching for another 1
- Read 1: write x, move right, go to state 2
- Read x: write x, move right, go to state 6
- Read ⊥: write ⊥, move left, go to state 7
#### 7. Turning the x to 1
- Read 1: write 1, move left, go to state 7 (shouldnt happen)
- Read x: write 1, move left, go to state 7
- Read ⊥: halt (done)
