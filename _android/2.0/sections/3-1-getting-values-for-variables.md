
Based on variable names, Liquid returns values on five different data types: `Date`, `String`, `int`, `float` and `boolean`. These methods return the `fallbackValue` if the value is not present or valid.

{% highlight java %}
Liquid.getInstance().getStringVariable(variableKey, fallbackValue);
Liquid.getInstance().getColorVariable(variableName, fallbackValue);
Liquid.getInstance().getDateVariable(variableKey, fallbackValue);
Liquid.getInstance().getIntVariable(variableKey, fallbackValue);
Liquid.getInstance().getFloatVariable(variableKey, fallbackValue);
Liquid.getInstance().getBooleanVariable(variableKey, fallbackValue);
{% endhighlight %}
