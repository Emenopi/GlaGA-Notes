---
tags:
  - Foundations_of_Professional_Software_Dev
  - Reference_Notes
---
> "Bad tests add developer overhead without providing value and can increase test suite instability"

In addition to checking that code is working correctly, tests protect code from future changes which may unintentionally alter behaviour.

Test writing forces the developer to consider the interface and implementation of their software. Highly [[Coupling|Coupled]] code is hard to test.

Tests serve as a form of documentation, illustrating how code is meant to be interacted with. They should be the first thing a developer reads to understand a new codebase.

***Unit Tests*** should be fast, small, and focused. Speed is important because these tests run frequently. Small tests that focus on a single unit of code make it easier to understand what has broken when a test fails

***Integration Tests*** can flush out problems that are difficult to identify by unit testing

***System Tests*** simulate real user interaction in pre-production environments

## Test Tools

***Test Writing Tools*** like mocking libraries help to write clean and efficient tests

***Test Frameworks*** help run tests by modelling a test's lifecycle from setup to teardown. They also save test results, integrate with build systems, and provide other helpers

***Code Quality Tools*** are used to analyse code coverage and code complexity, find bugs though static analysis, and check for style errors. Analysis tools are usually set up to run as part of a build or compile step

Tools may depend on other libraries which increases complexity of the system.
Some tools slow down tests.

### Mocking Libraries

- Commonly used in unit tests
- Mocks replace external dependencies with stubs that mimic the interface provided by the real system. They implement functionality required for the test by responding to inputs with hard-coded responses
- Eliminating external dependencies keeps unit tests fast and focused
- Mocking remote systems allows tests to bypass network calls, simplifying setup, and avoiding slow operations.
- Mocks also help keep application code from being riddled with test-specific methods, parameters, or variables. They help developers access protected methods and variables without modifying code
- Don't overdo mocking. Mocks with complex internal logic make tests brittle and hard to understand
- An excessive reliance on mocks is a code smell that hints to tight coupling


### Test Frameworks

- Test frameworks help to write and execute tests by:
	- Managing test setup and teardown
	- Managing test execution and orchestration
	- Generating test result reports
	- Providing tools such as extra assertion methods
	- Integrating with code coverage tools
- Setup and teardown methods allow developers to specify steps such as data structure setup or file cleanup that need to be executed before or after each test or set of tests
- Test frameworks help control speed and isolation of tests though test orchestration.
	- Tests can be executed serially or in parallel
		- Parallel execution is faster but more error prone due to shared state,, resource, or other contamination
- Test reports help debug failed builds


### Code Quality Tools (Linters)

- Linters run static analysis and perform style checks
- Static code analysers look for common mistakes
	- Particularly important for dynamic languages like Python and JavaScript
	- Look for known code smells and highlight questionable code but are not immune to false positives
- Code style checkers ensure all code is formatted the same way
- Code complexity tools guard against overly complex logic by calculating cyclomatic complexity (the number of paths through the code)
	- The higher the complexity, the more difficult it is to test and more defects it's likely to contain
- Code coverage tools measure how many lines of code exercised by test suite
	- Aim for 65% - 85% coverage as rule of thumb


## Writing Tests

- Many companies have formal QA teams with varying responsibilities including:
	- Writing black box or white box tests
	- Writing performance tests
	- Performing integration, user acceptance, or system tests
	- Providing and maintaining test tools
	- Maintaining test environments and infrastructure
	- Defining formal test certification and release processes
- Write tests with same care as other code
- Tests introduce dependencies, require maintenance, and need to be refactored over time
- Keep tests cohesive and decoupled
- Focus on testing fundamental functionality rather than implementation details
	- Helps when refactoring codebase as tests will still run
- Keep test dependencies separate from regular code dependencies
- Write tests that fail meaningfully
- Tests shouldn't fail when trivial changes are made
- Focusing on high-value tests yields most benefit for cost

## Determinism in Tests

- Deterministic code always produces the same output for the same input
- Nondeterministic tests degrade test value
	- Intermittent test failures are hard to reproduce and debug
- Nondeterminism is introduced by improper handling of sleep, timeouts, and random number generation
	- Tests that leave side effects or interact with remote systems also cause nondeterminism
- Escape nondeterminism by making time and randomness deterministic, cleaning up after tests, and avoiding network calls
	- Seed random number generators with a constant
	- Don't call remote systems in unit tests
		- Speed and portability are critical for unit tests
	- Use injectable clocks rather than static time methods so that you can control the timing your code sees in a test
	- Avoid sleeps and timeouts
	- Isolate and clean up leftover test state
		- Don;t depend on passed tests to clean up
	- Don't depend on test order