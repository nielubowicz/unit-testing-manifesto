# Tests: Why To 
- Avoid regressions
- Avoid bugs
- Ensure correct design
- Verification

# Tests: What To
### What type of tests should we be writing?
##### :white_check_mark: Algorithms / Data Processing
Code for business rules, or code that lives at network access layers, is some of the best code to unit test.
It often contains small, digestible bits of logic (which are easily testable) or needs to be prepared to handle a variety
of inputs (also easily testable). Even more importantly, this code is not often paired directly with UI elements so direct
QA or end user testing can be difficult. And finally, for Pull From Network And Display Data™ apps, this is really the most
crucial code component.

##### :white_check_mark: Bug Fix / Regression
It is a good idea to pair any bug fix with a set of unit tests. These tests should not only
ensure that the previous bug does not happen, but should also test against other permutations of
similar bugs (where possible). For example, if an off-by-one error is found at the end of an array, 
testing for other boundary conditions (index 0, empty array, etc) can prevent further bugs.

### What type of tests should we avoid writing?
##### :no_entry_sign: First- or Third-party code 
Assume that developers at other organizations have
done their due diligence. Assume that platform SDKs are performing as intended. If you discover
anything to the contrary, file a bug with the original development team. Their code is not 
your responsibility.

##### :no_entry_sign: Boilerplate code

##### :no_entry_sign: Simple, easy-to-read code
For example, a method that converts characters to uppercase, 
or does simple math, is a good candidate to avoid testing.

# Tests: How To
See [Mobiquity Calculator iOS Unit Tests](https://github.com/Mobiquity/iOSUnitTests) for an example project.

### The easiest way to test is to write simple code
Writing code that follows single-responsibility principle, has one task (or type of task), and has few dependencies makes testing much easier.

### Dependency-injection 
When you need to add tests to already existing code, sometimes fullscale refactoring isn't an option. In this case, prefer [dependency injection](https://medium.com/ios-os-x-development/dependency-injection-in-swift-a959c6eee0ab), using protocol-defined objects, to mock objects that you may not have control over or objects that are too complicated to test immediately.

### Setting up a Unit Test Project
See [Apple's Quick Start guide](https://developer.apple.com/library/content/documentation/DeveloperTools/Conceptual/testing_with_xcode/chapters/02-quick_start.html#//apple_ref/doc/uid/TP40014132-CH2-SW3) for a guide on how to set up a Unit Test target for your project. 

### Writing tests
A general formula for a unit test is to:
1. Arrange - set up the input or preconditions for your test
2. Act - perform your action
3. Assert - confirm that output matches expectations

See [XCAssert Documentation](https://developer.apple.com/library/content/documentation/DeveloperTools/Conceptual/testing_with_xcode/chapters/04-writing_tests.html#//apple_ref/doc/uid/TP40014132-CH4-SW34) for information on the various Assert statements available for testing.
### Tools
- [OCMock](http://ocmock.org) 
- [OCMock / Swift](http://ocmock.org/swift) As described within, OCMock does not fully support Swift and there are no immediate plans for Swift support. 
- [Apple: Writing Test Classes and Methods](https://developer.apple.com/library/content/documentation/DeveloperTools/Conceptual/testing_with_xcode/chapters/04-writing_tests.html) Swift itself is well-designed to allow for easy testing, mocking and data manipulation need for most environments. 

# Continuous Integration

* * *
_Heavily inspired by [Selective Unit Testing – Costs and Benefits](http://blog.stevensanderson.com/2009/11/04/selective-unit-testing-costs-and-benefits/)_
