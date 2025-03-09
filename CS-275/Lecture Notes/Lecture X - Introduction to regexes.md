Regex - Regular Expression
- Real application of automata
- Used every day

#### Pattern Matching
- Process of searching for a specific sequence (pattern) of characters within a larger set of data
	- Like a string or text
- Goal - check if a predefined pattern exists in the input and obtain useful information
- Examples:
	- Find/replace functions
	- Data validation (is this a valid email?)
	- Log analysis
	- Compilers and interpreters
	- Text processors

REGular EXpressions
- a regex is a string describing a specific pattern
- Regexes are then used in combination with search engines, which can scan the input looking for a subset of the data matching the specified pattern.
	- E.G:
		- if youre looking for a word "hello", the string "hello" specifies the specific equence (h-e-l-l-o)

#### REGEX
- Many programming languages include an engine for pattern matching and regexing in their standard library
- The specific syntax may depend on the chosen language, but there is a basic set of expressions that are common and shared among most languages.

#### REGEX and Automata
- Given a string "text", a simple way to check for a substring "sub" is to check, for each character, whether the substring of text that begins in that position is exactly "sub".
```python
for i in range(len(text)):  
match = 1 # Assume a match unless proven otherwise  
# Check if substring matches character by character  
for j in range(len(sub)):  
if text[i + j] != sub[j]:  
match = 0 # Mismatch found, break out  
break  
if match: # If all characters matched, return index  
return i  
return -1 # Return -1 if substring not found
```
- But this corresponds precisely to being recognised by the FSA that accepts the language {sub}
- But what if we are looking for, for example "this" or "that"?
- text: "the cat is on that table"
- sub: "this | that"

- The same process can be generalised, instead of using a FSA to recognise a language with 1/2 strings we can use it to recognise any regular language :o 
	- In other words, regexes were introduced originally a simple and compact notation to describe FSA (or, equiv, to describe regular languages)

#### Closure Properties:
![[Pasted image 20250304162225.png]]

#### Closure Properties
- The use of regular expression reflects the closure properties of regular languages.
- E.G: 
	- the FSA recognising the word "this" can be seen as the concaternations of FSAs recognising the words "t", "h", "i", "s". The language L = {this} can be seen as the language obtained as the concatenation:
		- ToHoIoS
		- where:
			- T = {t}
			- H = {h}
			- I = {i}
			- S = {s}
- Similarly the language described by the regex this|that is regular as it's the union of the two regular languages L={this} and M={that}

#### Basic Examples of Regexes
- "this" or "this|that" are examples of regexes
- In a regex, most characters represent themselves.
	- 't', 'h', 'i', 's' in "this"
- However some characters have special meanings and are used to represent more complex patterns
	- '|' in 'this | that'
	- . (matches any character, except newline)
	- \d (matches the digits 0-9)
	- \D (matches non-digits, everything not \d)
	- \w (matches the word characters a-z A-Z 0-9 _)
	- \W (matches every non-word character, every non word)
	- \s (matches the whitespaces,\t, \n, \r, \f, \v)
	- \S (matches every non-whitespace [not \s])

- a\dbc
	- Matches anything of the form 'a', then a digit, then 'bc'
- \d\s\d
	- matches any two digits separated by a whitespace
- \w,\w,\w
	- matches any three word characters separated by a comma

- We define the arbitrary set of characters using []
- [abc] - Matches either 'a', 'b' or 'c'
- [0-9] - Matches any character between '0' and '9'
	- same as \d
- [abc0-9] - Matches 'a', 'b', 'c', or any digit
	- same as [abc\d]
- [\^abc] - Matches anything that is NOT in the group
	- all except 'a', 'b', 'c'

#### Quantifiers(comes after the subject)
- * - 0+ repetitions
- + - 1+ repetitions
- ? - 0 or 1 repetitions
- {n} - Exactly n timestimes.
- {n,m} - At least n times, at most m 
	- {,m} means m or less times 
	- {n,} means n+ times

#### Special Characters
- ^ - Matches the beginning of a string
	- THIS HAS A DIFFERENT MEANING WITHIN A []
- $ - Matches the end of a string
- \ - Escape character
	- Used to change the meaning of the next character
		- It's behaviour changes depending on the context
- | - OR operator

#### Groups
- Powerful feature of regexes that are useful to isolate subpatterns.
- They are often used to elaborate the results of the match of the regex (in the rest of the program, outside of pattern matching)
- Specified using ()
- E.G:
	- (ab)+ [matches 'ab' one or more times]
	- (a|c{2})* [matches any sequence obtained alternating 'a' or 'cc']
	- (\w+[ \t]\*,){3}\w+ [matches four comma separated words]

#### Recursive Regexes
- Groups are the key to describe more than just one regular language
- This is usually achieved via recursive regexes
	- AKA regexes that allow a pattern to refer to itself
- The syntax is more complex and language dependent and can be a pain to read
- E.G:
	- a((?R)\*)b
