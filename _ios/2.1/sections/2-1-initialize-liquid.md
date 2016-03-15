
{% include alert.md type='warning' message="For every app you add on Liquid, two versions of the app are created: a **production** and a **development** version. These versions have completely distinct environments (i.e., different users, devices, sessions, events, targets and dynamic variables) and each app version has **its own API key**." %}

You can initialize Liquid singleton (once per app launch) with your app API key. Typically, the best place to do this is on `application:willFinishLaunchingWithOptions:` method at your `AppDelegate.m` file.

You can find your App API key on the <span class='fa fa-cog'></span> **App Settings** of Liquid's dashboard.

{% highlight swift %}
// AppDelegate.m

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {

  // assuming that you're using a DEBUG flag
  #ifdef DEBUG
    [Liquid sharedInstanceWithToken:@"YOUR-DEVELOPMENT-APP-TOKEN" development:YES];
  #else
    [Liquid sharedInstanceWithToken:@"YOUR-PRODUCTION-APP-TOKEN"];
  #endif

  // The rest of your code goes here...
  return YES;
}
{% endhighlight %}

From this moment on, each time you want to call a Liquid method you can do:

{% highlight swift %}
[Liquid sharedInstance];
{% endhighlight %}

{% include alert.md type='info' message="All interactions using Liquid SDK should be done using this shared instance of `Liquid` object (and not using `LQ*` models)." %}
