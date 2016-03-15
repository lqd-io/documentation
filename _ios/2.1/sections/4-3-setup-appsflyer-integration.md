
If you're already using AppsFlyer in your app, you can view the user acquisition source on Liquid following this guide:

* On your app, after initializing our SDK set AppsFlyer customer user id to Liquid `device unique_id`:

{% highlight swift %}
[[AppsFlyerTracker sharedTracker] setCustomerUserID:[[Liquid sharedInstance] deviceIdentifier]];
{% endhighlight %}

* Select Liquid on the AppsFlyer integration menu, they'll ask for your Liquid App key that is available in your app settings page.
