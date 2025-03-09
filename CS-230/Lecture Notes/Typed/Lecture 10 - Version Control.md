- Version control tracks changes to a set of files
- A project / repository is a set of file in version control
- Version control works better on text files (.java, .c, .txt) than binary files (.class, .exe., .jpg)
- Commit edits should be small

#### EACH COMMIT:
- With each revision, the system stores:
	- The diffs for the version
	- The new version number
	- Other:
		- Author / person checking it in
		- Time of the checkin
		- Log file message (CRITICAL)

#### BRANCHES:
- Slightly different revisions of a file which are tracked slightly differently
- Must explicitly ask to create a branch

#### MERGING:
- Merging is Syntactic
- Semantic errors may not create syntactic conflicts however the code may very well still be wrong.

#### GIT (Came after Subversion):
- GIT is a distributed version control system
	- No central repository required
	- People commit locally, then push their commits to other repositories
	- You  can make a centralised repository and then use git as a centralised system if needed.
- People can push changes to other people's local repositories
- People can pull changes from other people
- Massively Flexible 
	- Many ways to work with it
	- Makes it hard to learn