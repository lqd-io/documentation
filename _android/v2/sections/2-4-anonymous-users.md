
If you never identify your user, all activity will be tracked anonymously. As soon as a user is identified, all that anonymous activity will be automatically **aliased** to the identified user. This means that you'll no longer see the anonymous user, but the identified one.

This process of user aliasing is automatic, is the default behavior and is **higly recommended** that you alias your users. However, if you don't want this behavior, you may append the prefix `alias:false` when identifying your user, like shown in the following example:

{% highlight java %}
Liquid.getInstance().identifyUser(identifier, attributes, false);
{% endhighlight %}

{% include alert.md type='info' message="Our recommendation is to keep your users identified as much as you can, even after they logout. This will ease the analysis of their behaviour. However, if for any reason you really want to turn the SDK back to the anonymous state, you can use the method `Liquid.getInstance().resetUser();`. This will create a new anonymous user (with a new Unique ID and no custom attributes). If your user is already anonymous, this will only wipe their attributes, leaving the unique_id intact." %}
