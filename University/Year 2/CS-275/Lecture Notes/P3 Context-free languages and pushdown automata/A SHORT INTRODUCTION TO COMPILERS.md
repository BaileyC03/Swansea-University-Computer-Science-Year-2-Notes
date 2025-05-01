#### How does a compiler / interpeter work? 
- A compiler is a program that can read a program in one language [source language] and translate it into an equivalent program in another language [target language]
![[Pasted image 20250423142843.png]]
- An interpreter is a program that processes a program written in the source language and directly executes the operations specified in the source program on inputs supplied by the user.
![[Pasted image 20250423142921.png]]

Java is both compiled and interpreted (what the flip?)
![[Pasted image 20250423142946.png]]

#### Syntax VS Semantics:
- The analysis of a source code is divided into 2 major parts: 
	- Syntax -> Set of rules that describe a valid program
	- Semantics -> "Meaning" and logic or program.

#### CREATING A SIMPLE COMPILER:
- To do this we need 3 main ingredients:
	- Grammar -> We need to specify how a valid program should look
	- Lexer -> Software that checks the source files respect the grammar
	- Parser -> Software that analyzes the output of the lexer and executes the code

#### Hello World
- To make a print command we can describe the grammars as such:
	- S -> PRINT STR
	- Print -> print
	- STR -> "TXT"
	- TXT -> [a-z ]TXT
	- TXT -> e

#### The Lexer:
- The part of the interpreter that checks the syntax and converts the source code in an easier-to-analyze form for the parser.
- While there are software libraries for text analysis, we're building outs from scratch so cant be doin that. Example below reads the source code 1 character at a time and is executed once per line (So in theory every line is a program!)

- We need to recognise if a line is a valid word in our program: 
- Refer to the grammar above
![[Pasted image 20250423143609.png]]
- However the lexer needs to translate this into an input for the parser.
- For this, the lexer makes a list of tokens that take the form:
	- <opcode, value>
	- E.G: <PRINT, hello world> tells the parser to print 'hello world'

#### The Parser:
- Analyses the output of the lexer and figures out what the flip to do
![[Pasted image 20250423143918.png]]
- Lexers and parsers are usually written in an already existing language. The first ones, however, were done in assembly!

#### VARIABLES AND BASIC ARITHMETIC
- Now to add variable instantiation we can focus on integers for this.
- We need 2 things: 
	- Syntax for creating variables (int x, int y)
	- Syntax for writing simple math expressions with +,-,*,=
		- y = 3
		- x = (y+3)\*(2-1)

#### Syntax for creating variables:
Our current grammar is: 
- S -> PRINT STR
- PRINT -> print
- STR -> "TXT"
- TXT -> [a-z]TXT
- TXT -> e

So we're gonna need to add the following rules:
- S -> INT VAR
- INT -> int
- VAR -> [a-z]VAR
- VAR -> e

Now we have more rules, the automaton is also gonna get a bit more chungus large.
![[Pasted image 20250423144410.png]]

#### The Simbol Table
- How do we know the value of x, if x has a value
- All of the components of the compiler usually share access with a common memory location konwn known as the symbol table
- Upon receiving <INT, x> the parser stores the symbol x and initialises its value to 0.
![[Pasted image 20250423144930.png]]

#### Variable assignment and expressions
- We want to add code that makes this work: 
![[Pasted image 20250423145014.png]]
These lines have 3 partS:
- Left hand side of equality -> A variable
- Equality symbol -> =
- Right hand side of equality -> An expression
Henceforth we must add the following rules: 
- S -> VAR EQ EXPR
- EQ -> =
- EXPR -> NUMBER | 
			VAR | 
			(EXPR + EXPR) |
			(EXPR - EXPR) |
			(EXPR * EXPR)
- NUMBER -> 0 | 1 | 2 ... 9
Meaning our language looks like this now: 
![[Pasted image 20250423145340.png]]
Matching bracket's cannot be described with a finite automaton btw.
This is a context-free language tho

#### Back To The Lexer: 
- Since we have a context-free language, the lexer now implements a pushdown automaton
- It works similarly as before but now we have more opcodes
![[Pasted image 20250423145548.png]]
omg so complex :c 

#### THE PARSER: 
- A list of opcodes is easier to analyse as we know they follow precise rules
- The parser can use the lexer's output to produce the parse tree of the expression
![[Pasted image 20250423145657.png]]
- Parse trees make the analysis of the expression way easier.
- We obtain the numerical value by a simple recursive algorithm
- The parser needs to check that variables exist in the symbol table.
- If they don't, it can either initialise them or raise an error
- For typed languages (like C or Java) a type check is done before assigning values

#### IF, THEN, ELSE:
```java
if (expression){
	print"stuff"
}else{
	print(nothin
}
```
- A grammar for expression can be obtained similarly to the grammar for math.
	- Bool -> TV | COND | (BOOL and BOOL) | (BOOL or BOOL) | (not(BOOL))
	- TV -> true | false
- As our language only works with integers, COND should be some statements about integers (\==,<, >, <= etc)
	- COND -> CAR C_OP VAR
	- C_OP -> == | != | <= | >= | < | >

Very poggers thank u
