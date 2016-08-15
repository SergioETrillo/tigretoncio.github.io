---
layout: post
title: "Advent of Code, Day 3"
description: JS article
modified: 2016-07-13
category: Algorithms
imagefeature: alg.jpg
comments: true
---

To keep coding everyday, I have decided to go through the [Advent of Code](http://adventofcode.com/) challenges

# Day 3

Instructions for day 3 are available [here](http://adventofcode.com/day/3).  OK, Santa is in the process of delivering gifts to houses, and is using the "Elf navigation system" to know where to go. Moves are always exactly one house to the North (^), South (v), East (<) or West (>). After each move, Santa delivers another gift to the house at that location.  However the navigation system is not very precise, and Santa ends up visiting some houses more than once.  The question askes how many houses receive **at least one present**.  As input there is a long string with the route that Santa takes directed by his elvian team.

## About the problem

Hmm, this has some similarity to problem 1, however it uses cartesian coordinates now.  Santa starts in coordinates (0,0), and follows the path provided.  However it is not possible to sum up all the different elements to understand how many _unique_ houses receive gifts.

Basically we need a way to understand if every house that Santa visits is a new house, (and if count it accordingly), or he has been already, (and therefore ignore it).  After the path is completed, we just deliver.

So the "quick and dirty" solution is just to store in a list the coordinates of the houses that Santa is visiting, and check every time there is a move whether the house is in the list or not.

Uh oh, the instructions are 8192 moves, I have a feeling that this is going to be *slooooow* because when we start building the list, every single move will need to check for thousands of records to see if the move is new or not, (and if it is, it will need to check the whole list!).

So dirty, that I can do.  Quick, well not so much... (Slow and dirty can be useful in some scenarios, but I don't think that applies here... ;-)

In order to choose the data structure for the coordinates, again a short trip to the land of Internet search landing in [SO](http://stackoverflow.com/questions/525957/using-tuples-in-ruby) shows me that I could use OpenStrcts to get the coordinates nicely wrapped in a simple object, without the need of using a class for this.  Ok, code, here we go!

## The code

Ok, so after all this discussion I have managed the following:

<script src="https://gist.github.com/tigretoncio/4ba39cd0d284ea7e0a68b0148b7447b6.js"></script>

You may be probably wondering: "How is providing the moves inputs, and how did he provided the same inputs for day1 problem?"

Good question.

I just got in a hurry so decided to use the default REPL for ruby (irb), and copy pasting the entry, (["cowboy style"](https://www.youtube.com/watch?v=9bZkp7q19f0), I know...)

<a href="../images/day3/input.gif" target="_blank">
  <img src="../images/day3/input.gif">
<a/>

## Solution discussion

Clearly this is a non-optimal way of resolving this problem.  It takes quite long to resolve, just for almost 9000 moves.  In order to determine the program performance and try to fix it, I added the following method to the class

<script src="https://gist.github.com/tigretoncio/01194a2e710cfc9d855a38f02ca89308.js"></script>

using irb to run that method, it takes 4.6 seconds to get the answer back.  I am using a Linux Mint virtual machine over a mid-range Windows 10 laptop, so hardware is not top-notch, but that's not the point.  The point is that there are more efficient ways of doing things.  At least, it does the job.

## To Do

I was thinking about about this algorithm and how to speed up performance.  Ideally I would like something like the implementation for day 1, i.e. just counting how many symbols of each and making a simple mathematical calculation.  However it does not seem to be possible.

Second level of ideal solution would be to know if a visited home is new or not.  For that, I got some ideas.  If I implement some sort of _High Water Mark_ (HWM) per cardinal point, then if the move goes outside that HWM, I will know straight away that it is a new home, and won't need to iterate through the array looking for a home that I know for sure won't be there.

The idea looks interesting, but partial. I probably will need to dive into my geometry courses to understand if there is another way to "calculate" whether the point is visiting has been visited before of not.  Quite probably there must be a way of doing that kind of calculation, and that will certainly speed up the algorithm.  Even implementing this HWM should provide a noticeable difference.

Something To Do...

## Part 2

Uh Oh! Part 2 is asking about getting a "Robo-Santa" to help in the gift delivery! The story talks of "next year", however if this is to help power the snow machine for Santa, it must have worked this year, or is it a parallel reality 11.22.63 style?... anyway.

Santa and Robo starts at the same location, then take turns moving based on the instructions from the drunken elf, who is reading btw the same script as previous year.  The challenge asks how many houses receive at least one present.

## The approach

Mmm that one got me thinking a bit.  Clearly Robo and Santa were using the same script, so the first idea was to separate the script in 2, the instructions for Robo and for Santa.  That thought didn't went very far away, as I thought it could be complicated to manage the concurrent way of doing things.  for e.g. if I started with Santa and went to a position where Robo would have been going if it was concurrently would that matter? After reflection the answer is that it doesn't, Robo would visit the house and if that home was properly added in the gifted_home lists, it wouldn't have mattered.  So that was probably a nice way of doing it... Tah Dah!! (To Doo!)

But in this case I took another route.  Basically I decided to keep the script of movements together, and duplicate the "current address" to track the movements of Robo and Santa.  Also, I implemented some logic to know whose turn was to deliver gifts.

##  The code

<script src="https://gist.github.com/tigretoncio/ce9c9634552d63b4742a4c34da06615c.js"></script>

So I needed to repeat quite a lot of code because of the way I designed this one.  The more I think about it the more I think splitting the entry is the most efficient way of doing it.  Oh well, sometimes we win, and sometimes we learn... I did a bit of refactoring in initializing the OpenStructs now that I needed two, and defining them in paralell.  In the bootcamp where I studied they did not like to use paralell assignment and apparently many style guides forbid them because code is less clear, but imho they help to make code cleaner, (although I hold very my code opinions very weakly and are happy to change my mind if I am asked nicely :)

I moved all variables to private and kept them to read only as it is good practice to limit the information exposed by classes and attributes to the strict minimum required.

## To Do

Take a look to the solution of splitting input, and compare with this one to see how it simplifies, (or not).