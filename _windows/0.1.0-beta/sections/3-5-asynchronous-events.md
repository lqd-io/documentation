
Optionally you can be notified of Liquid internal internal events by implementing `ValuesReceived` and `ValuesLoaded` to take action when:

* When values are received from Liquid dashboard (not necessarily loaded)
* When values are loaded

If you want to be notified of those events, you just need to implement `LiquidOnEventListener` interface on your code.

As an example, assuming that you want to take action on your activity, you should implement the `LiquidOnEventListener` interface like this:

{% highlight c# %}
// For example where you initialize Liquid
Liquid.ValuesReceived += LiquidValuesReceived;
Liquid.ValuesLoaded += LiquidValuesLoaded;
{% endhighlight %}

and your implementation file should be like this:

{% highlight c# %}
private void LiquidValuesReceived(object sender, EventArgs e)  {
  // Do something with new values, e.g: await Liquid.Instance.LoadValues(); 
}

private async void LiquidValuesLoaded(object sender, EventArgs e) {
  Background = new SolidColorBrush(await Liquid.Instance.GetColorVariable("bgcolor", Colors.Gray));
  // Define your code here...  
}
{% endhighlight %}
