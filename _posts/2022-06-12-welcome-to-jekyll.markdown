---
layout: post
title:  "Create a chart using Charts framework"
date:   2022-06-12 18:01:33 -0500
categories: jekyll update
---
In WWDC 22 the new Charts framework was announced and it has never been so easy
to create beautiful Charts. Let's get right to it..

Let's create our datasource. We will show a graph of the temperatures in Kansas City
for last week. We will create a struct which will hold the day of the week and the average temperature for that
day respectively.

{% highlight ruby %}
struct TemperatureTrend: Identifiable {
  var day: String
  var value: Double
  var id: String { return day }
}
{% endhighlight %}

Next we will create an array that will hold temperatures for all days Monday thru Sunday.

{% highlight ruby %}
let data : [TemperatureTrend] = [
  .init(day: "Mon", value: 75),
  .init(day: "Tue", value: 70),
  .init(day: "Wed", value: 80),
  .init(day: "Thur", value: 62),
  .init(day: "Fri", value: 78),
  .init(day: "Sat", value: 79),
  .init(day: "Sun", value: 81),
]
{% endhighlight %}

![My helpful screenshot](/assets/test-image.jpg)

You can create various types of Charts using the new Charts framework. We will create a
Line Chart which will display the average temperature trend over the week.

{% highlight ruby %}
struct ChartView {
  var body: some View {
    Text("Daily temperatures for last week in Kansas City.")
    Chart(data) {
      LineMark(
          x: .value("Day", $0.day)
          y: .value("Temperature", $0.value)
        )
    }
  }
}
{% endhighlight %}
