---
layout: post
title: "Week 3 - Rock-Paper-Scissors challenge"
description: Comments about the third weekend challenge on my Ronin adventure
modified: 2016-05-02
category: personal
imagefeature: rps.jpg
comments: true
---

After two weeks of OOP in Ruby, several GitHub repos and more pairing programming than recommended by the doctor, we started the third week with an introduction to the web. We learnt the internet basics such as the relation between client and servers, the HTTP protocol, the `GET` and `POST` requests, and so on. The framework used to build our first web application was Sinatra and the tools used for TDD the application were Rspec and Capybara.

The challenge was building the game Rock, Paper, Scissors for one player (Man vs. CPU). My version includes the two players mode and also an extended version of the game, with Lizard and Spock. See the <a href="https://en.wikipedia.org/wiki/Rock-paper-scissors" target="_blank">wikipedia article</a> for more details about the game.

The goals of the challenge were understanding the client-server communication via requests **GET** and **POST**, the usage of HTML forms, test-driven the development of the application using Capybara feature tests, and learn how to create a simple website with Sinatra. 

>I learnt how a Sinatra project applies the MVC structure in order to follow the idea of separation of concerns and organise the code in different layers. 

You can see my work on this GitHub <a href="https://github.com/omajul85/rps-challenge" target="_blank">repo</a>. The application has been deployed on Heroku and you can play with it <a href="https://rps-omajul85.herokuapp.com/" target="_blank">here</a>.

These are the **skills** that I acquired after this week:

  - **Build simple applications in Sinatra:** This framework was a good starting point to understand the MVC pattern for implementing user interfaces on computers. 
  
  - **HTML and CSS:** Although it has not been the strong point of this challenge, I dedicated some time to improve the front-end using CSS. 
  
  - **Ruby classes on web applications:** The first two weeks provided me a better understanding of Ruby and OOP. This third week was crutial to understand how to use classes to program the business logic (models) of the project. For example, the game has been modeled using three classes: `Game`, `Player` and `Computer` (that inherits from `Player`).

  - **Capybara:** This challenge was an opportunity to work with the Capybara library (written in Ruby). This library provides the code to simulate how a user interacts with the application. I have used Capybara and Rspec to write the feature tests and verify that the application works as expected.