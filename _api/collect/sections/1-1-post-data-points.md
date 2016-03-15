
This endpoint is used to create a data point. The only request format accepted is JSON.

Session handling is automatically managed by Liquid backend, and not at the generation of a data point. Two data points are considered on the same session if they're timestamps are close to each other in less than the *maximum time between two events after which a new session is inferred* (e.g. if a data point is not within 5 minutes or less from an already existent data point it will generate a new session, otherwise it will be added to the session of that already existent data point). You may to change this definition by setting this value in your App Settings.

It is **very important** to understand the [structure of a data point](#structure-of-a-data-point) before creating them.

#### Headers

| Header | Example | Notes |
| --- | --- | --- |
| Authorization | `Token vE_S7CluDfNVPx_UgWCpn-5CPszRCOjC` | The app API key |
| Accept | `application/json` | Use `application/vnd.lqd.v1+json` if you want to stick to a specific API version. |
| Content-Type | `application/json` | |

#### Resource URL

`https://collect.lqd.io/data_points`

#### Parameters

We highly recommend a full understanding of the structure of a data point before generating new data points. A full explanation of each of those parameters and its nested attributes is **[explained below](#structure-of-a-data-point)**.

{% include field.html key='timestamp' type='String (ISO8601)' description='The date and time of the moment the event happens.' example='`"2015-01-07T17:28:05.270+00:00"`' %}

{% include field.html key='user' type='Hash/Dictionary' description='Check [data point structure](#structure-of-a-data-point) for full info.' example='`{ "unique_id": "02318f2cdd156d78fd4431", "identified": true, "name": "John Doe", "age": 30 }`' %}

{% include field.html key='device' type='Hash/Dictionary' description='Check [data point structure](#structure-of-a-data-point) for full info.' example='`{ "unique_id": "F348DE-31E0-4ACF-B2B0-5065FF8FCFB0", "model": "iPad2,5", vendor: "Apple" }`' %}

{% include field.html key='event' type='Hash/Dictionary' description='Check [data point structure](#structure-of-a-data-point) for full info.' example='`{ "name": "Buy Product", "product_id": 3293 }`' %}

#### Example request

**POST**

`https://collect.lqd.io/data_points`

{% highlight json %}
{
  "timestamp": "2015-01-07T17:28:58.270+00:00",
  "user": {
    "unique_id": "02318f2cdd156d78fd4431",
    "identified": true,
    "first_name": "John",
    "last_name": "Doe",
    "age": 30,
    "gender": "male"
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
    "push_token": "5862036a860c6b6aada50117caea626d20ed3187d6981c8190cfa6199526ce30",
    "screen_size": "768x1024",
    "system_version": "7.0.1",
    "system_language": "en_GB",
    "locale": "en_GB"
  },
  "event": {
    "name": "Buy Product",
    "product_id": 3293,
    "price": 17.24
  }
}
{% endhighlight %}

#### Response

| Code | Status | Content | Scenario
| --- | --- | --- | ---
| 200 | OK | n/a | Data point is valid and was enqueued for processing.
| 400 | Bad Request | n/a | Content is not a valid JSON.
| 401 | Unauthorized | n/a | Authorization failed (invalid API token).
| 422 | Unprocessable Entity | Production app: n/a <br /> Development app: error message (see below) | Data point is invalid.

Error messages for **Unprocessable Entity (422)** have the following structure:

{% highlight json %}
{
  "error": "Error Message",
  "details": "A string explaining the error in detail"
}
{% endhighlight %}
