---
layout: post
title:  "Multiline String Literals in Swift"
date:   2024-06-13 13:00:00 -0500
categories: swift
tags: strings tips language
---

If you want to declare a string that is really long or spans over multiple lines, then swift makes it really easy to do so with multiline string literals.

The syntax to declare these strings are using the triple quotes """ instead of the double "" quotes.

Let’s take an example where you had to declare a simple JSON that gives info about a Book.

{% highlight ruby %}
let bookJSON = """
{
    "name": "Swift Programming Guide",
    "id": 12345,
    "author": "John Appleseed"
}
"""
{% endhighlight %}

In the above example the triple quotes tells the compiler that the string spans multiple lines
and makes it more readable. Another advantage is that you can write the text within the triple quotes as if you were
writing using a text editor, meaning all the indentations and line breaks will be honored making it easier to follow along.

For example, the same `bookJSON` string when using the regular double quotes would look something like this.
{% highlight ruby %}
let bookJSON = "{ \"name\": \"Swift Programming\", \"id\": 12345, \"author\": \"John Appleseed\" }"
{% endhighlight %}

As we can see multiline string literals can be use to declare simple HTML, JSON or simple scripts inline making code more readable.
