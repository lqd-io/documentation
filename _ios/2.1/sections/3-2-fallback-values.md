
You should **always** define fallback values for your dynamic variables. This will avoid strange behaviors in cases where your app is first launched without an Internet connection, but also if you accidentally delete a variable in Liquid dashboard, or define a different data type between your code and Liquid dashboard.

Each time you use a dynamic variable, you can define its fallback value using the `fallback:` suffix in Liquid **KVO** (Key-Value Observing) methods:

{% highlight swift %}
NSString *title = [[Liquid sharedInstance] stringForKey:@"title" fallback:@"Be welcome!"];
UIColor *bgcolor = [[Liquid sharedInstance] colorForKey:@"loginBgColor" fallback:[UIColor red]];
NSDate *promoDay = [[Liquid sharedInstance] dateForKey:@"promoDay" fallback:[NSDate date]];
NSInteger abTesting = [[Liquid sharedInstance] intForKey:@"loginVersion" fallback:3];
CGFloat discount = [[Liquid sharedInstance] floatForKey:@"discount" fallback:0.25];
BOOL *initialAds = [[Liquid sharedInstance] boolForKey:@"showAds" fallback:YES];
{% endhighlight %}

To ease the development process, each time you use a dynamic variable, its fallback value will be sent to Liquid dashboard and stored as default value (**only** when your app is compiled with Liquid **in development mode**).
