
Most of the times, it is useful to have all dynamic variables and their fallback values in the same place.

This kind of practice not only improves code organization and readability, but also reutilization of static values in your code.

This way, we recommend you to create `FallbackVariables.{h,m}` files, like shown on the example below:

{% highlight c# %}
public class DefaultValues {
  public static final String welcome_message = "Welcome!";
  public static final int bg_color = Color.BLUE;
  public static final float discount = 0.25f;
  public static final bool show_ads = true;
}
{% endhighlight %}

By doing that you easily change the default variables without changing all activities, like:

{% highlight c# %}
Background = new SolidColorBrush(await Liquid.Instance.GetColorVariable("bgcolor", DefaultValues.bgColor));
{% endhighlight %}

{% include alert.md type='warning' message="Most of the times, you'll want to make sure that your **default values** (in Liquid dashboard) are the same as the **fallback values** (in your code)." %}
