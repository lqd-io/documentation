
To send Push Notifications to your users' devices through Liquid's segmentation feature you'll just need two things:

* Register for Push Notifications on Apple servers

* Inform Liquid about each device's APNS (Apple Push Notification) key.

This is done in your `didFinishLaunchingWithOptions:` (for the 1st step) and by calling `setApplePushNotificationToken:` method at the moment you have access to the key (for the 2nd step), like shown below:

{% highlight swift %}
// AppDelegate.m

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    [application registerForRemoteNotificationTypes:(UIRemoteNotificationTypeAlert | UIRemoteNotificationTypeBadge | UIRemoteNotificationTypeSound)];
    return YES;
}

- (void)application:(UIApplication *)app didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken {
    [[Liquid sharedInstance] setApplePushNotificationToken:deviceToken];
}

- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo {
    [[Liquid sharedInstance] handleRemoteNotification:userInfo forApplication:application];
}
{% endhighlight %}

Configure APNS Certificate

To send Push Notifications as your App, Liquid must authenticate with Apple's Push Notification Service (APNS) using your App's certificate.

Check our [Push Notifications Documentation](/documentation/dashboard#import-apns-cert) to learn how to set it up on Liquid dashboard.
