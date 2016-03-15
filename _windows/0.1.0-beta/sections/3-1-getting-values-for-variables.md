
Based on variable names, Liquid returns values on five different data types: `DateTime`, `string`, `int`, `float` and `bool`. These methods return the `fallbackValue` if the value is not present or valid.

{% highlight java %}
await Liquid.Instance.GetColorVariable(variableKey, fallbackValue);
await Liquid.Instance.GetDateVariable(variableKey, fallbackValue);
await Liquid.Instance.GetStringVariable(variableKey, fallbackValue);
await Liquid.Instance.GetIntVariable(variableKey, fallbackValue);
await Liquid.Instance.GetFloatVariable(variableKey, fallbackValue);
await Liquid.Instance.GetBooleanVariable(variableKey, fallbackValue);
{% endhighlight %}
