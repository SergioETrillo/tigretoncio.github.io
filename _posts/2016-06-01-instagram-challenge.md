---
layout: post
title: "Week 7 - Instagram challenge"
description: Comments about the seventh weekend challenge of Makers Academy.
modified: 2016-06-06
category: portfolio
imagefeature: camera.jpg
comments: true
---

The seventh week of course introduced a new framework: <a href="http://rubyonrails.org/" target="_blank">Ruby on Rails</a>. Ruby is a general-purpose programming language, though it is best known for its use in web programming. Ruby on Rails is a web application framework created in Ruby that allows the creation of complex websites. Rails uses the model-view-controller (MVC) framework and provides default structures for a database, a web service and web pages.

> The weekend challenge was building a simplified clone of instagram on Ruby on Rails where users can post pictures, and write comments and like them.

This was an intense week to learn Ruby on Rails in a week.  However with the intense work previously done on Ruby and with a lot of motivation, it was possible to be done.

There was quite a lot of new technology added here, apart from Ruby on Rails I needed something to manage the pictures, (Paperclip gem), and also a platform to store them, as Heroku is not design to store an important amount of data.  So I used <a href="https://aws.amazon.com/" target="_blank">Amazon Web Services</a>, profiting of their 1 year free offer, (I used their fantastic storage service AWS S3).  I also used devise to manage user authentication, Factory Girl to create objects for test, Simple Form gem to create easy forms, and a few other gems, bits and pieces.

The code is <a href="https://github.com/tigretoncio/instagram-challenge" target="_blank">available here</a>, and the app is stored in Heroku <a href="https://pichagram.herokuapp.com/" target="_blank">here</a>

The goals of this exercise were:

  * Practice in the use of Ruby on Rail applications, and the MVC framework

  * Practice the database aspect using ActiveRecord which is the ORM used by Rails.

  * Practice the search and use of many different Gemfiles in an application, separating through groups depending on the software development live cycle, (development, test, production)

  * Experiment with presenting data. Although I did not have a lot of time to "make it beautiful" and it is in my to-do list.

  * Ensure sensitive data does not appear in the code and publicly available on GitHub.

  * Continue the practice of Test-Driven Development to ensure good test coverage, which is a very important feature in applications that change often, (all successful ones).

