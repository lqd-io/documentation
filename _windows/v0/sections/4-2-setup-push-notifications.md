
If you want to take advantage of the powerful Liquid segmentation feature to send Push Notifications to your users devices, you'll need to inform Liquid about their WNS Application SID (Windows Notification Application ID) and its Secret.

This is done by calling `setupPushNotifications` method at the moment you have access to the Registration ID. If you already have your own push notification mechanism, please skip to [this section](#advanced-settings).

* To enable Toast Notifications you should go to your Application Manifest and choose `Yes` in the *Toast Capable* option as the image suggests:
<img src='{{ site.github.url }}/assets/windows/push_notifications_screen_1.png' data-action='zoom'/>

#### Register user to receive Push-Notifications

In order to configure your application to receive push notifications through Liquid you should call the `SetupPushNotifications` method as follows:

{% highlight c# %}
// App.xaml.cs
protected async override void OnLaunched(LaunchActivatedEventArgs e)  { 
  await Liquid.Initialize("YOUR-APP-TOKEN", this, e);
  await Liquid.Instance.SetupPushNotifications();
  /* (...) */ 
}
{% endhighlight %}

#### Advanced settings

If you already have your own mechanism to send push notifications, you just need to inform Liquid of your user WNS Uri, like this:

{% highlight c# %}
// App.xaml.cs
protected async override void OnLaunched(LaunchActivatedEventArgs e)  {
  await Liquid.Initialize("YOUR-APP-TOKEN", this, e);
  Liquid.Instance.SetWNSDeviceUri(wnsRegistrationUri);
  /* (...) */ 
}
{% endhighlight %}

The push notifications from Liquid will contain the key `lqd_message`, associated with the text of the message that you created from Liquid Dashboard.

#### Configure WNS Application SID and Secret

To send Push Notifications as your App, Liquid must authenticate with Microsoft’s WNS, using your Application SID and the Application Secret.

Check [this](/dashboard/notifications#configure-wns-sid-and-secret/) section to know how to import it to Liquid dashboard.
