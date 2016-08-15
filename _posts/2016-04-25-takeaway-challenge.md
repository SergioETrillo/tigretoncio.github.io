---
layout: post
title: "Week 2 - Takeaway challenge"
description: More OOP, introduction to APIs
modified: 2016-04-25
category: portfolio
imagefeature: takeaway.jpg
comments: true
---

The second week involved further Object Oriented Programming in Ruby, and the use of external APIs to enhance our software.  I used the <a href="https://www.twilio.com/docs/api/rest">Twilio API</a> to send SMS notifications for a fast-food order program, once the order is placed.  The code for this challenge is <a href="https://github.com/tigretoncio/takeaway-challenge" target="_blank">available here</a>

This challenge helped me to learn about:

  * The importance of using a <a href="http://tosbourn.com/what-is-the-gemfile/" target="_blank">Gemfile</a> in Ruby to list the gems used in our application. That way the program is portable to any other machine, as all the dependencies are listed within the Gemfile.

  * API test.  It is very important to ensure that third party APIs are properly "stubbed" to ensure the test and development do not impact in the other party's service.

  * Application test, focusing on the interface public elements, and using tools to measure test coverage (<a href="https://coveralls.io/" target="_blank">coveralls report</a>).

  * Application design, particularly the use of Dependency Injection to respect SOLID princips such as <a href="https://en.wikipedia.org/wiki/Single_responsibility_principle" target="_blank">Single Responsibility Principle</a>.

  * How to apply <a href="https://en.wikipedia.org/wiki/Test-driven_development" target="_blank">Test Driven Development</a> and the "red-green-refactor" cycle.

  * Ensure that sensitive information such as user phone numbers are not available in code that is publicly available in GitHub. (I used dotenv Gem for that).

  * Practice code style, using the right level of indentation and start using tools to analyze code for style violations, (<a href="https://houndci.com/" target="_blank">hound</a>).