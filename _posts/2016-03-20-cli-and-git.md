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
---------------------------

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

In this example, we have used the tr command to replace the colon ":" by a newline. By doing so, it is more easy to read the paths of our environment variable `$PATH`.

{% highlight ruby %}
def myFn(var)
    return var * 2
end
{% endhighlight %}


# Git commands

> This is cool!

Enjoy!