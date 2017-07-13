---
layout: post
title:  "How to think about developer tests"
date:   2017-07-12 17:22:00
categories: python
---

How to think about developer tests
====

The initial version of these notes are taken from a [Github repo][githubrepo] about testing. Later I'll expand this with examples,
which will be in Python.

* Correctness
    * Tests should prove that your code works as claimed.
    * Tests show how the code is intended to be used, what arguments to supply and what behavior or return values to expect back.
    * Tests ideally exercise every line of the code and every possible execution pathway thru the code. This is called [coverage][coverage].
    * Trapeze artists ALWAYS use safety nets. Software engineers should always use tests for the same reason.
    * After your development work in one area is done, keep running your tests there! They will notify you if other work elsewhere breaks your code. This is called [regression testing][regressiontesting].
    * Aim to write code that is easy to test - non-testable code is often bad code.
* Process stuff
    * Tests should run fast, so that you can conveniently re-run them constantly as you develop your code.
    * It's a very smart idea to set up machinery that automatically runs your tests frequently, as least once per day.
    * If your tests are so slow that you never want to run them, THEY WILL NOT HELP YOU and the time spent on them has been wasted.
    * Tests and code should be developed together: for each little piece of functionality, write a test that fails because the functional code isn’t written yet, then write code to satisfy the test.
* Be a team player
    * The tests you write as a developer should help the QA person responsible for testing your code.

[Unit tests][unittesting] are for independently testing something small in isolation (a class, or a module). Mocks are used to represent other classes,
but also things like databases or network connections or hardware, things that may be slow or unreliable. Unit tests should run very quick and you should
feel free to write LOTS of them.

[Functional][functional] or [integration tests][integration] test larger pieces of functionality spanning multiple classes or modules.

The economics of software testing
----

I am a big advocate of extensive developer testing. You probably know the rationale, but just to review, [bugs are cheaper to fix][easierfix] when they
are caught earlier and often the earliest quickest way to catch them is while you are developing the code. Some bugs can be caught while you're still
just thinking about how to develop the code, but testing encourages good habits in that phase as well.

You may be worried that writing tests will chew up valuable time in your schedule. People who do a lot of testing find that overall, tests save time,
because there are far fewer unpleasant time-consuming surprises later on.

Mocks
----

Mocks are an important enough topic to merit individual discussion.

They can be implemented with fixtures or with monkeypatch, or with the standard mock module, and are used to represent anything that you aren't immediately
testing. If you're testing a class or module that ordinarily interacts with others, those others can be mocked out. You'll also want to mock out anything
that is either slow or unreliable, such as a network connection or a database. In cases where reliability can be an issue, write tests to exercise the
possible failures.

Mocks are closely related to a testing pattern called [Dependency injection](https://en.wikipedia.org/wiki/Dependency_injection) which ALL the cool kids
are doing these days.

[//]: # Here is a comment in Markdown, see https://stackoverflow.com/questions/4823468/comments-in-markdown

[coverage]: <https://en.wikipedia.org/wiki/Code_coverage>
[regressiontesting]: <https://en.wikipedia.org/wiki/Regression_testing>
[unittesting]: <https://en.wikipedia.org/wiki/Unit_testing>
[functional]: <https://en.wikipedia.org/wiki/Functional_testing>
[integration]: <https://en.wikipedia.org/wiki/Integration_testing>
[easierfix]: <http://www.agilemodeling.com/essays/costOfChange.htm>
[githubrepo]: <https://github.com/wware/pytest-yucks>
