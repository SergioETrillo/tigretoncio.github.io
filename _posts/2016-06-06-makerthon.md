---
layout: post
title: "Week 8 - Makerthon"
description: Comments about the Makerthon (group project in 4 days).
modified: 2016-06-06
category: portfolio
imagefeature: summer.jpg
comments: true
---

Week 8 was fully dedicated to Makerthon. Makerthon is a code marathon where a group of 4-5 students work on a project that is agreed on Monday morning and must be presented the very same week on Friday afternoon. The projects are taken from a list of ideas that were selected on a previous brainstorming session.

The project in which I participated was a holiday planner application extracted from the following idea:

> Make an application that helps people to plan the activities for their next summer.

With that idea in mind, there were no further details or indications for the language or framework we should use to code this application. The goal was to work as a team, organize our work for doing pair-programming, follow the agile methodology for the development cycle and apply the [XP-values as](http://www.extremeprogramming.org/values.html) as much as we can.

From the very beginning we decided to build an AngularJS application that interacts with external APIs in order to collect data that is organized and presented to the users. More concretely, the application uses the Yelp API in order to get some data about a possible destination. The user selects some options on a form and then uses a search field to type the kind of activity he/she is looking for. In addition, the application uses the Wunderground API in order to provide the current weather of the selected destination.

The most interesting challenge of this project was the integration of the Yelp API. Yelp uses OAuth 1.0a for authenticating API requests as per the OAuth specification (Accessing Protected Resources). Each request must contain several parameters such as the consumer key, a token, a timestamp, etc. With these parameters Oauth generates a signature that allows the application to send the API request. The problem we encountered is that our application could send only one API request when clicking on the submit button of the form. If the user changes some fields of the form, subsequent clicks on the submit button won't trigger any API request. That is due to the fact that each API request requires a unique signature provided by OAuth. One workaround would be refreshing the page, but that option also deletes all the fields of the form. The solution that we found was regenerating the parameters required for the signature every time the user changes the form. This is done using the Angular directive **ng-change**. There are mainly two functions to workaround the problem: a reset function that simply clears the old values of the parameters, and an update function that invokes reset and set new values for each parameter. Once the new parameters are set, the system generates a new signature and the API request can be sent. The trick is that all the fields in our form use the ng-change directive, so the reset/update functions are invoked every time the user changes the form. By doing so, there is no need to refresh the page for multiple queries.

Another interesting part of the project was the creation of our own API. It is simply an API that provides information about different holidays destinations. By selecting different categories, the API provides a destination with the bigger score. The score is calculated by counting the number of categories that match the choice of the user for each one of the destinations managed by the API. The city with more matches is suggested to the user.

These are the **skills** that I acquired after this week:

  - **API integration with Angular:** Design and implementation of the different controllers and services.

  - **Waffle:** We have used Waffle to manage our GitHub issues, keep track of the progress, do the Quality Assurance and split the work for the different members of the group. This is a good tool for pair-programming, specially when the team work is done remotely.

  - **API in Rails:** This project was a first point of contact with the development of RESTful APIs in Rails.

  - **Bootstrap:** Even though is not one of the strongest goals for the week, we have done a good job in terms of styling the application and make it user friendly and attractive. We have used the Bootstrap framework to glamourize the site. 

  - **Deployment on Heroku:** Deploy an Angular application to Heroku was also a challenge this week. It required the usage of node.js and express. Adding the right dependencies was important to make the application working in production.

You can see our work on this GitHub <a href="https://github.com/tigretoncio/I-know-what-you-will-do-this-summer" target="_blank">repo</a>. The application has been deployed on Heroku. You can find your next holiday destination <a href="http://holiday-planner.herokuapp.com/" target="_blank">here</a>.

