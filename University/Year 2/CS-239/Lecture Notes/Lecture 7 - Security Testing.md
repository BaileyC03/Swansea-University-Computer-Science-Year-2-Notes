#### Introduction:
- Software testing:
	- Evalyation against functional / non functional requirements
- Connectivity:
	- E.G: Cloud computing, Location-based services
- Vulnerability:
	- A weakness of an asset or group of assets which can be exploited by one or more threats
- Security Testing
	- Software evaluation against Security Requirements

#### Software Testing: Revisit:
- Static testing:
	- Review software development artifacts without executing them
		- Manual review of design focs / source code
		- Code static analysis etc
- Dynamic testing:
	- Execute and verify software against expected behaviours from a finite set of Test Cases
		- Test suite - finite set of test cases

#### Test Case Execution
![[Pasted image 20250414105426.png]]
- Verdict
	- Pass / Fail / Inclusive
	- Failure - an undesired behaviour
	- Fault - the cause of the failure

#### Testing Dimensions:
![[Pasted image 20250414105506.png]]

#### Security Testing Purposes:
- Security Functional Testing
	- To validate intended security functionality
		- Do all indented security countermeasures function correctly using well-defined expected outputs? 
- Security Vulnerability Testing
	- To identify unintended system vulnerabilities
		- Does the system have any known vulnerabilities? 
		- Using malicious, unexpected inputs

#### Vulnerability
- A type of fault related to security properties
- Related to 1+ assets and their corresponding security properties
- The existence of a vulnerability means either missing or faulty security countermeasures / mechanisms

#### Exploitation and Attack
- Exploitation
	- Malicious input/steps to make use of a vulnerability
	- Each vulnerability can have multiple exploitations
- Attack
	- Perform an exploitation to violate related security property of an asset
- Security Testers
	- Play the role of a hacker to exploit systems vulnerabilities
#### Model-based Security Testing 
- Automatic and systematic generation of test cases from models of systems under test and their environments
- ![[Pasted image 20250414105923.png]]
- Benefits:
	- Early and explicit review of system behaviours
	- Better documentation of test cases
	- The ability to automatically generate useful tests and measure and optimise test coverage
	- The ability to evaluate and select regression test suites
	- Easier updates of test models and suites due to changes in requirements and designs
	- Higher test quality through model-based quality analysis
	- Shorter schedules and lower costs
- Input Models:
	- Attacker models
		- Attacker's targets, capabilities and steps (Attack trees, attack graphs etc)
	- Vulnerability models:
		- Weakness encoding in system models
	- Properties models:
		- Asset not-to-be-violated security properties encoding in system models

#### Generating test cases from Attack Trees: 
- Input, an attack tree
- Output, a set of abstract test cases
![[Pasted image 20250414110228.png]]

#### Abstract Test Cases (ATC)
- ATC - A sequence of attack actions
- ATC Execution - Execute every attack action in order
- Successful Execution / Attack
	- All attack actions are successfully executed
- Failed Execution / Attack
	- Not all attack actions are successfully executed
- An ATC passes if its execution is not successful
- An ATC fails if its executions is succesful

#### Generating Test Cases:
- Simple Actions
![[Pasted image 20250414110457.png]]

- Simple OR
![[Pasted image 20250414110517.png]]
![[Pasted image 20250414110718.png]]

- Simple AND
![[Pasted image 20250414110534.png]]
![[Pasted image 20250414110655.png]]

- Simple SAND
![[Pasted image 20250414110551.png]]`
![[Pasted image 20250414110752.png]]

- COMBINED: 
![[Pasted image 20250414110831.png]]

