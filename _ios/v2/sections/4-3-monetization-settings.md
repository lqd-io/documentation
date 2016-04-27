
On the **Dashboard section** [(check the demo)](https://onliquid.com/demo/) you will find your app's Monetization metrics (Conversions, Purchases and Revenue) for the last 30 days. In order to set these values properly follow the guide bellow.

#### Conversions

A conversion can be any event (such as a purchase or a sign-up) that you consider important in the context of your app. You can pick up to 5 events and you'll instantly get insights on how these events performed (converted) in the last 30 days:

* click on <span class='fa fa-cog'></span> **Settings** and select up to 5 events that you consider to be a *conversion*
<img src='{{ site.github.url }}/assets/shared/setup_conversion@2x.png' alt='Track a Conversion whenever a user does any of these events' data-action='zoom'/>

#### Purchases

Every event that has the attribute `price` is automatically considered a *purchase*.

An example would be:

{% highlight swift %}
// The price value must be an integer
[[Liquid sharedInstance] track:@"Buy Product" attributes: @{ @"price": 10 }];
{% endhighlight %}

#### Revenue

The sum of all values (integer) of the attribute `price` included on all events.
