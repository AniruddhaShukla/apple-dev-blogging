---
layout: post
title:  "How to restrict dates in DatePicker in SwiftUI?"
date:   2023-04-23 22:00:00 -0600
categories: swiftui
tags: pickers
---

In this post we will see how to allow only selection of dates in a certain time frame.
Let's consider an example where you only want to allow the user to select dates within the next 2 years from today
for their trip.

The current selected date will be maintained by the `@State` variable `departureDate`.

{% highlight ruby %}
@State var departureDate = Date()
{% endhighlight %}

The initializer of the `DatePicker` accepts a range of dates. So we will need to pass this range where our startDate will be today's date and the end date should be 2 years from now which we will call `maxAllowedDate`.

Next, let's calculate the `maxAllowedDate`, which would be 2 years from today.

{% highlight ruby %}
// 2 years from today in seconds.
let maxAllowedDate = Date().addingTimeInterval(60 * 60 * 24 * 365 * 2)
{% endhighlight %}

We can now initialize our `DatePicker` with this range.

{% highlight ruby %}
List {
    DatePicker("Departure Date",
               selection: $departureDate,
               in: Date()...maxAllowedDate, displayedComponents: [.date])
}
{% endhighlight %}

![Date Picker]({{ site.url }}/{{site.baseurl}}/assets/alloweddate.png)

Now, the user will be only able to select dates in our specified range as shown above and
all dates outside this range will get disabled for selection.
