---
layout: post
title:  "SwiftUI List"
date:   2022-09-24 11:35:59 -0500
categories: swiftui
---
SwiftUI makes it really easy to build lists similar to a UIKit Table View if you have coded in UIKit before.
Using a `List` you can display rows of data in a single column.

For example, you can display the list of cities in the world.

{% highlight ruby %}
List {
    Text("New York City")
    Text("Portland")
    Text("Kansas City")
    Text("San Fransisco")
    Text("Bengaluru")
    Text("Madrid")
}
{% endhighlight %}

You can even categorize cities in their respective countries using a `Section` container to give our list some
hierarchy.

Let's add some more cities and categorize them under the country they belong to.

{% highlight ruby %}
List {
    Section("USA") {
        Text("New York City")
        Text("Portland")
        Text("Kansas City")
        Text("San Francisco")
    }

    Section("India") {
        Text("Bengaluru")
        Text("Pune")
        Text("Mumbai")
    }

    Section("Spain") {
        Text("Barcelona")
        Text("Madrid")
    }
}
{% endhighlight %}
