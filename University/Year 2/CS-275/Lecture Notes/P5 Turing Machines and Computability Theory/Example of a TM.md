#### A TM RECOGNISING {a^n b^n c^n}

#### 1. Starting State
- read a: write x, move right, go to State 2
- read b: go to state no
- read c: go to state no
- read x: write x, move right, go to State 1
- read ⊥: go to state yes

#### 2. Scanning for a b
- read a: write a, move right, go to State 2
- read b: write x, move right, go to state 3
- read c: go to state no
- read x: write x, move right, go to state 2
- read ⊥: go to state no

#### 3. Scanning for a c
- read a: go to state no
- read b: write b, move right, go to State 3
- read c: write x, move right, go to State 4
- read x: write x, move right, go to state 3
- read ⊥: go to state no

#### 4. Returning to the beginning
- read a: write a, move left, go to state 4
- read b: write b, move left, go to state 4
- read c: write c, move left, go to state 4
- read x: write x, move left, go to state 4
- read ⊥: write ⊥, move right, go to State 1