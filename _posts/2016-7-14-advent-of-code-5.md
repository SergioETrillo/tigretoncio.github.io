---
layout: post
title: "Advent of Code, Day 5"
description: JS article
modified: 2016-07-15
category: Algorithms
imagefeature: alg.jpg
comments: true
---

To keep coding everyday, I have decided to go through the [Advent of Code](http://adventofcode.com/) challenges

# Day 5

Instructions for day 5are available [here](http://adventofcode.com/day/5). Alright, Santa needs help to filter from children letters which words are nice and which are naugthy (!).

A nice string is defined as a number of properties, (contains 3 vowels, at least one letter appears twice in a row, and does not contain a set of strings such as ab, cd, pq or xy).  Question asks how many nice words are in a provided file input.

## About the problem

ok, this is a typical regex problem! Internet and [SO](www.stackoverflow.com) to the rescue... Basically we need to define the relevant regex expressions, then read the file and check against those expressions.  If the conform to the properties of what Santa calls nice, then increment our counter by one.  Finally, deliver the counter to Santa!

Part 2 is very similar, but just changing the properties again, with the hilarious sentence: "Realizing the error of his ways, Santa has switched to a better model of determining whether a string is naughty or nice. None of the old rules apply, as they are all clearly ridiculous."  Bravo!

## The code

<script src="https://gist.github.com/tigretoncio/a29ecbed72975e69790080ab936410f9.js"></script>

## Explanation

As discussed above, the challenging bits on this one were in creating the right regex that could be matched against the string provided.  I extended the String class just because I thougth it was much more readible to get an expression such as `@nice_words += 1 if word.nice?`, but this is probably getting me too Rubyist and not very pragmatic, as extending the class could cause issues later on, (although not necessarily).  Also I decided to extract the regex expressions as constants as in theory they should not change.