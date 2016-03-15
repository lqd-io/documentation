
#### Example of a minimum-filled data point:

An example of a data point with just the minimum required fields is shown below:

{% highlight json %}
{
  "timestamp": "2016-01-01T00:00:00.000+00:00",
  "user": {
    "unique_id": "02318f2cdd156d78fd4431",
    "identified": true
  },
  "device": {
    "unique_id": "78F348DE-31E0-4ACF-B2B0-5065FF8FCFB0"
  },
  "event": {
    "name": "buy_product"
  }
}
{% endhighlight %}

#### Example of a fully-filled data point

An example of a data point with all the recommended fields present plus some custom attributes on User, Device and Event is shown below:

{% highlight json %}
{
  "timestamp": "2016-01-07T17:28:58.270+00:00",
  "user": {
    "unique_id": "02318f2cdd156d78fd4431",
    "identified": true,
    "first_name": "User",
    "last_name": "Name",
    "age": 30,
    "gender": "male",
    "sign_up_date": "2016-01-07T17:28:05.270+00:00"
  },
  "device": {
    "unique_id": "78F348DE-31E0-4ACF-B2B0-5065FF8FCFB0",
    "app_bundle": "io.lqd.LiquidDemo",
    "app_name": "Demo App",
    "app_version": "1.0",
    "release_version": "1.0.1",
    "carrier": "Vodafone",
    "internet_connectivity": "Cellular",
    "sdk_version": "1.0.0",
    "model": "iPad2,5",
    "name": "Username's iPad",
    "vendor": "Apple",
    "push_token": "52036a860c6b6aada50117caea626d20ed3187d6981c8190cfa6199526ce30",
    "screen_size": "768x1024",
    "system_version": "7.0.1",
    "system_language": "en",
    "locale": "en",
    "latitude": 41.342543,
    "longitude": -8.846341
  },
  "event": {
    "name": "Buy Product",
    "product_id": 3293,
    "price": 17.24
  }
}
{% endhighlight %}
