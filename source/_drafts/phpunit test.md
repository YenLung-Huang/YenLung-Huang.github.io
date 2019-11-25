---
title: phpunit test
date: 2019-08-02 22:21:11
tags:
---
1. New Operators
The principles of unit testing dictate that we should test in isolation. We’ll cover this concept more
in future chapters, but, in short, your goal should be to test the current class, and nothing else. Don’t
access the database, don’t test that your Filesystem class fetches some data from a web service.
Those should have their own tests, so don’t double up.

“I usually re-evaluate any classes with more than four [dependencies].” - Taylor Otwell⁷

Unit Testing
Think of unit testing as going over your classes and methods with a fine-tooth comb, ensuring that
each piece of code works exactly like you expect. Unit tests should be executed in isolation, to make
the process of debugging as easy as possible. 80% of your tests will be in this style.
If it helps, when you think of unit testing, think one object, and one object only. If a test fails, you
know exactly where to look.

Model Testing
Some members of the Ruby on Rails community associate model testing (even when these tests
touch the database) with unit testing. This unfortunately can be a bit misleading. Unit tests should
be isolated from all external dependencies. Once you ignore this basic rule, you’re no longer unit
testing. You’re writing integration tests (more on that shortly).
In this book, when we test our models, we’ll stay true to the traditional definition of unit testing,
unless specified otherwise.
Imagine that a method in your model is responsible for sending an email. If following good design
patterns, you’ll likely have a class that is dedicated to sending email (single responsibility priniciple).
This presents a problem, however: how do we successfully unit test this method, if it calls an external
Mailer class? The answer is to use mocks, which we’ll cover extensively in this book. A mock allows
us to fake the Mailer class, and write an expectation to ensure that the proper method is called. This
Chapter 1: Test All The Things 19
way, even if the Mailer component is currently broken (it will have its own tests), we can still verify
whether or not the model method is working as expected.
Integration Testing
If a unit test verifies that code works correctly in isolation, then an integration test will fall on the
other end of the spectrum. These tests will flex multiple parts of your application, and typically
won’t rely on mocks or stubs. As such, be sure to create a special test database.
As an example, think of a car. Sure, the engine and fuel injection system might individually work
as expected (each passes its own set of unit tests), but will they work when grouped together?
Integration testing verifies this.
Functional (Controller) Testing
What do you call the process of testing a controller? Some frameworks may refer to this as functional
testing (and it is), but we’ll simply stick with - wait for it - controller testing!
More traditionally, think of functional testing as a way for you and your team to ensure that the code
does what you expect. While unit tests verify each unit of a class, functional testing is a bit broader
and can trigger multiple pieces of your application. Most frequently, these tests will be triggered
from the outside in, which is why they’re also commonly referred to as System Tests. One important
note is that functional tests typically won’t require a server to be running.
Acceptance Testing
You’ve already learned that functional testing ensures that the code meets the requirements of the
development team. However, there will be cases when, even though the tests return green, the
final implemented feature will not meet the requirements of the client. This is what we refer to as
acceptance testing. In other words, does this code meet the requirements of the client? Your software
can pass all unit, functional, and integration tests, but still fail the acceptance tests, if the client or
customer realizes that the feature doesn’t work as they expected.


### TDD
1. Arrange: Set the stage, instantiate objects, pass in mocks.
2. Act: Execute the thing that you wish to test.
3. Assert: Compare your expected output to what was returned

### BDD
Given
1. Given: Given this set of data,
2. When: when I perform this action,
3. Then: then I expect that response.