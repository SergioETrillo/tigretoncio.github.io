---
layout: post
title: "Advent of Code, Day 1"
description: JS article
modified: 2016-07-12
category: Algorithms
imagefeature: alg.jpg
comments: true
---

To keep coding everyday, I have decided to go through the [Advent of Code](http://adventofcode.com/) challenges.  I will provide a short explanation about the problem, and how I provided a solution.  I am sure they will be plenty other better solutions for those, I am happy to know about them if you would like to share :)

# Day 1

Instructions for day 1 are available [here](http://adventofcode.com/day/1).  Basically, Santa goes up 1 floor if the char "(" is found, and goes down 1 floor if ")" is used.  He starts in floor 0 and it's assumed no upper or lower limit.  There is a code of instructions, (long string of "(" and ")") provided as input for this challenge

## About the problem

This looks like a simple challenge.  The first basic idea could be to start taking the symbols one by one, and keep a counter that would start at 0, adding 1 if there is "(", or subtracting 1 if there is "(".  However, this is the same as counting all the symbols "(", doing the same with all symbols "(", and deduct them, the result being the solution

## The code

Based on the above discussion, the code is very simple.  I made a ruby implementation as follows, (did not even bother to make a class for this...)

<script src="https://gist.github.com/tigretoncio/f0c3330afca4d206e363d2de5eda441f.js"></script>

Executing this code gives the right answer for the challenge.

## Day 1 - part 2

I haven't realized, but every day seems to have 2 challenges! I merrily went to day2 without realising that.  OK, back to day 1 to finish this and get another star!

## The new problem

Now it's a matter to know wich character that causes Santa to enter the basement (floor -1).

## Solution

I created the following code:

<script src="https://gist.github.com/tigretoncio/f3a4dcca8d76cfdc9995e1fd51bfdd5a.js"></script>

(if you want to know how I added the entry chars in my system ["Gangnam Style"](https://www.youtube.com/watch?v=9bZkp7q19f0) check [here]())

# Discussion

Basically I was following move after move, tracking the result and comparing if that floor was the basement or not.  Also I took care of using the basement as a constant, to remove any [magic numbers](http://stackoverflow.com/questions/47882/what-is-a-magic-number-and-why-is-it-bad) out of the code.