---
layout: page
permalink: /about/index.html
title: Omar Alvarez
tags: [Omar, Alvarez, omajul, omajul85, developer]
chart: true
---
<figure>
  <img src='/images/about/mi-acordeon.jpg'>
  <figcaption>In Piedecuesta, Colombia</figcaption>
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

My name is **Omar Alvarez**, and this is my personal blog. It currently has {{ site.posts | size }} posts in {{ site.categories | size }} categories which combinedly have {{ total_words }} words, which will take an average reader ({{ site.wpm }} WPM) approximately <span class="time">{{ total_readtime }}</span> minutes to read. {% if featuredcount != 0 %}There are <a href="{{ site.url }}/featured">{{ featuredcount }} featured posts</a>, you should definitely check those out.{% endif %} The most recent post is {% for post in site.posts limit:1 %}{% if post.description %}<a href="{{ site.url }}{{ post.url }}" title="{{ post.description }}">"{{ post.title }}"</a>{% else %}<a href="{{ site.url }}{{ post.url }}" title="{{ post.description }}" title="Read more about {{ post.title }}">"{{ post.title }}"</a>{% endif %}{% endfor %} which was published on {% for post in site.posts limit:1 %}{% assign modifiedtime = post.modified | date: "%Y%m%d" %}{% assign posttime = post.date | date: "%Y%m%d" %}<time datetime="{{ post.date | date_to_xmlschema }}" class="post-time">{{ post.date | date: "%d %b %Y" }}</time>{% if post.modified %}{% if modifiedtime != posttime %} and last modified on <time datetime="{{ post.modified | date: "%Y-%m-%d" }}" itemprop="dateModified">{{ post.modified | date: "%d %b %Y" }}</time>{% endif %}{% endif %}{% endfor %}. The last commit was on {{ site.time | date: "%A, %d %b %Y" }} at {{ site.time | date: "%I:%M %p" }} [UTC](http://en.wikipedia.org/wiki/Coordinated_Universal_Time "Temps Universel Coordonné").

I am a Ronin student at <a href="http://www.makersacademy.com/" target="_blank">Makers Academy</a>. Originally from Colombia, I have lived in France for the last 5 years. I studied a M.Sc. in Systems engineering specialised in Image and Sound at the University of Valenciennes. I completed an internship at Technicolor working in a R&D department dedicated to digital watermarking. The project I worked on was **Video Watermarking for HTTP Adaptive Streaming**.For more information on this topic, here is the <a href="https://www.dropbox.com/s/j1hvfdd4ldbgwju/icassp2014.pdf" target="_blank">link</a> to our paper.

After that intense experience, I wanted to try something new, so I decided to move to Paris and work in the broadcasting industry. I have worked as a support engineer at <a href="http://www.dalet.com/" target="_blank">Dalet</a> for the last 2 years. This work gave me the opportunity of working for TV and Radio channels from all around the world.

> Now, my desire is to go back to the development field. This time I want to go deeper into web. That is why I applied to Makers. 

When I am not programming, I like to play music and discover new instruments (the photo above is my latest purchase). Also I love cooking and experimenting with exotic flavours.

I hope this blog gives you an insight into the life of someone that aspires to work as a developer. I will try to keep you updated on my progress during my adventure as Roniner at Makers. 