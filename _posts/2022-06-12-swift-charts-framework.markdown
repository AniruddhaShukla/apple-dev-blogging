---
layout: post
title:  "Create a chart using Swift Charts"
date:   2022-06-12 18:01:33 -0500
categories: jekyll update
---
In WWDC 22 the new Swift Charts framework was announced and it has never been easy
to create beautiful Charts. You will need Xcode 14 installed which at the time of writing is in Beta.
Let's get right to it..

In this example, we will show a graph of the average temperatures in Kansas City
for last week. We will create a struct which will hold the day of the week and the average temperature for that
day respectively. These will be our X and Y axes on the chart.

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


You can create various types of Charts using the new Charts framework. We will create a
Line Chart which will display the average temperature trend over the week.

{% highlight ruby %}
struct ChartView {
  var body: some View {
    Text("Daily temperatures for last week in Kansas City.")
    Chart(data) {
      LineMark(
          x: .value("Day", $0.day),
          y: .value("Temperature", $0.value)
        )
    }
  }
}
{% endhighlight %}

![Line Chart]({{ site.url }}/{{site.baseurl}}/assets/linechart.png)

We can also represent data  using points on the Line chart. Swift Charts framework allows us to
combine Marks.

{% highlight ruby %}
Chart(data) {
    LineMark(
        x: .value("Day", $0.day),
        y: .value("Temperature", $0.value)
    )

    PointMark(
        x: .value("Day", $0.day),
        y: .value("Temperature", $0.value)
    )
}
{% endhighlight %}

![Point Mark]({{ site.url }}/{{site.baseurl}}/assets/pointmark.png)


Sometimes, showing these temperatures as Bars for each day might make more sense. You can easily do this by
switching `LineMark` struct with `BarMark`.

{% highlight ruby %}
BarMark(
    x: .value("Day", $0.day),
    y: .value("Temperature", $0.value)
  )
{% endhighlight %}

If you want to now add a color to your bars or line chart you can use the `foregroundStyle` modifier.

![Line Chart]({{ site.url }}/{{site.baseurl}}/assets/redbarchart.png)

{% highlight ruby %}
Chart(data) {
    BarMark(
        x: .value("Day", $0.day),
        y: .value("Temperature", $0.value)
    )
    .foregroundStyle(.red)
}
{% endhighlight %}

And that's pretty much what you need to get started with Charts.
