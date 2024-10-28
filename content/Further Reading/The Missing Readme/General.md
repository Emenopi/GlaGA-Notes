---
tags:
---
## Concepts to investigate

- Software entropy: 
	- drift towards messy code
	- prevention: style, bug detection tools code reviews, refactoring
- Technical debt: 
	- future work to fix shortcomings in current code
	- increasingly complex workarounds - compounds with replication - complexity spreads
	- prudent vs reckless
- Null object pattern
	- Uses objects in lieu of null values e.g. returns empty list instead of null
- Object Types

## Takeaways
- Leave code cleaner than found
	- Separate code cleanup commits from behaviour changing commits
- Commits
	- Prefix with issue ID
	- https://chris.beams.io/posts/git-commit
- Defensive programming (p. 48)
	- Avoid null values
		- Use the null object pattern and option types
		- Perform null checks at beginning of methods; use `NotNull` annotations or similar features when available
	- Use immutable variables
		- prevent unexpected modifications
		- can improve compiler efficiency
	- Use type hinting and static type checking
		- constrain values that variables can take, e.g. Enum instead of string
		- ensures unexpected values will immediately fail
		- use most specific type possible when defining variables
		- Type hinting lets you specify a variables type in a language that's normally dynamically typed
	- Validate inputs
		- use preconditions, checksum and validate data, use security best practices, and tools to find common errors
		- reject bad input as early as possible
	- Use exceptions
		- don't use special return values (null, 0, -1, etc) to signal an error
		- be precise with exceptions. Use build in exceptions when possible, avoid generic exceptions
		- use exceptions for failures, not controlling logic
		- throw exceptions early, catch exceptions late
			- throw early: catch exceptions as close to the error as possible so devs can quickly find relevant code. avoids second error being triggered masking the first one
			- catch late: propagate exceptions up the call stack until you reach level of the program capable of handling exception