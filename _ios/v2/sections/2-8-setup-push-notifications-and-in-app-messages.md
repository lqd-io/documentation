
To send push notifications and in-app messages to your users' through Liquid's formulas you'll just need three things:

* Register for push notifications on Apple servers

* Inform Liquid about each device's APNS (Apple Push Notification) key.

* Notify Liquid SDK to handle incoming push notifications

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

#### Configure APNS Certificate

To send Push Notifications as your App, Liquid must authenticate with Apple's Push Notification Service (APNS) using your App's certificate. Check the [Setup push notifications certificates](#setup-push-notifications-certificates) section to learn how to set it up on Liquid dashboard.
