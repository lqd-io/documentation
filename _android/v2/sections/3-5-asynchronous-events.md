
Optionaly, you can be notified of Liquid's internal events by implementing `LiquidOnEventListener` interface on your code, to take action when:

* When values are received from Liquid dashboard (not necessarily loaded)
* When values are loaded

As an example, let's assume you want to take action in your activity, then you should implement the `LiquidOnEventListener` interface like this:

{% highlight java %}
// Your activity
public class MainActivity extends Activity implements LiquidOnEventListener {
  // Define your code here...
}
{% endhighlight %}

and your implementation file should be like this:

{% highlight java %}
@Override
public void onValuesReceived() {
  // Do something with new values, e.g: Liquid.getInstance().loadNewValues();
}

@Override
public void onValuesLoaded() {
  bg.setBackgroundColor(Liquid.getInstance().getColorVariable("bgcolor", Color.GRAY));
  // Define your code here...
}
{% endhighlight %}
