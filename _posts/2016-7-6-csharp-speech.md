---
layout: post
title: "Speech Synthesizer in C#/.NET"
description: JS article
modified: 2016-05-02
category: C#/.NET
imagefeature: csharp2.jpg
comments: true
---

.NET is a programming framework created by Microsoft with literally thousands of libraries and classes that are ready to be used to create applications easily.

In this post we are going to reference one of those classes to make our computer speak over a string we are entering.  Cool, isn't it?


## Let's do this!

I will just add a very simple code to show the functionality, and how easy is to have our computer speak what we are passing it through.  First of all we need to create a new project, in [Visual Studio](https://www.visualstudio.com/).  Visual Studio is free in its Community edition, and now Visual Studio Code is now available for Mac OS X and Linux!

### Opening a project

Once you have installed Visual Studio, it is easy to open a new "Console Project":


<a href="https://tigretoncio.github.io/images/VS1.gif" target="_blank">
  <img src="https://tigretoncio.github.io/images/VS1.gif">
<a/>


### The code

We will just want to ask the user to enter a string that can be read by the computer.  But before that, we need to reference the right assembly, which is the way of telling Visual Studio which is the library we want to use.


<a href="https://tigretoncio.github.io/images/Find-Assembly.gif" target="_blank">
  <img src="https://tigretoncio.github.io/images/Find-Assembly.gif">
<a/>


System.Speech has loads of classes and methods related to Speech recognition and synthesis.  There is a namespace called [System.Speech.Synthesis](https://msdn.microsoft.com/en-us/library/system.speech.synthesis(v=vs.110).aspx) which will use.  (A namespace is a container that helps to organise classes under a same label).  Within this namespace there is a class called SpeechSynthesizer.  This class has a number of methods that relate to speech synthesis, and there is one call "Speak" and that takes an string as argument, that does what it says on the tin!

So we just need to accept an string from our user, instantiate a SpeechSynthesizer object and invoke the Speak method, passing as argument the user entry.  The code is as follows:

<script src="https://gist.github.com/tigretoncio/8cb531ee89d7c0f57fabe1d23a873788.js"></script>

The program can be launched in Debug --> Start without debugging, (or with keyboard shortcuts Ctrl + F5).

And that's it! Just a few lines and the power of .NET framework have converted our computer in a speaker "parrot".  Use it for the good...

