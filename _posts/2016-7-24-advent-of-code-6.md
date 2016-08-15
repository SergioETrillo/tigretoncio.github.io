---
layout: post
title: "Advent of Code, Day 6"
description: JS article
modified: 2016-07-24
category: Algorithms
imagefeature: alg.jpg
comments: true
---

To keep coding everyday, I have decided to go through the [Advent of Code](http://adventofcode.com/) challenges

# Day 6

Instructions for day 6 are available [here](http://adventofcode.com/day/6).

Because of my neighbours keep defeating me in the chrismas lights decoration year after year, apparently I've decided to deploy one million lights in a 1000x1000 grid! (I hope they will be LED or will need a loan to pay the electricity bill! even so I think I will!)

Santa is sending me the instructions to display the ideal lighting config, and the lights include whether to turn on, off or toglle various inclusive ranges given as coordinate pairs.  The problem asks how many lights will be lit after the 300 instructions are followed...

## About the problem

Right so the brute force approach is to effectively define the matrix of 1 million elements, follow the instructions and then count the lights on.  Looks like pretty straight forward.

## The code

<script src="https://gist.github.com/tigretoncio/e7173905ae9a3e74dd7166eae29cf32e.js"></script>


## Explanation

What we do here is to define the grid as a 2D array containing 0 if the light is switched off, 1 if it is on.
First, we read data from a file text where our instructions are stored, and split these data by line, storing this data in the variable lines.
Then, there is a method to extract instructions from each of these lines, getting the command instruction, and the start / end coordinates.

Then it is a matter of iterate through the lines with the instructions, extracting these instructions with the previous method, and update the grid on each instruction, depending on the command (switch on switch off, toogle), and the beginning and end coordinates.

At the end of all instructions, we just need to sum the array and that is the solution to the challenge.

## Discussion

Of course this is a pretty inefficient as we need to perform operations on a 1-million grid all the time.  Some tips to improve efficiency would be just to keep the lighten bulbs, and do some checks to understand the current lighten bulbs at any time.  Also each instruction should check if it intersects with the areas kept in status for lighten bulbs.  So for no intersections and switch off command we could completely ignore those, (as status will keep the same).  If they are switch on and they are within the status again we could ignore those, as status does not change, and for toggles we would need in any case to treat them as will change from ligthen to off or viceversa.

These changes would make the code more complex, but in principle increase the performance of the code, depending on the set of instructions.  However, for the part 2 this type of coding would not help very much, will see why below.

## Part 2

Now just when I am done installing the lights I realize I mistranslated Santa's message from Ancient Nordic Elvish (d'oh!).

- turn on actually means incress brightness by 1
- turn off means decrease brightness by 1, (if they are switch off then no change)
- toggle means increase brightness of lights by 2

With this new set of instructions it is asked the total brightness.

## Solution

Using the brute force approach is flexible enough, and as we have tried to use the [Single Responsibility Principle](https://en.wikipedia.org/wiki/Single_responsibility_principle), it is easy to implement a new method `process_command2` which implements the new set of rules.

## Part 2 code

The code is the same, but instead of `process_command` method we use a `process_command2` method implementing the new rules.  It is as follows:

<script src="https://gist.github.com/tigretoncio/e497cba5c789aad218435a7d182b2409.js"></script>

so then invoking this method in the main code provides the right answer for this challenge. Cool!


