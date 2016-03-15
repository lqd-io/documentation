
If you have information about user geolocation (a `Location`) you can use Liquid to track device location. All you need to do is to inform Liquid SDK about current device location using the following method:

{% highlight c# %}
await Liquid.Instance.SetCurrentLocation(Geocoordinate gc);
{% endhighlight %}

Liquid doesn't automatically track location changes. This means you're responsible to inform Liquid SDK each time device location changes.

From this moment on, all data points sent to Liquid will include `latitude` and `longitude` attributes associated to Device entity.
