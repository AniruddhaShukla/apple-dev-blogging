---
layout: post
title:  "How to shuffle elements in an array in Swift"
date:   2022-10-03 21:00:00 -0500
categories: swift, array
---

If you have an array or a sequence of elements that you want to arrange in a random order then
you can use a built in function that Swift provides, called `shuffled()`.

Let's consider that you have an array of Integers

{% highlight ruby %}
let numbers = [1, 2, 3, 4, 5, 6, 7, 8]
print(numbers.shuffled()) // Prints [3, 7, 2, 6, 8, 4, 1, 5]
{% endhighlight %}

In the above example, the sequence is random, so executing this again can result in a
different sequence each time.
