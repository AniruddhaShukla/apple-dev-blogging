---
layout: post
title:  "How to display DatePicker in SwiftUI?"
date:   2023-04-17 20:05:00 -0600
categories: swiftui
tags: pickers
---

In this post we will see how to create a simple Date Picker in SwiftUI.
Let's create a `@State` variable that will keep track of the current selected date.

{% highlight ruby %}
@State var departureDate = Date()
{% endhighlight %}

We will next initialize the DatePicker and pass in the `departureDate`

{% highlight ruby %}
DatePicker("Departure Date", selection: $departureDate,
                      displayedComponents: [.date])
{% endhighlight %}

If you want to display the time along with the date you would pass
both `date` and `hourAndMinute` to the `displayedComponents` parameter.

{% highlight ruby %}
DatePicker("Departure Date", selection: $departureDate,
                      displayedComponents: [.date, .hourAndMinute])
{% endhighlight %}

If you want to perform any action after a new departure date is selected by the user
you can apply the `.onChange` modifier and capture the newly selected date.

{% highlight ruby %}
DatePicker("Departure Date", selection: $departureDate,
           displayedComponents: [.date]).onChange(of: departureDate) { newValue in
    print("Departure date: \(newValue)") // The new selected departure date will be printed.
}
{% endhighlight %}

You can also change the style of the `DatePicker` by applying the `.datePickerStyle` modifier.
There are different styles available like `.wheel`, `.graphical`, `.compact` and `.automatic`.
