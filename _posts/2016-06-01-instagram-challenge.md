---
layout: post
title: "Week 7 - Instagram challenge"
description: Comments about the seventh weekend challenge of Makers Academy.
modified: 2016-06-06
category: personal
imagefeature: camera.jpg
comments: true
---

The seventh week of course introduced a new framework: Ruby on Rails. Ruby is a general-purpose programming language, though it is best known for its use in web programming. Rails is a ruby gem that extends the Ruby programming language. Rails combines Ruby with HTML, CSS and JavaScript to create web applications that run on a web server (that is why Rails is considered a server-side or backend framework).

> The weekend challenge was building a simplified clone of instagram on Ruby on Rails where **users** can post **pictures**, write **comments** on pictures and **like** a picture. As a bonus, styling the website like the real instragram's site (or more awesome).

During the week we learned how Rails applications are organized using a pattern that other developers would recognize. Code is easier to write, understand and maintain if it fits a pattern you are familiar with. In this case, that pattern is again Model-View-Controller. The model manages the data, logic and rules of the application. The view represents how the information is displayed to users. The controller accepts input and converts it to commands for the model or view. More specifically, the model in this challenge consists of those elements that are going to be stored on a database such as the users, the pictures and the comments. The views are the different files that are going to display information as a webpage on a browser (ERB, HTML, CSS) and the controllers, such as `pictures_controller` or `comments_controller`, coordinate the interaction between the user, the views and the model. Controllers are responsible for routing external requests to internal actions that create, read, update and delete (CRUD) resources (information on databases).

You can see my work on this GitHub <a href="https://github.com/omajul85/instagram-challenge" target="_blank">repo</a>. The application has been deployed on Heroku. You can share your images with the world <a href="https://instagram-omajul85.herokuapp.com/" target="_blank">here</a>.

These are the **skills** that I acquired after this week:

  - **Testing with Jasmine:** Write simple test for the JavaScript objects used on the application.

  - **jQuery:** I wrote some functions using jQuery in order to animate the behaviour of the game and give it some dynamism. The buttons of the game, used for selecting the number of pins knocked down, change dynamically in order to avoid wrong input from user and also provide a simpler game experience (instead of typing the number of pins on a form for example).

  - **JavaScript:** Understand some similarities and differences of JavaScript in comparison with Ruby. How to create objects (not classes) in JavaScript, what is a constuctor, why use prototypes, etc.

  - **Google chrome DevTools:** Used to efficiently track down layout issues, test JavaScript code on the console, inspect the HTTP requests of my controllers and get insights for code optimization.

  - **State machine model:** Although there are several ways to solve this challenge, I decided to base my solution on the Finite-state machine (FSM) modeling. A particular FSM is defined by a list of its states, and the triggering condition for each transition. The states represent different situations during a bowling game such as: rolling the first ball in a frame, rolling the second ball in a frame, scoring a strike, and so on. The states change from one to another by a triggering event or condition (aka transition), which in this case are the pins knocked down when rolling a ball and the possible bonus when scoring a spare or strike. 

  The image below is a state diagram for a bowling game:

  ![Diagram](http://s19.postimg.org/408xieodv/Graph.png)

