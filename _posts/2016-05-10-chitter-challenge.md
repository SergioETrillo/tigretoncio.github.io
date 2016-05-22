---
layout: post
title: "Week 4 - Chitter challenge"
description: Comments about the fourth weekend challenge on my Ronin adventure
modified: 2016-05-10
category: personal
imagefeature: chitter.jpg
comments: true
---

The challenge for the fourth week was building a simplified Twitter clone that will allow users to post messages (aka peeps) to a public stream. This challenge requires the implementation of user authentication process. 

Different technologies are used in this project:

* **Sinatra (including usage of Partials and Flash):** Sinatra is a web application library that focuses on "quickly creating web-applications in Ruby with minimal effort".

* **DataMapper:** An Object Relational Mapper (ORM) written in Ruby. In computer science, ORM is a programming technique for converting data between incompatible type systems in object-oriented programming languages. By using DataMapper our model objects gain the ability to communicate with the database and treat the table columns as Ruby attributes.

* **Database cleaner:** Set of strategies for cleaning your database in Ruby. Database cleaner ensures a clean state during tests.

* **Bcrypt:** This gem allows developers to easily harden the applications against attacks attempting to steal password information from users. It is our responsibility as a web developer to make our web applications secure.

* **Rake:** Rake is *Ruby make*, a make-like language written in Ruby. Rake is used extensively, especially for the innumerable little administrative tasks necessary when developing database-backed web applications. In this case, the main tasks are upgrading or migrating our database.

You can see my work on this GitHub <a href="https://github.com/omajul85/chitter-challenge" target="_blank">repo</a>. The application has been deployed on Heroku. You can share your peeps with the world <a href="https://chitter-omajul85.herokuapp.com/" target="_blank">here</a>.