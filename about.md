---
layout: page
permalink: /about/index.html
title: Sergio Enrech Trillo
tags: [Sergio, Enrech, Trillo, tigretoncio, developer]
chart: true
---
<figure>
  <img src='/images/about/tigretoncio.jpg' width="50%" height="50%" />
  <figcaption>Fighting the tiger in Oslo</figcaption>
</figure>

{% assign total_words = 0 %}
{% assign total_readtime = 0 %}
{% assign featuredcount = 0 %}
{% assign statuscount = 0 %}

{% for post in site.posts %}
    {% assign post_words = post.content | strip_html | number_of_words %}
    {% assign readtime = post_words | append: '.0' | divided_by:200 %}
    {% assign total_words = total_words | plus: post_words %}
    {% assign total_readtime = total_readtime | plus: readtime %}
    {% if post.featured %}
    {% assign featuredcount = featuredcount | plus: 1 %}
    {% endif %}
{% endfor %}

Welcome to my blog.

I have just graduated from Makers Academy Remote at <a href="http://www.makersacademy.com/" target="_blank">Makers Academy</a>, the European leading bootcamp providing an intense 4 months practical training, simulating an agile corporation environment and applying agile techniques such as user stories, weekly retrospectives, XP values, pair programming or scrum teams, and learning by coding using languages such as Ruby or JavaScript.  It was very intense, working long hours to succeed on the challenges, and I loved it.

Previously I have done a few other things, from working for multinationals to start ups, but I felt the call of code and there can't be any other way, I must develop as a way of life.

I am also very interested in the microsoft framework, and currently learning C# by myself, using the fantastic resources available at <a hreg="https://www.pluralsight.com/" target="_blank">Pluralsight</a>.  But I am also interested by Web technologies such as JavaScript, Angular and of course Ruby and Ruby on Rails!

> My desire is to get a developer role where I can continuously learn and become a truly respected professional in the field.


Thank you for visiting! If you like to see a bit more of my work, please visit my <a href="https://github.com/tigretoncio" target="_blank">GitHub account</a> or <a href="mailto:senrech@gmail.com?Subject=Hi%20Sergio!" target="_top">
send me a message</a>