---
layout: post
title:  "What are computed properties in Swift?"
date:   2023-01-05 15:00:00 -0500
categories: swift
tags: tips language
---

Computed properties, as the name suggests are properties whose value is derived
from other stored properties at runtime and are a valuable tool to know in Swift programming.
This eliminates the need to store these properties.

 In this post, we'll see how to use computed properties in Swift by creating a `User` struct that has two string properties: `firstName` and `lastName` and an integer that stores their `age`.

 {% highlight ruby %}
 struct User {
   let firstName: String
   let lastName: String
   let age: Int
}
{% endhighlight %}

Next we will add a computed property called `fullName` which will be computed from
the `firstName` and `lastName`.

{% highlight ruby %}
struct User {
  let firstName: String
  let lastName: String
  let age: Int
  var fullName: String { firstName + " " + lastName }
}
{% endhighlight %}

The advantage in doing this is that we do not need to store the fullName.
It will always be readily available to us from the `firstName` and the `lastName`.

{% highlight ruby %}
struct User {
  let user = User(firstName: "Joe", lastName: "Schmuck", age: 42)
  print(user.fullName)  // Prints "Joe Schmuck"
}
{% endhighlight %}

To explain this further, we would now like to know if our user is an adult.
A user can be considered an adult if they are 18 years or above. Sure, the caller can compute
this on their end, but what if this was available as a computed property on the `User` itself since we already know the
age of the user.
Let's add another computed property `isAdult` in our `User` struct.

{% highlight ruby %}
struct User {
  let firstName: String
  let lastName: String
  let age: Int
  var fullName: String { firstName + " " + lastName }
  var isAdult: Bool { return age >= 18}
}
{% endhighlight %}


{% highlight ruby %}
struct User {
  let user = User(firstName: "Joe", lastName: "Schmuck", age: 42)
  print(user.isAdult)  // Prints "true"
}
{% endhighlight %}

To sum it up, computed properties are a powerful tool that give us the ability to add
additional logic to our code. It makes our code concise and easier to follow along.
