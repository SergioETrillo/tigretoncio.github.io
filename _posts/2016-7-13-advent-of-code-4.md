---
layout: post
title: "Advent of Code, Day 4"
description: JS article
modified: 2016-07-14
category: Algorithms
imagefeature: alg.jpg
comments: true
---

To keep coding everyday, I have decided to go through the [Advent of Code](http://adventofcode.com/) challenges

# Day 4

Day 4, here we go!

Instructions for day 4 are available [here](http://adventofcode.com/day/4). But oh no! Santa has succumbed to the digital trends, and he needs to start mining _"AdventCoins"_, which are some sort of [bitcoins](https://en.wikipedia.org/wiki/Bitcoin) that is going to use as gifts to children.  So to do this he needs someone to find MD5 hashes which, in hexadecimal, start with at least 5 zeroes.  The input of the MD5 hash will be the combination of a super-secret key (the input provided) and a positive integer that produces such a hash.  They are a couple of examples provided.

## About the problem

Uh Oh!  mmm excuse me?  Hopefully I won't need to come back to my notes about cryptography from my Telecoms degree to resolve that...At the beginning this looks daunting and of extreme difficulty...

But it is not.

Basically we just need an implementation of MD5, and try that function with the combination entry that is suggested until we get the answer.  ruby has the function built in in the digest/md5 system file.  In .NET I can use MD5CryptoServiceProvider from the System.Security.Cryptography namespace.

## The code

<script src="https://gist.github.com/tigretoncio/2f015c0e7bf40e8ee5fdb6d37d2aa742.js"></script>

## Explanation

It's pretty basic.  Once we have a function that generates the MD5 hash for us, we just need to iterate changing the input of the number that we are looking for, and comparing if the result contains 5 zeros in the beginning.  In ruby the output of the MD5 hash calculation function is a string so it is very easy to handle it to take the 5 initial digits using a range in the array

## Part 2

Part 2 is pretty much the same, with the same input, we need to get the result for a number that starts for 6 zeros... However, it was great to pinpoint some issues of my previous code, I missed to remove the magic number, and therefore I need to change more this time...

## The code

<script src="https://gist.github.com/tigretoncio/6348168846832323c2c88e69c39c4ec8.js"></script>

I have introduced a constant "ZEROS" instead of using 5 or 6 as I was doing in part one.  That allows to search for any number of zero digits, just changing the figure in line 5.  Isn't that cool?  Also, ruby allow to "multiply" string characters, the result is to replicate that character or string by the number multiplied, which is useful here.  Classy!