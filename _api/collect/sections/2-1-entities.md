
#### Timestamp

The date and time (a string with the ISO 8601 format) of the moment the event happens.

---

#### User

Contains information about the user that performed the event, a unique identifier (like a primary key) that uniquely identifies the user, a flag stating if the user is **anonymous** or **identified** and other optional custom fields.

##### Mandatory fields:

{% include field.html key='unique_id' type='String' description='A unique ID that uniquely identifies the user. For anonymous users we recommend [using a strong UUID](good-practices).' example='username@example.com' %}

{% include field.html key='identified' type='Boolean' description='Should be `true` if the user is identified, `false` if user is anonymous.' example='`true`' %}

##### Custom fields (optional):

You can always include custom fields, Liquid supports `String`, `Integer`, `Float`, `Boolean` or `DateTime(ISO8601)`, for example:

{% highlight json %}
{
  "user": {
    "age": 30,
    "identified": true,
    "name": "Username",
    "rating": 4.3,
    "sign_up_date": "2016-01-01T00:00:00.000+00:00",
    "unique_id": "02318f2cdd156d78fd4431"
  }
}
{% endhighlight %}

---

#### Device

Contains information about the device where the user generated the event. The only mandatory field is `unique_id`. All the other fields are optional but recommended to be present, as they're very useful for segmentation on Liquid dashboard.

##### Mandatory fields:

{% include field.html key='unique_id' type='String' description='A unique ID that uniquely identifies the device.' example='`"BE74F041-69B7-4E3B-AB91-A3C7FD150683"`' %}

##### Custom fields (optional):

{% highlight json %}
{
  "device": {
    "app_bundle": "io.lqd.LiquidDemo",
    "app_name": "Demo App",
    "app_version": 1.0,
    "release_version": "1.0.1",
    "carrie": "Vodafone",
    "internet_connectivity": "Cellular",
    "sdk_version": "1.0.0",
    "mode": "iPad2,5",
    "name": "Username's iPad",
    "vendor": "Apple",
    "push_token": "5862036a860b6aa...c8190cfa61526ce30",
    "screen_size": "768x1024",
    "system_version": "7.0.1",
    "system_language": "en_GB",
    "locale": "en_GB",
    "latitude": 41.342543,
    "longitude": -8.846341,
    "unique_id": "BE74F041-69B7-4E3B-AB91-A3C7FD150683"
  }
}
{% endhighlight %}

---

#### Event

Contains information about the event. The only mandatory field is `name`, which should contain a string with a name that describes the event. All the other fields are custom attributes related with the event, e.g.: `product_id: 5634` or `price: 13.54`.

##### Mandatory fields:

{% include field.html key='name' type='String' description='An identifier, event names should have a minimum length of 3 characters and a maximum of 50.' example='"buy_product"' %}

##### Custom fields (optional):

{% highlight json %}
{
  "event": {
    "name": "Buy Product",
    "product_id": "57634",
    "price": 13.54
  }
}
{% endhighlight %}

---
