
If you never identify your user, all activity will be tracked anonymously. As soon as a user is identified, all that anonymous activity will be automatically **aliased** to the identified user. This means that you'll no longer see the anonymous user, but the identified one.

This process of user aliasing is automatic, is the default behavior and is **higly recommended** that you alias your users. However, if you don't want this behavior, you may use the attribute `false` like shown in the following example:

{% highlight c# %}
await Liquid.Instance.IdentifyUser(identifier, attributes, false);
{% endhighlight %}

{% include alert.md type='info' message="Our recommendation is to keep your users identified as much as you can, even after they logout. This will ease the analysis of their behaviour." %}
