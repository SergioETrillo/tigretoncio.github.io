---
layout: post
title: "How to see the Intermediate Language in C#/.NET"
description: JS article
modified: 2016-05-02
category: C#/.NET
imagefeature: csharp2.jpg
comments: true
---

.NET framework uses a Common Language Interface, (CLR), which oversees the execution of .NET programs. The CLR is for example responsible for:

- manage memory
- type safety
- exception handling
- garbage collection
- thread management

Also the CLR provides a virtualized execution environment, which is a fancy way of saying that the program does not need to know anything about the CPU or the Operating System it is running on.

This CLR supports many languages, not just C#.  Another popular language from Microsoft supported by CLR is VisualBasic, and they are other languages, such as JavaScript, C++, Java or even Ruby!, (list of languages available [here](http://en.citizendium.org/wiki/List_of_languages_using_the_.NET_Framework)).

How is it done to support so many languages? .NET architecture uses an Intermediate Language (IL), which is produced by the compiler regardless of the language used to develop a program.  That IL code will be converted by the Just in Time compiler.

If you are curious to know what the Intermediate language looks like, you can use a tool called "ildasm" in order to see that code.

## How it works

Open a command windows and try to execute ildasm.  If you get an error, then set the path as follows:

<script src="https://gist.github.com/tigretoncio/2100aed2e8fc2726e7bea20245f7ab34.js"></script>

Then build your solution in Visual Studio, to get your .exe file HelloWorld, and go to your file path with your windows command line, then you are able to use ildasm.  The following command line code explains that:

<script src="https://gist.github.com/tigretoncio/2136c51bc75f726be85af7f870706eef.js"></script>

After the execution of this command you should see a window like this:

<a href="https://tigretoncio.github.io/images/ildasm/ildasm1.png" target="_blank">
  <img src="https://tigretoncio.github.io/images//ildasm/ildasm1.png">
<a/>

And selecting the Main element, the Intermediate Language for the program:

<a href="https://tigretoncio.github.io/images/ildasm/ildasm2.png" target="_blank">
  <img src="https://tigretoncio.github.io/images/ildasm/ildasm2.png">
<a/>

If you are familiarized with machine language you may think it has some similarities.  Also, it is interesting to note that the calls to methods WriteLine() and Readline() are explicitely stated.

Seeing the intermediate language can be useful some times if we want to know who certain operations are working, and for people who love to take a peek under the hood!
