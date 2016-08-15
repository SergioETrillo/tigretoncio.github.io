---
layout: post
title: "Advent of Code, Day 2"
description: JS article
modified: 2016-07-12
category: Algorithms
imagefeature: alg.jpg
comments: true
---

To keep coding everyday, I have decided to go through the [Advent of Code](http://adventofcode.com/) challenges

# Day 2

Instructions for day 2 are available [here](http://adventofcode.com/day/2).  In a nutshell, the elves wants to know how much wrapping paper is needed for gifts.  All gifts are boxes, and the required paper area is the area of the box, plus the area of the smallest side of the box as margin. A list of boxes sizes is provided as data input.

## About the problem

Again relatively simple, however there are a few things to consider, such as:

- Recovering and formatting of data
- Calculations as per the box area formula, adding the margin

## Solution discussion

My first thought was to recover the data from the website itself, in order to make the calculations.  Using ruby there are numerous gems that can be used to retrieve data from the web, after a quick trip to [SO](www.stackoverflow.com) I decided to use Nokogiri.

However, I found a problem and Nokogiri was giving an error when trying to download the HTML data.  I was searching a bit the problem and I think the problem is due to the fact that to retrieve the data the user must logged in, and I could not reproduce that in my ruby program.  As this was not the focus of the exercise I decided then to store the data in a file, and have the code read it.

## The code

The code I generated is:

<script src="https://gist.github.com/tigretoncio/ea3f6119006546c20d6e4e27311d7d64.js"></script>

In this occasion I thought it relevant to create a class to manage the problem solution.  I tried to applied some of the [SOLID](http://www.davesquared.net/2009/01/introduction-to-solid-principles-of-oo.html) principles, mainly the Single Responsibility Principle (SRP), and tried to extract behaviour in different methods, separating the different responsibilities to read the data from file, of formatting data and iterating through the data to perform the calculations and add the total.  The only public method main() method calls for the relevant methods to perform the calculation.

Instantiating a new object WrappingPaper and invoking the main() method provides the right solution, (i.e. in the REPL w = WrappingPaper.new; w.main() )

## Refactoring

Refactoring is a continous process and pretty much depend on time available, (which is always not much), and the amount of change that the code is expected to endure, (which is often underestimated).  In this case I was refactoring to separate logic following SRP, and perhaps a bit more of refactoring would be required to extract the long calculation operand into their own methods, to provide legibility to the program.  I am sure I am missing quite a lot of things, but at least it calculates the 1000 input entries in a breezy and provides the right answer, cool! :)

# Part 2

Ok now the elves also require to calculate so much ribbon required.  It seems that the ribbon required to wrap a present is the shortest distance around its sides, and of top of that they require an extra length of ribbon equal to the cubic feet of volume of the present.

# The code

I generated this:

<script src="https://gist.github.com/tigretoncio/10bbd799bc1ad89baba2432b246cad95.js"></script>

(that includes the previous solution, with some refactoring done)

# Code discussion

Again I was trying to separate all different code functionalities to ensure that was clean and maintainable.  I thought about the possibility of joining this function into the previous one, with some selector, (calculate wrap or ribbon depending on an argument input), but that looked more complex and imo did not provided any added value.  So I created parallel methods for the ribbon calculation using the same structure.

And I got a star and the line 2 of the tree iluminated!



