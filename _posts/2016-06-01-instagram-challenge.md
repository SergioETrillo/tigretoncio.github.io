---
layout: post
title: "Week 7 - Instagram challenge"
description: Comments about the seventh weekend challenge of Makers Academy.
modified: 2016-06-06
category: portfolio
imagefeature: camera.jpg
comments: true
---

The seventh week of course introduced a new framework: Ruby on Rails. Ruby is a general-purpose programming language, though it is best known for its use in web programming. Rails is a ruby gem that extends the Ruby programming language. Rails combines Ruby with HTML, CSS and JavaScript to create web applications that run on a web server (that is why Rails is considered a server-side or backend framework).

> The weekend challenge was building a simplified clone of instagram on Ruby on Rails where **users** can post **pictures**, write **comments** on pictures and **like** a picture. As a bonus, styling the website like the real instragram's site (or more awesome).

During the week we learned how Rails applications are organized using a pattern that other developers would recognize. Code is easier to write, understand and maintain if it fits a pattern you are familiar with. In this case, that pattern is again Model-View-Controller.

The goals of this exercise were:

  * Understand how Rails applications are organized. How to separate concerns and responsabilities applying correctly the MVC pattern. What are the actions of the controllers ?, how should I present the information to the user (*views*), what database tables do I need (*models*) ?...

  * Getting familiar with database migrations.

  * Use correctly the Gemfile and separate the gems into groups according to the purpose of them (test, development, production).

  * Search the appropriate gems that help us solving the challenge. In this case, I used **Cloudinary**, which is an end-to-end image management solution for websites and mobile apps. My instagram clone uses Cloudinary for image uploads, storage and simple manipulations. Another gem used in this project is **acts_as_votable** which allows records (pictures) to be votable. Another important gem used for this project is **devise**, a flexible authentication solution for Rails.

  * Experiment with styling frameworks. This app uses Bootstrap, a combination of HTML, CSS and JavaScript code designed to help build user interface components (Front-end-Framework).

  * How to prevent sensible data, like API keys and passwords from being published on GitHub using environment variables both locally and on Heroku. Ex:
  ```ruby
  production:
  cloud_name: ENV["CLOUDINARY_CLOUD_NAME"]
  api_key: ENV["CLOUDINARY_API_KEY"]
  api_secret: ENV["CLOUDINARY_API_SECRET"]
  enhance_image_tag: true
  static_image_support: true
  ```

  * Use Test-Driven Development as a development cycle (red-green-refactor). Implement feature and unit test in order to test the app and find regressions.

You can see my work on this GitHub <a href="https://github.com/omajul85/instagram-challenge" target="_blank">repo</a>. The application has been deployed on Heroku. You can share your images with the world <a href="https://instagram-omajul85.herokuapp.com/" target="_blank">here</a>.
