#### Turing Reductions: 
Definition:
- A language A is turing reducible to language B (written A <=T B) if there exists an algorithm to decide membership in A using a hypothetical library function (called oracle) for deciding membership in B.
	- if A <=T B, then B is "at least as non-computable" as A is. 
		- if A is undecidable, so is B
	- "Natural PRovlems" tend to either be computable or we can reduce the Halting problem H to them
	- E.G:
		- given a multivariate integer polynomial, does it have an integer root? <- is undecidable

#### Above the Halting Problem
Definition:
- Let Tot = {\<m> | M halts for all w (element of) Σ* }.
- Then H <=T Tot, but Tot /<= H.
	- in fact, Tot is equivalent to: "Does this TM equipped with an oracle for H halt on the empty input?"

#### Collatz Conjecture:
Consider the following processes run on some natural number n:
- If n = 1, halt.
- If n is even, set n := n/2, goto 1
- else, set N := 3n+1, goto 1.
Collatz Conjecture -> The process above will terminate for all n>= 1

#### Automata are a different world:
- Theorem:
	- It is decidable whether a finite automaton will accept any word at all
- Theorem:
	- It is decidable whether a finite automaton will accept infinitely many words

#### Some Terminology:
- A function f : Σ* -> Σ* is called computable if:
	- There is a TM that will halt for any input w (element of) Σ and
	- when halting, f(w) is written on the tape
- A functon F: N -> N is called computable if:
	- the function F2:{0,1}* -> {0,1}*
	- mapping the binary representation of n to the binary representation of F(n) is computable.

#### The Church-Turing Thesis
- The computable functions are exactly those functions that we would intuitively deem to be "computable".
	- i.e. those that have some algorithmic procedure to obtain their inputs
- (physical) The computable functions are exactly those functions for which there exists an abstract physical process to transform their input into an output.
(Neither of the above are mathematical theorems, we cannot prove them however there is overwhelming evidence)


# WHAT DOES THAT MEAN IDK - HERE'S CHATGPT'S VERSION:

### **Turing Reductions (What If We Had a Magic Helper?)**

- Imagine you had a magical helper (called an _oracle_) that could instantly answer yes/no questions about some problem B.
    
- A problem A is _Turing reducible_ to B (written `A ≤T B`) if you could solve A using that helper for B.
    
    - So if A is hard, then B must be at least as hard—or harder.
        
    - For example, if A is undecidable (no algorithm can solve it), then so is B.
        
- In the real world, most problems we deal with are either:
    
    - Solvable by an algorithm (computable), or
        
    - So hard that they’re at least as hard as the **Halting Problem** (we can reduce the Halting Problem to them)
        
- **Example**:
    
    - “Does a given polynomial with several variables have an integer solution?”  
        → This is **undecidable**. No algorithm can always answer this.
        

---

### **Problems Even Harder Than the Halting Problem**

- Define **Tot** as the set of all Turing machines that halt on _every_ possible input.
    
- We can reduce the Halting Problem to Tot (`H ≤T Tot`), meaning Tot is at least as hard as H.
    
- But the reverse is not true: you can't reduce Tot to the Halting Problem.
    
    - Tot is even harder—it’s like asking:
        
        > "If I had a magic helper that could solve the Halting Problem, could I now tell whether a machine halts on _all_ inputs?"
        

---

### **The Collatz Conjecture (Simple to State, Impossible to Prove?)**

- Pick any number `n`:
    
    - If `n == 1`, stop.
        
    - If `n` is even, divide it by 2.
        
    - If `n` is odd, do `3n + 1`.
        
    - Repeat.
        
- The **Collatz Conjecture** says this will always eventually reach 1, no matter what number you start with.
    
- No one knows if this is true for _all_ numbers. We’ve tested billions—it works—but there’s still no proof.
    

---

### **Automata Are a Simpler World**

- For finite automata (like really basic computers), some things are actually easy to figure out:
    
    - **You can decide** if the automaton accepts at least one word.
        
    - **You can decide** if it accepts infinitely many words.
        

---

### **Computable Functions – What’s Actually "Doable" by a Machine**

- A function `f` from strings to strings is _computable_ if there’s a Turing machine that:
    
    - Always finishes (halts), and
        
    - Leaves `f(w)` written on the tape when it stops.
        
- A function `F` from numbers to numbers is computable if:
    
    - You can build a string-to-string function that:
        
        - Takes the binary version of a number `n`
            
        - And gives back the binary version of `F(n)`
            
    - And this string function is computable by a Turing machine.
        

---

### **The Church-Turing Thesis (The Big Picture)**

- This is the belief (not a proven fact) that:
    
    - Anything we’d _intuitively_ consider “computable” can be computed by a Turing machine.
        
    - In other words, there’s no algorithm that exists _outside_ what a Turing machine can do.
        
- There’s even a physical version:
    
    - Any process that could happen in the physical universe, where inputs become outputs, can also be modeled by a Turing machine.
        
- It’s not a theorem—we can’t prove it—but it’s backed up by a lot of evidence.