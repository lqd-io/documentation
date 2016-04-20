
Most of the times, it is useful to have all dynamic variables and their fallback values in the same place.

This kind of practice not only improves code organization and readability, but also reutilization of static values in your code.

This way, we recommend you to create a static class file, like:

{% highlight java %}
public class DefaultValues {
  public static final String WELCOME_MESSAGE = "Ahoy!";
  public static final int BG_COLOR = Color.BLUE;
  public static final float DISCOUNT = 0.25f;
  public static final boolean SHOW_ADS = true;
}
{% endhighlight %}

By doing that you easily change the default variables without changing all activities, like:

{% highlight java %}
bg.setBackgroundColor(Liquid.getInstance().getColorVariable("bgcolor", DefaultValues.bg_color));
{% endhighlight %}

while keeping a list of your dynamic variables and fallback values in one unique place.

{% include alert.md type='warning' message="Most of the times, you'll want to make sure that your *default values* (in Liquid dashboard) are the same as the *fallback values* (in your code)." %}
