---
layout: post
title:  "How to create a Picker View in SwiftUI. "
date:   2022-11-06 19:10:00 -0600
categories: swiftui
tags: pickers
---

SwiftUI makes it really easy to create different types of pickers using the
`pickerStyle` modifier. If you ever wondered how to build a segmented control in SwiftUI read on, as you can easily
build one using PickerView.

In our example, we will give the user the ability to choose from different
cuisine types.

First we will define our cuisine type.
{% highlight ruby %}
enum CuisineType: String, CaseIterable {
    case Indian, Chinese, American, Thai
}
{% endhighlight %}

We have conformed to `CaseIterable` protocol so that we can iterate over all the
cases, which in our example would be all the declared cuisine types.

We will also keep track of the currently selected cuisine that will be necessary
for the `Picker` to keep track of the currently selected value.

We will have to default to a cuisine type to start things off. In this example
we have defaulted to Indian cuisine since that's my favorite.

{% highlight ruby %}
struct MenuView: View {
    @State private var selectedCuisine = CuisineType.Indian

    var body: some View {
        VStack {
            Text("Selected Cuisine: \(selectedCuisine.rawValue)")
            Picker("Select Cuisine", selection: $selectedCuisine) {
                ForEach(CuisineType.allCases, id: \.self) {
                    Text($0.rawValue)
                }
            }.pickerStyle(.menu)

        }
    }
}
{% endhighlight %}

The `pickerStyle` modifier let's us choose between different types of styles
available namely `segmented`, `menu`, `wheel`.
You can also choose `automatic` which is the DefaultPickerStyle so that the
system can choose one for you depending on several factors which can be found in
the documentation for `DefaultPickerStyle`.

That's all you need to get started with Pickers in SwiftUI.
