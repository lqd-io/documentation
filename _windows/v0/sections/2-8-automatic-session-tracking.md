
Once again, like device information, you don't need to worry about session tracking. Liquid does it for you, using the following logic:

+ A session **starts** when the user is identified (using one of the user identification methods).
+ A session **ends** when the user closes the application for more than a predefined time (default is `30` seconds). This means that if the user closes the app for 15 seconds, and reopens it, session is considered the same.

We recommend you to keep the default value on this, but you can change the timeout value (in seconds) of a session by calling `SessionTimeout`:

{% highlight c# %}
Liquid.Instance.SessionTimeout = value;
{% endhighlight %}
