---
layout: post
title: "Week 4 - Chitter challenge"
description: Comments about the fourth weekend challenge of Makers Academy.
modified: 2016-05-10
category: portfolio
imagefeature: chitter.jpg
comments: true
---

This week has exposed something very important to create a web application: Databases! Concepts of relational databases have been exposed and practiced, together with security considerations, (user authentication), and more feature testing using Capybara.

The weekend challenged involved to build a Twitter "clone" allowing users to send messages (_peeps_). Users must sign up with their email and usernames to write peeps, but they can read peeps without login.



The main new technologies used for this project are:

  * <u>DataMapper</u>: An Object Relational Mapper (ORM) written in Ruby.  It allows to use the database functions at developer level without the need of using SQL queries. By using DataMapper our model objects gain the ability to communicate with the database and treat the table columns as Ruby attributes.

  * <u>BCrypt</u>: BCrypt is a Ruby Gem that allows to <a href="https://codahale.com/how-to-safely-store-a-password/" target="_blank">safely store a password.

  * <u>PostgreSQL</u>: PostgreSQL is a very popular open source object-relational database.

  * <u>Rake</u>: Rake is Ruby make, a make-like language written in Ruby, to deal with tasks and dependencies.

  * <u>Heroku</u>: <a href="https://www.heroku.com/" target="_blank">Heroku</a> is a great cloud platform as a service that allows people to build and deliver apps.


You can see my work on this GitHub <a href="https://github.com/tigretoncio/chitter-challenge" target="_blank">repo</a>. The application has been deployed on Heroku. You can share your peeps with the world <a href="https://cheeter-challenge-sergio.herokuapp.com" target="_blank">here</a>.