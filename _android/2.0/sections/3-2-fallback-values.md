
You should **always** define fallback values for your dynamic variables. This will avoid strange behaviors in cases where your app is first launched without an Internet connection, but also if you accidentally delete a variable in Liquid dashboard, or define a different data type between your code and Liquid dashboard.

Each time you use a dynamic variable, you can define its fallback value in the methods:

{% highlight java %}
Liquid.getInstance().getColorVariable(loginBgColor, Color.GREEN);
Liquid.getInstance().getDateVariable(promoDay, date);
Liquid.getInstance().getStringVariable(title, "Hello");
Liquid.getInstance().getIntVariable(abTestingLoginVersion, 3);
Liquid.getInstance().getFloatVariable(discount, 0.25);
Liquid.getInstance().getBooleanVariable(showAds, true);
{% endhighlight %}

To ease the development process, each time you use a dynamic variable, its fallback value will be sent to Liquid dashboard and stored as default value (**only** when your app is compiled with Liquid **in development mode**).
