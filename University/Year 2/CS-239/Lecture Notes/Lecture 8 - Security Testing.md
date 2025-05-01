#### Coded-Based Security Testing (CBST)
- To detect vulnerabilities by examining the source code
- Input: Source code (non-executable under system test)
- Approaches: Manual VS Automatic

#### Manual Code Review
- Expert to read source code line-by-line
- Expertise: 
	- Application architecture
	- Implementation techniques
		- Programming languages
		- Frameworks
		- Libraries
	- Security
	- Secure coding guidelines
- Steps:
	- Understand attack surfaces
	- Review code
	- Report the result

#### Static Application Security Testing [SAST]
![[Pasted image 20250414114231.png]]
#### SAST Analysis
- Syntactic Checks:
	- Calling insecure APIs
	- Using insecure configuration options
- Semantic Checks
	- Using models of data flow and/or control flow.
	- E.G: SQL Injection due
		- due to unsanitised data flow from input to SQL statement

#### Tainted Analysis:
- Tracking the propagation of tainted data through a program

#### Penetration Testing (Pentesting)
- To mimick real-world attacks on real systems and data
- To use tools and techniques commonly used by attackers
- To circumvent security features
- To seek combinations of vulnerabillities on 1+ systems to gain more access
![[Pasted image 20250414114729.png]]

#### Pen-Testing; Pros and Cons:
- Pros - Helps determine:
	- System tolerance under real-world attacks
	- The level of sophistication an attacker needs
	- Additional countermeasures to mitigate threats
	- Defenders ability to detect and respond to attacks
- Cons:
	- Labour intensive
	- Require great expertise
	- Cause system under test (or systems) damaged or inoperative
	- Need careful consideration, notification and planning

#### Fuzz Testing
- To stress system under test with unexpected inputs and data structures through external interfaces
![[Pasted image 20250414114937.png]]
- Techniques:
	- Random fuzzing
	- Mutation-based fuzzing
	- Generation-based fuzzing
	- Advanced fuzzing

#### Mutation-based Fuzzing:
![[Pasted image 20250414115100.png]]
- Mutation example: BlendFuzz
![[Pasted image 20250414115259.png]]
- Mutation Example:
![[Pasted image 20250414115320.png]]

#### Generation Based Fuzzing
![[Pasted image 20250414120424.png]]

