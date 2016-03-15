
If you have information about user geolocation (a `CLLocation`) you can use Liquid to track device location. All you need to do is to inform Liquid SDK about current device location using the following method:

{% highlight swift %}
[[Liquid sharedInstance] setCurrentLocation:YOUR-CLLOCATION-INSTANCE];
{% endhighlight %}

Liquid doesn't automatically track location changes. This means you're responsible to inform Liquid SDK each time device location changes. This is usually done in your `CLLocationManagerDelegate` delegated method, like:

{% highlight swift %}
- (void)locationManager:(CLLocationManager *)manager didUpdateToLocation:(CLLocation *)newLocation fromLocation:(CLLocation *)oldLocation {
    // The rest of your code...
    [[Liquid sharedInstance] setCurrentLocation:newLocation];
}
{% endhighlight %}

From this moment on, all data points sent to Liquid will include `latitude` and `longitude` attributes associated to Device entity.
