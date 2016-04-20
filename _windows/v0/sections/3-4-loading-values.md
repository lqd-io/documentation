
Each time your app is open or closed/paused, new values are requested to Liquid. However, **they are not immediately loaded by the SDK** as it could cause strange behaviors in front of user eyes. By default, when new values are available, they will only be loaded the next time your app is open.

You can change this behavior just by setting `AutoLoadVariables` variable to `true` after initializing Liquid singleton:

{% highlight swift %}
Liquid.Instance.AutoLoadValues = true;
{% endhighlight %}
