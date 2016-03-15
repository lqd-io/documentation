
In order to keep track of a specific user between different sessions and devices (or different app installations) you must identify it with a **unique identifier**. This will allow you to use analytics based on their information.

This identifier is usually a strong UUID, e.g: `"02318f2cdd156d78fd4431"`. We recommend using your back-end database ID to identify a user. Alternatively, you can use an email or username, provided they **cannot be changed**.

Tipically, you know more about your user than only his identifier. Liquid allows you to create analytics based on this information through Key-Value user attributes (on a `NSDictionary`).

For each of the above situations, you should identify your user with one of the following two methods, respectively:

{% highlight swift %}
// Only use this method on anonymous users.

[[Liquid sharedInstance] identifyUserWithIdentifier:@"UNIQUE-USER-ID"];
[[Liquid sharedInstance] identifyUserWithIdentifier:@"john.doe@gmail.com" attributes:@{ @"age": @35 }];
{% endhighlight %}

It is not mandatory to the user attributes at the moment of user identification. You can set their attributes later [using setter methods](#user-attributes).

{% include alert.md type='info' message="Liquid SDK keeps a cache of your previously identified user. This means that you don't need to identify your user each time your app is open." %}
