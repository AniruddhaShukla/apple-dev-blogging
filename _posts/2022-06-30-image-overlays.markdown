---
layout: post
title:  "Overlay text on an image in SwiftUI"
date:   2022-06-30 22:30:33 -0500
categories: swiftui
---
There are many times when one needs to show text on an image, for example display credits
of the photographer on an image.
SwiftUI makes this incredibly easy to do so with the `overlay` modifier.

For this example, we will display an image we got from unsplash.com and then display
the name of the photographer who took this image.

{% highlight ruby %}
VStack(alignment: .leading) {
  Image("backgroundImage") // replace backgroundImage with your image name.
      .resizable()
      .aspectRatio(contentMode: .fit)
}
{% endhighlight %}

We will create a separate view that will display the overlay so we can reuse this
if neccessary.
We will set the opacity of the view to 60% in our example.

{% highlight ruby %}
struct OverlayTextView: View {
    let creditName: String
    var body: some View {
        ZStack {
            Text("Credit: \(creditName)")
                .font(.callout)
                .padding(8)
                .foregroundColor(.white)
                .font(.footnote)
        }.background(Color.black)
        .opacity(0.6)
        .cornerRadius(10.0)
        .padding(8)
    }
}
{% endhighlight %}

Here is how `OverlayTextView` looks with the above setup.
![Image Overlay Text]({{ site.url }}/{{site.baseurl}}/assets/overlayview.png)

Now we can display this view on top of our `backgroundImage` by calling the
`overlay` modifier as mentioned earlier. The photographer who took the image
is Grace Gallingam so we will display her name as a credit on our image.


{% highlight ruby %}
VStack(alignment: .leading) {
  Image("backgroundImage") // replace backgroundImage with your image name.
      .resizable()
      .aspectRatio(contentMode: .fit)
      .overlay(OverlayTextView(creditName: "Grace Galligan"), alignment: .bottomTrailing)
}
{% endhighlight %}

![Image Overlay Text]({{ site.url }}/{{site.baseurl}}/assets/overlaytextimage.png)

If you want to display the image on the top left we will pass `.topLeading` attribute to the
`alignment` parameter of the `overlay` modifier.
