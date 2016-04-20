
User attributes are Key-Value objects stored in the form of a `NSDictionary`.

Data types of these attributes can be: `NSString`, `NSDate`, `NSNumber` and `NSNull`. Primitive types are **NOT** allowed. Use objects only.

An example that includes all this attributes could be:

{% highlight swift %}
NSDictionary *userAttributes = @{
  @"name": @"Anna",
  @"woman": @YES,
  @"facebookId": @"123456789",
  @"age": @25
};
{% endhighlight %}

Usually you track these attributes when you [identify your user](#identify-your-users), but you can also set those attributes anytime using one of the following methods, depending on the number of attributes you're tracking:

{% highlight swift %}
[[Liquid sharedInstance] setUserAttribute:@25 forKey:@"age"];
[[Liquid sharedInstance] setUserAttributes:@{
  @"age": @25,
  @"name": @"Anna"
}];
{% endhighlight %}

{% include alert.md type='info' message="You should not store nothing more than user information on this collection, i.e. do not store information related with the device (like model or carrier). This information is stored on the device entity, as explained below." %}
