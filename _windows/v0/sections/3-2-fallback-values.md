
You should **always** define fallback values for your dynamic variables. This will avoid strange behaviors in cases where your app is first launched without an Internet connection, but also if you accidentally delete a variable in Liquid dashboard, or define a different data type between your code and Liquid dashboard.

{% highlight c# %}
await Liquid.Instance.GetColorVariable(loginBgColor, Colors.Green);
await Liquid.Instance.GetDateVariable(promoDay, date);
await Liquid.Instance.GetStringVariable(title, "Hello");
await Liquid.Instance.GetIntVariable(abTestingLoginVersion, 3);
await Liquid.Instance.GetFloatVariable(discount, 0.25);
await Liquid.Instance.GetBooleanVariable(showAds, true);
{% endhighlight %}

To ease the development process, each time you use a dynamic variable, its fallback value will be sent to Liquid dashboard and stored as default value (**only** when your app is compiled with Liquid **in development mode**).
