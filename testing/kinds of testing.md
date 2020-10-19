# Kinds of Testing

## Questions to ask about testing

1) What kind of thing to they test?
2) When are these tests written and run?
3) What information does a failure provide?

## Unit Testing

A unit test focuses on a single “unit of code” – usually a function in an object or module. By making the test specific to a single function, the test should be simple, quick to write, and quick to run. This means you can have many unit tests, and more unit tests means more bugs caught. They are especially helpful if you need to change your code: When you have a set of unit tests verifying your code works, you can safely change the code and trust that other parts of your program will not break.

## TDD

TDD or Test-Driven Development is a process for when you write and run your tests. Following it makes it possible to have a very high test-coverage. Test-coverage refers to the percentage of your code that is tested automatically, so a higher number is better. TDD also reduces the likelihood of having bugs in your tests, which can otherwise be difficult to track down.

The TDD process consists of the following steps:

Start by writing a test
Run the test and any other tests. At this point, your newly added test should fail. If it doesn’t fail here, it might not be testing the right thing and thus has a bug in it.
Write the minimum amount of code required to make the test pass
Run the tests to check the new test passes
Optionally refactor your code
Repeat from 1

## BDD

BDD – Behavior-Driven Development – is perhaps the biggest source of confusion. When applied to automated testing, BDD is a set of best practices for writing great tests. BDD can, and should be, used together with TDD and unit testing methods.
One of the key things BDD addresses is implementation detail in unit tests. A common problem with poor unit tests is they rely too much on how the tested function is implemented. This means if you update the function, even without changing the inputs and outputs, you must also update the test. This is a problem because it makes doing changes tedious.

## Smoke tests

Sanity check for functionality