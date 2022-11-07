---
layout: post
title:  "What is discardableResult in Swift?"
date:   2022-07-06 18:50:45 -0500
categories: swift
tags: language
---
When a function is marked with `@discardableResult`, it allows the caller to ignore the return value of the function.

For example let’s consider a function that returns if an operation was successful.

{% highlight ruby %}
func setPersonName(name: String) -> Bool {
    // Some processing happens here
  return true
}
{% endhighlight %}

Now when the caller calls this function the compiler will suggest that Result of call to `setPersonName` is unused.

{% highlight ruby %}
setPersonName(name: "Joe") // you will receive a compiler warning here.
{% endhighlight %}

To silence the compiler you have to create a variable to store the Bool value returned from the function.

{% highlight ruby %}
let result = setPersonName(name: "Joe")
{% endhighlight %}

But in certain situations the caller might not care about the result of the call. Marking the function with discardableResult silences the compiler warning and allows you to ignore the return value from the function.

{% highlight ruby %}
@discardableResult
func setPersonName(name: String) -> Bool {
  // Some processing happens here
  return true
}
{% endhighlight %}

Compiler will not warn you anymore when you invoke the function `setPersonName(name: "Joe")`.  
