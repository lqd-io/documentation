
Probably the most important entity of analytics is an event. Events can be anything you want in the context of your application. It can be a click on a button, a product that is bought or any other interaction. Events are identified by a unique name, and can (optionally) have attributes (Key-Value).

{% include alert.md type='warning' message='Event names should have a minimum length of 3 characters and a maximum of 50. Also note that Liquid uses the attribute `name` to store the event name. If you set a custom event attribute with the key `name` it will be overrided by the SDK.' %}

You can track an event anytime you want on your code, using one of the following methods:

{% highlight java %}
Liquid.getInstance().track("Click Profile Page");
Liquid.getInstance().track("Buy Product", attrs);
{% endhighlight %}

##### Track your Monetization metrics

In order to take advantage of the Monetization section of the Dashboard view, you have to send a `price` attribute on your events, make sure to check the [Monetization settings](#monetization-settings) section for detailed information.
