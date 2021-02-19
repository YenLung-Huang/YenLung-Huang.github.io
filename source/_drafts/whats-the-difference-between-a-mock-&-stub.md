---
title: What's difference between a mock & stub?
date: 2019-07-21 20:55:30
tags:
 - test
---

## Stub

I believe the biggest distinction is that a stub you have already written with predetermined behavior. So you would have a class that implements the dependency (abstract class or interface most likely) you are faking for testing purposes and the methods would just be stubbed out with set responses. They would not do anything fancy and you would have already written the stubbed code for it outside of your test.

## Mock

A mock is something that as part of your test you have to setup with your expectations. A mock is not setup in a predetermined way so you have code that does it in your test. Mocks in a way are determined at runtime since the code that sets the expectations has to run before they do anything.

## Difference between Mocks and Stubs

Tests written with mocks usually follow an initialize -> set expectations -> exercise -> verify pattern to testing. While the pre-written stub would follow an initialize -> exercise -> verify.

## Similarity between Mocks and Stubs

The purpose of both is to eliminate testing all the dependencies of a class or function so your tests are more focused and simpler in what they are trying to prove.


## Foreword
There are several definitions of objects, that are not real. The general term is test double. This term encompasses: dummy, fake, stub, mock.

## Reference
According to [Martin Fowler's article](http://martinfowler.com/articles/mocksArentStubs.html):


```
* Dummy objects are passed around but never actually used. Usually they are just used to fill parameter lists.
* Fake objects actually have working implementations, but usually take some shortcut which makes them not suitable for production (an in memory database is a good example).
* Stubs provide canned answers to calls made during the test, usually not responding at all to anything outside what's programmed in for the test. Stubs may also record information about calls, such as an email gateway stub that remembers the messages it 'sent', or maybe only how many messages it 'sent'.
* Mocks are what we are talking about here: objects pre-programmed with expectations which form a specification of the calls they are expected to receive.
```

## Style
Mocks vs Stubs = Behavioral testing vs State testing

## Principle
According to the principle of Test only one thing per test, there may be several stubs in one test, but generally there is only one mock.

## Lifecycle
Test lifecycle with stubs:

Setup - Prepare object that is being tested and its stubs collaborators.
Exercise - Test the functionality.
Verify state - Use asserts to check object's state.
Teardown - Clean up resources.
Test lifecycle with mocks:

Setup data - Prepare object that is being tested.
Setup expectations - Prepare expectations in mock that is being used by primary object.
Exercise - Test the functionality.
Verify expectations - Verify that correct methods has been invoked in mock.
Verify state - Use asserts to check object's state.
Teardown - Clean up resources.

## Summary
Both mocks and stubs testing give an answer for the question: What is the result?

Testing with mocks are also interested in: How the result has been achieved?

# Another
A stub is a simple fake object. It just makes sure test runs smoothly.
A mock is a smarter stub. You verify your test passes through it.
