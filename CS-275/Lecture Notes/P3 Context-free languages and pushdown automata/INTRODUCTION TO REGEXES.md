#### PATTERN MATCHING: 
- Process of searching for a specific sequence (aka pattern) of characters within a larger set of data (like a string or text).
- The goal is to check whether a predefined pattern exists within the input and obtain the useful information to elaborate the data.
- It's like super fuckin common in CS.
	- Find / replace function
	- Data validation (real email?)
	- Log analysis
	- Compilers, Interpreters
	- Text processors etc

#### REGular EXpressions (REGEX):
- A regex is a string describing a specific pattern.
- These are used in combination with search engines which scan the input looking for a subset of the data matching the specified pattern.
- E.G: 
	- Imagine that in a document you search for a specific word like "hello"
	- That is a specific sequence of characters h-e-l-l-o

#### Regex in programming languages:
- Many programming languages actually have a pattern matching engine for patterns and regexes. 
- This is how it looks in python:
``` python
import re

text = "Hello, this is a simple string"
pattern = "Hello"

match = re.rearch(pattern,text)
print(match.group())
```

#### Regex and Automata
- If we are given a string, variable name *text*, a simple way to search for a substring sub is to check - for each character - whether the substring of text that begins in that position is exactly *sub*.
- This actually corresponds precisely to being recognised by the FSA that accepts the language {sub}
- E.G: 
	- text = "Hello, this is a simple string"
	- sub = "this"
![[Pasted image 20250423133200.png]]

- E.G: 
	- what if we are looking for "this" OR "that"? 
	- We can actually change our FSA to reconise both:
		text = "The cat is on that table"
		sub = "this | that"
![[Pasted image 20250423133424.png]]
- Technically its best to not combine the "th" parts for whatever reason, I forgot why tho. you prolly can and it'll be ok.

- The same process can be generalised though, instead of using a FSA to recognise a language with just 1/2 strings, we can use it to recognise literally any regular language! :ooo 
- AKA regexes were originally introduced as simple cmpact notation to describe FSA (and regular languages by extension)

#### Closure Properties: 
Remember the following: 
![[Pasted image 20250423134545.png]]
I would put this in text but cba to get the funky symbols so if ur a random guy reading this off my github its slide 9 here: [https://canvas.swansea.ac.uk/courses/52641/files/7870623?module_item_id=3157720]

- The use of regular expression reflects the closure properties of regular languages
- E.G: 
	- the FSA recognising the word "this" can be seen as the concatenation of FSA's recognising the words t,h,i and s.
	- The language L = {this} can be seen as the language made by concatenating {t}, {h}, {i}, {s}
	- Also! The language described by the regex this|that is regular as it's the union of the 2 regular languages L = {this} and M = {that}

####  Basic Examples of Regexes: 
- Like in previous examples, "this | that" are some examples of regexes
- In a regex, most characters tend to just represent themselves like "t" in "this".
- Some characters can be quirked up however, check this shit out:

#### QUIRKED UP REGEX CHARACTERSL
- . - Matches any character except newline
- \d - Matches the digits (0-9)
- \D - Matches every non-digit (aka !\d)
- \w - Matches the word chatacyers (a-z, A-Z, 0-9, _)
- \W - Matches every non-word character (aka !\w)
- \s - Matches the  whitespaces (' ', \t, \n, \r, \f, \v)
- \S - Matches every non-whitespace (aka !\s)

#### Examples: 
- a\dbc -> Anything with the form 'a', then a digit, then 'bc'
- \d\s\d -> Any 2 digits with whitespace between
- \w,\w,\w -> Any 3 words with commas between them

#### REGEX SETS:
- We can define arbitrary sets of characters using []
- E.G: 
	- [abc] -> matches either a, b or c
	- [0-9] -> matches any character between 0-9, aka \d
	- [abc0-9] -> a,b,c or any digit (aka [abc\d])
	- [^ abc] -> matches anything NOT in the group (aka not a/b/c)

#### Quantifiers: 
- * ->  0+ Repetitions
- + -> 1+ Repetitions
- ? -> 0 or 1 Repetition
- {n} -> Exactly n times
- {n,m} -> at least n times, at most m times.
	- can be blank to signify 0 and infinity for n and m

#### Special Characters
- ^ -> Matches the beginning of a string
	- UNLESS USED IN A [], then it's a "not".
- $ -> matches the end of a string
- / -> Escape character, used to change the meaning of the next character
- | -> OR operator

Examples: 
- ^Hello -> Any string which begins with hello
- bye$ -> Any string that ends with bye
- \w\\w -> matches any word (\w) followed by literally "\w"
- \d{7}@swansea\.ac\.uk -> Swansea student email
- this|that -> this or that

#### Groups: 
- Powerful, used to isolate subpatterns.
- Helpful in elaborating the results of the match of the regex (in the rest of the program, outside of the pattern matching
- E.G: 
	- (ab)+ -> Matches 'ab' 1+ times
	- (a | c{2})* -> matches any sequence of spamming 'a' or 'cc'
	- (\w+[ \t]\*,){3}\w+ -> Matches 4 comma separated words

#### Recursive Regexes: 
- Groups are the key to describing way more than just regular languages.
- This is usually achieved by defining recursive regexes (i.e. regexes that allow a pattern to refer to itself.)
- The syntax can be complex and language dependent and can be funky.
- E.G: 
	- a((?R)\*)b
