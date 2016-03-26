---
layout: post
title: "Linked lists, hashes and recursion in Ruby"
description: Visual explanation of the linked list implemented using Hashes
modified: 2016-03-26
category: web_development
imagefeature:
comments: true
---
The last three challenges of the session 3 of the <a href="https://github.com/makersacademy/ruby-kickstart/tree/master/session3/3-challenge" target="_blank">ruby-kickstart</a> use some nested hashes to create what is called a linked list. 

In computer science, a linked list is a linear collection of data elements, called nodes pointing to the next node by means of pointer. It is a data structure consisting of a group of nodes which together represent a sequence. Under the simplest form, each node is composed of data and a reference (in other words, a link) to the next node in the sequence. This structure allows for efficient insertion or removal of elements from any position in the sequence. From <a href="https://en.wikipedia.org/wiki/Linked_list" target="_blank">https://en.wikipedia.org/wiki/Linked_list</a>

I find very useful the diagrams and images to reinforce learning. So, I hope that the representations below can help you to understand this concept. I decided to share this with you because the images really helped me to figure out what this was all about.

### Linked list in images
<br>

<figure>
  <img src='/images/web_development/LLexplanation.png'>
  <figcaption>A linked list whose nodes contain two fields: an integer value and a link to the next node.<br>The last node is linked to a terminator used to signify the end of the list.</figcaption>
</figure>

* **Head:** Points to the first node in the linked list
* **Tail:** Points to the last node in the linked list


### Using hashes to build the linked list:
<br>
We start by creating a hash called `head` in this example:

{% highlight ruby %}
head = {:data => 1, :next => nil}
{% endhighlight %}

This line will create a linked list that so far only contains one none. So, that node is both the head and tail.

![LL1]({{ site.url }}/images/web_development/LL1.png)

To add a new node to the list, we do the following:

{% highlight ruby %}
head = {:data => 2, :next => head}
{% endhighlight %}

At this point, our list can be represented like this:

![LL2]({{ site.url }}/images/web_development/LL2.png)

We can progressively add more nodes to the list, always *linking* to the next node in the sequence. Let's add one more node:

{% highlight ruby %}
head = {:data => 3, :next => head}
{% endhighlight %}

The graphical representation of our list is:

![LL3]({{ site.url }}/images/web_development/LL3.png)

And the full hash is:

{% highlight ruby %}
$ head
# => {:data=>3, :next=>{:data=>2, :next=>{:data=>1, :next=>nil}}}
{% endhighlight %}

With that in mind, we have to create some methods to manipulate linked list. Let's see an example.

### Recursion

The exercices need to be solved using recursion. Click <a href="https://vimeo.com/24716767" target="_blank">here</a> to see the Ruby Kickstart - Introduction to Recursion video.

Implementing recursive methods can be tricky, and I admit that I spent a lot of time trying to solve this <a href="https://github.com/makersacademy/ruby-kickstart/blob/master/session3/3-challenge/10_hashes.rb" target="_blank">challenge</a>. This post is my two cents to help you solving those challenges of session 3. As a bonus, I am sharing a little recursive function that can be used to calculate the number of nodes of a given list. This does not solve any of the challenges, but can work as a guide to take some ideas and try to implement your solution.

{% highlight ruby %}
def countNodes(list, count = 1)
    return count if list[:next] == nil
    countNodes(list[:next], count += 1)
end
{% endhighlight %}

This method accepts two parameters, a list (hash) and a variable that is used to count the number of nodes that is initialised to 1. If you are already in the tail of the list, `list[:next]` will be `nil` and you can return the number of nodes `count`. Notice that if you pass a list with only one node, the method will return 1, that is, the value by default. Otherwise, you call again the countNodes method passing as arguments the next node of the list and incrementing the count in 1.