---
layout: post
title:  "Property Wrappers in Swift"
date:   2024-10-23 21:00:00 -0500
categories: swift
tags: tips language
---

Property wrappers provide a way to add behaviors like validation,
transformation, or default values to properties without repeating the same code elsewhere.

Let's take an example where we can use property wrapper for performing a transformation on a value.
We will create a `@Capitalized` property wrapper that automatically capitalizes any string assigned to
a property:

{% highlight ruby %}
@propertyWrapper
struct Capitalized {
    private var value: String = ""
    
    var wrappedValue: String {
        get { value }
        set { value = newValue.capitalized }
    }
}
{% endhighlight %}
The setter in the above example takes the incoming value and capitalizes it and assigns it to the value property.
The getter, as we can see then provides the capitalized value.

You can now use `@Capitalized` to automatically capitalize user input:

{% highlight ruby %}
struct User {
    @Capitalized var name: String
}

var user = User()
user.name = "john appleseed"
print(user.name) // Code Prints: John Appleseed

{% endhighlight %}

As we can see, in the above example the name gets capitalized everytime behind the scenes when the name is set.