---
layout: post
title:  "How to remove nil elements in an array in Swift"
date:   2022-12-22 15:00:00 -0500
categories: swift
tags: arrays tips language
---

If you have an array or a sequence of elements that might contain nil values that you might want
to remove, Swift provides a great higher order function that is pretty handy called `compactMap`.

Let's consider that you have an array of names and the requirement is to only keep valid names such that the name is not nil.

{% highlight ruby %}
let names = ["Kate", nil, "Rohan", "Mohammad", "Joe"]
let validNames = names.compactMap { $0 }
{% endhighlight %}

If you were to print validNames it will only contain `["Kate", "Rohan", "Mohammad", "Joe"]`.

Let's take this example a bit further. If the names array also contains
some empty strings in the sequence you can use `filter` function to remove them.
You can chain multiple higher order functions together.

{% highlight ruby %}
let names = ["Kate", nil, "", "Jack", "Rohan" "Mohammad", "", "Joe"]
let validNames = names.compactMap { $0 }.filter { !$0.isEmpty }
{% endhighlight %}

If you were to print `validNames` it will contain `["Kate", "Jack", "Rohan", "Mohammad", "Joe"]` removing any empty names.

To recap, the `compactMap` method first removes all nil elements from the array, and then the `filter` method removes any empty strings that might be in the array.
