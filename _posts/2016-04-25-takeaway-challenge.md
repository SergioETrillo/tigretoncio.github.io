---
layout: post
title: "Week 2 - Takeaway challenge"
description: Introducing the Twilio API
modified: 2016-04-25
category: personal
imagefeature: takeaway.jpg
comments: true
---

The challenge of the second week of course was related to OOP in Ruby and the usage of 3rd party software. Particularly, we had to use the Twilio API in order to send SMS-notifications. Our application is a simple takeaway that handles orders from customers on a predefined menu. The takeaway has to notify the customer that the order has been placed by sending a SMS. You can see my solution for the challenge <a href="https://github.com/omajul85/takeaway-challenge" target="_blank">here</a>. 

The goals of this exercise were:

  - Understand the importance of using a Gemfile to list the gems used in our application. By doing so, all the project dependencies can be pulled in whenever the project is checked out on a new machine.
  - Stubbing the Twilio API. This API provides access to an online service. If we do not stub this, we will send test SMS everytime we run our test, which is not a good thing.
  - Test explicitely **every** element of the public interface.
  - Improve the way we desing our application. This implies an appropriate use of Dependency Injection in order to respect the Single Responsability Principle. We do not want classes that do too much things. In addition, this was a good opportunity to refactor efficiently.
  - Use the dotenv gem to ensure that sensitive infomration such as phone numbers and security tokens are not pushed up to public repos on Github. 
  - Improve our style and indentation by using tools to analyze our code for violations.

To be continued...