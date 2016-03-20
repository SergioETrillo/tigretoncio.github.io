---
layout: post
title: "Cheat sheet for some shell and Git commands"
description: Topics of the first week of PreCourse at Makers Academy
modified: 2016-03-20
category: web_development
tags: [command line, git, github, shell]
imagefeature:
comments: true
---
The first week of PreCourse is almost finished and we have worked with two main topics that are essential for any programmer: the command line and Git. I want to share with you some of the commands that I found interesting:

## Shell commands
-----------------

* **which**: Find out the pathname of a file or link

{% highlight shell %}
$ which ruby
=> /usr/local/rvm/rubies/ruby-2.3.0/bin/ruby
{% endhighlight %}


This command could be used to look for the <a href="https://en.wikipedia.org/wiki/Shebang_(Unix)" target="_blank">shebang</a> that you need to add on the ruby files that you want to be executed without invoking explicitely the ruby interpreter.

* **tr**: Translates (substitutes) sets of characters

{% highlight shell %}
$ echo $PATH | tr : '\n'
=>  /usr/local/rvm/rubies/ruby-2.3.0/bin
    /mnt/shared/bin
    /home/ubuntu/workspace/node_modules/.bin
    /home/ubuntu/bin
    ...
{% endhighlight %}

In this example, we have used the **tr** command to replace the colon ":" by a newline. By doing so, it is more easy to read the paths of our environment variable `$PATH`.

* **export**: set variables on a bash shell

{% highlight shell %}
$ echo "export SEASON=summer" >> ~/.bash_profile
{% endhighlight %}

In this case, we are not just setting a varible on the environment variable list, but also we are keeping it for further usage. Remember that by default the variables should be recreated every time a new session on a terminal starts. By adding the variable to the ~/.bash_profile file we do not need to recrate it again.

One of the common uses of a environment variable is storing sensitive data, such as passwords. In case we want to use an environment variable in our ruby program, we can invoke it like this:

{% highlight ruby %}
myVar = ENV["SEASON"]
puts "#{myVar}"
{% endhighlight %}

*This list is not completed yet...*

# Git commands
--------------

* How to delete a branch on GitHub (the website)

{% highlight shell %}
$ git push origin --delete <branch_name>
{% endhighlight %}

* Revert local changes to a file that is not staged

{% highlight shell %}
$ git checkout <filename>
{% endhighlight %}

* Recreate one (or more) file(s) in your working directory as they were at that moment in time without altering history use

{% highlight shell %}
$ git checkout <SHA> -- <filename>
{% endhighlight %}

*This list is not completed yet...*
