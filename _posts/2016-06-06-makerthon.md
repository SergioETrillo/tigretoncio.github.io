---
layout: post
title: "Week 8 - Makerthon"
description: Comments about the Makerthon (group project in 4 days).
modified: 2016-06-06
category: portfolio
imagefeature: summer.jpg
comments: true
---

Week 8 was fully dedicated to Makerthon. Makerthon is a code marathon where a group of 4-5 student work on a project that is decided monday morning and must be presented the very same week on friday afternoon. The projects are taken from a list of ideas that were selected on a previous brainstorming session.

The project in which I participated was a holiday planner application extracted from the folowing idea:

> Make an application that helps people to plan the activities for their next summer.

With that idea in mind, there were no further details or indications for the language or framework we should use to code this app. The goal was to work as a team, organize our work for doing pair-programming, follow the agile methodology for the development cycle and apply the [XP-values as](http://www.extremeprogramming.org/values.html) much as we can.

From the very beginning we decided to build an AngularJS application that interacts with external APIs in order to collect data that is organized and presented to the users. More concretely, the 
You can see our work on this GitHub <a href="https://github.com/tigretoncio/I-know-what-you-will-do-this-summer" target="_blank">repo</a>. The application has been deployed on Heroku. You can find your next holiday destination <a href="http://holiday-planner.herokuapp.com/" target="_blank">here</a>.

These are the **skills** that I acquired after this week:

  - **Testing with Jasmine:** Write simple test for the JavaScript objects used on the application.

  - **jQuery:** I wrote some functions using jQuery in order to animate the behaviour of the game and give it some dynamism. The buttons of the game, used for selecting the number of pins knocked down, change dynamically in order to avoid wrong input from user and also provide a simpler game experience (instead of typing the number of pins on a form for example).

  - **JavaScript:** Understand some similarities and differences of JavaScript in comparison with Ruby. How to create objects (not classes) in JavaScript, what is a constuctor, why use prototypes, etc.

  - **Google chrome DevTools:** Used to efficiently track down layout issues, test JavaScript code on the console, inspect the HTTP requests of my controllers and get insights for code optimization.

  - **State machine model:** Although there are several ways to solve this challenge, I decided to base my solution on the Finite-state machine (FSM) modeling. A particular FSM is defined by a list of its states, and the triggering condition for each transition. The states represent different situations during a bowling game such as: rolling the first ball in a frame, rolling the second ball in a frame, scoring a strike, and so on. The states change from one to another by a triggering event or condition (aka transition), which in this case are the pins knocked down when rolling a ball and the possible bonus when scoring a spare or strike. 

  The image below is a state diagram for a bowling game:

  ![Diagram](http://s19.postimg.org/408xieodv/Graph.png)

