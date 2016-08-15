---
layout: post
title: "Advent of Code, Day 7"
description: JS article
modified: 2016-07-28
category: Algorithms
imagefeature: alg.jpg
comments: true
---

To keep coding everyday, I have decided to go through the [Advent of Code](http://adventofcode.com/) challenges

# Day 7

Instructions for day 7 are available [here](http://adventofcode.com/day/7).

Right, so this time little Bobby has been given a toy which is _a little_ over the recommended age range, (which must start from 50 and for PhD.holders), and Santa is asking our help to assemble it.

Basically the instructions are a bit confusing, but overall there are some elements:

- signals: This is a 16-bit signal which is represented as an integer between 0 and 65535, (for its binary representation)

- wires: which are identified by lowercase letters, "a", "b"... up to "ma"

- gates: a signal is provided to each wire by a gate, another wire, or some specific value. Each wire can only get a signal from one source, but can provide its signal to multiple destinaions.  A gate provides no signal until all of it inputs have a signal.

So there is a booklet instruction describing how to connect the parts together, for example, `x AND y -> z` means to connect wires `x` and `y` to an AND gate, and then connect its output to wire `z`. It then provides a few examples, and the available logical operations which are:

- AND (takes 2 wires)
- OR (takes 2 wires)
- NOT (only takes 1 wire)
- LSHIFT (takes 1 wire, and an integer which is the number of bit shifts to the wire signal)
- RSHIFT (same input as LSHIFT)

For a strange reason little Bobby wants to know what would be the result signal, if the kit's instructions booklet is implemented, (339 logical instructions of the style `x AND y -> z`)

## About the problem

Right ok, so taking a look to the input data, the first thing I could notice is that the entries look completeley randomised, those are the few entries of the input, (full data available [here](http://adventofcode.com/day/7/input))

```

lf AND lq -> ls
iu RSHIFT 1 -> jn
bo OR bu -> bv
gj RSHIFT 1 -> hc
et RSHIFT 2 -> eu
bv AND bx -> by
is OR it -> iu
b OR n -> o
gf OR ge -> gg
NOT kt -> ku
ea AND eb -> ed
kl OR kr -> ks


```

So in principle, do we have any entry that provides some initial data to work with? and is there an "a" signal that we can use to start deriving?

I row 79 we get the instruction `lx -> a` so we know that a is a funtion of lx.  if we search lx we get `lw OR lv -> lx` so a depends on lx, lw and lv, searching for lw we would get `lc LSHIFT 1 -> lw` so a depends on lx who depends on lw and lw and lw depends on lc...

So the first pattern here is that it looks like the author is putting the wires in alphabetical order in terms of the dependencies on how they work, (if we consider `a` as an exception).  We can confirm that looking for wire b, and we get in line 55: `19138 -> b`.

So this is the first signal with data!  b therefore do not depend on a, it is then an independent variable and has already a defined signal of 19138.  What about c? line 90 gives us: `0 -> c`.  Another independent variable!  What about d?  line 282 this time: `b RSHIFT 2 -> d`.  This is good! d depends on b, who is an independent variable! Let's check e: line 284 : `b RSHIFT 3 -> e` again dependent on b which we know what it is! So the logic is clear, we need to rearrange but alphabetical order, start processing the initial instructions, and then probably use the results to continue to process further instructions until arriving to the lx instruction, which is the value we are looking for! _Sort of easy..._

## High level algorithm

OK, so this is a relatively complex problem, not because of the logical operations which are fairly trivial, but basically to process the input data to get the elements we need to process those binary operations.

### Data processing

The way I approached this problem was as follows:

- Create file in my directory with data input.

- I need to sort by alphabetical order, however I need to sort by the last part of the instruction, (i.e. in `a AND b -> z` I need to sort by `z` which is the output of the instruction).  So I need to reverse the elements between the `->`

- Then I need to sort, however a simplistic sort by alphabetical order is not enough. Why? Because it will sort by the order a, aa, ab, ac... and we need to ensure an order a, b, c,...z, aa, ab, because aa will certainly depend on letters from the end of the alphabet that we need to calculate before.  Just to explain this, aa instruction is `x RSHIFT 5 -> aa`, so aa depends on x, and can't be at the begining of the instructions.  So the sorting algorithm is:

```
SORT BY length of the variable, then
SORT BY alphabetical order of the variable
```
- Also when the reversal is done, there are some spaces that should be removed in order to properly process the data

- And we probably need a data structure to ensure that we can capture the wires and its values, in order to use them for the next calculations.  For that I decided to use a Hash, (or dictionary in C#), keeping as key the value of the wire, and value the existing value of the logical operation to do, which I will be replacing by the result signal once it is calculated.  So it is pretty straight forward to convert the existing array of data into a Hash.  And with that chaps, the data processing part of this challenge is completed.


### Signal processing

Once we get the data processed as we want, it is a matter of processing signals until we get a result. For that I did the following:

- I kept in separate variables the first item of the hash, as it points out to the signal that I need to calculate to provide a result and stop the program.  Once this is stored, I delete that variable as it is the "exception" and won't be used as data input or to calculate signals from other wires

- Then I iterate through the remaining item, and again there is a bit more data processing as I need to distinguish between the different situations:
  - instruction already contains a value, (independent variable)
  - instruction contains a business logic to calculate
My visual inspection of the data told me that they are only 2 "independent" variables (b and c), so I could have hardcode them in the program, however that would be very inflexible if in the second challenge part Santa or little Bobby decide to change the data!

- I also need to process the logic function, which can be of 2 main types depending of the arguments:
  - NOT function: with format "NOT <signal>"
  - Any other function, with the formal "op1 LOGICAL_FUNCTION op2"
The any other function again can have two type of arguments.  Operators can be either wires, and therefore the program needs to look these variables up in the hash and get the right signal values, but also they can already be signal values.  For example, in line 48 of the unsorted input file we have `1 AND cc -> cd`.  Operator1 is already a signal of value 1, so we don't need to go and lookup its value elsewhere.  cc is a signal which will have been calculated previously and will be stored in the hash, and therefore we will need to look up the value of cc in the hash and substitute it by the right value.  Same situation happening with RSHIFT or LSHIFT, where Operator2 is always a signal indicating the number of bits the Operator1 signal needs to shift to get the result.
So we will need some sort of recognition on whether an operator is a "signal" or a "wire".  We will use a simple regex expression for that

- Finally, with all these data processing done, we will just have "signals" and we will process the binary calculations requested.  At that point, we will need to replace the value in the hash for the signal we are calculating, to ensure that it is available for the next calculation which probably use the value currently calculated.

## The code

I have used a TDD approach for this one, which is the right way of developing for programs that will experience a high rate of change.  Although not required in this situation, it is a good practice exercise to ensure there are unit and integration tests that check every bit of the program.  That way if some of the program changes we will know straight away if there is any side effects.

### Unit Tests
<script src="https://gist.github.com/tigretoncio/3df8e949dc573132c1bf88f23610cd13.js"></script>

### Integration Tests
<script src="https://gist.github.com/tigretoncio/f3f0bff85d0bcff8264ceb62c644ef82.js"></script>

### Code
<script src="https://gist.github.com/tigretoncio/f695aed9ecfcb2f503be38d00b0433a1.js"></script>

## Part 2

Taking directly from the instructions:
_"Now, take the signal you got on wire a, override wire b to that signal, and reset the other wires (including wire a). What new signal is ultimately provided to wire a?"_

Very easy, simply use the value obtained in part one and change the b instruction in the file with it, to get the new right solution!



## How to cheat on this one (*)

If you want to have a solution "just" for the sake of getting the stars, but without any code to show off about, you may want to use a lateral thinking approach.  As we know that the solution is a number between 0 and 65535, we can "take a guess" on the middle of the range.  The author of the challenge is nice enough to let us know if the guess is too high or too low.  The web page blocks you for a minute to get another guess.  However, if it is too high, then you choose the range [0, 32768], and guess in the middle, (i.e. 16384).  And repeat the process.  In principle in around 16 minutes you should get the answer...



_(*) Kids, this is not an encouraged way of resolving the challenge, Santa does **not** approve!_

