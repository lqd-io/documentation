
Returns aggregated data about a user. It contains three keys:

{% highlight json %}
{
  "attrs": {},
  "last_device": {},
  "session": {}
}
{% endhighlight %}

| Attribute | Description |
| --- | --- |
| `attrs` | User attributes, including custom ones. These are accumulated and reflect the last known information of each user.
| `last_device` | Information about the last device used by this user.
| `session` | Session-related metrics of this user.

#### Headers

| Header | Example | Notes |
| --- | --- | --- |
| Authorization | `Token vE_S7CluDfNVPx_UgWCpn-5CPszRCOjC` | The app API key, available at the App settings on Liquid dashboard.
| Accept | `application/vnd.lqd.v1+json` | Optionally, you can use `application/json` if you don't care about which api version you are using, notice future changes may break you code if you do this. |
| Content-Type | `application/json` | |

#### Resource URL

`https://analyze.lqd.io/users/:unique_id`

{% include alert.md type='warning' message='The `unique_id` attribute should be URL encoded.' %}

#### Example Request

**GET**

`https://analyze.lqd.io/users/02318f2cdd156d78fd4431`

#### Example Result

{% highlight json %}
{
    "id": "559d081f70726f181222a1a7",
    "attrs": {
        "campaign": null,
        "churn_prob": 1,
        "city": "Bristol",
        "country": "United Kingdom",
        "country_code_alpha2": "UK",
        "devices_count": 1,
        "first_seen_at": "2015-07-08T11:23:08.514+00:00",
        "identified": false,
        "last_seen_at": "2015-07-08T11:23:09.822+00:00",
        "mediasource": null,
        "unique_id": "02318f2cdd156d78fd4431"
    },
    "last_device": {
        "unique_id": "78F348DE-31E0-4ACF-B2B0-5065FF8FCFB0",
        "first_seen_at": "2015-07-08T11:23:08.514+00:00",
        "last_seen_at": "2015-07-07T10:22:08.822+00:00",
        "app_bundle": "io.lqd.LiquidDemo",
        "app_name": "Demo App",
        "ip_address": "8.8.8.8",
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
        "system_language": "en",
        "locale": "en"
    },
    "session": {
        "avg_length": 93,
        "max_length": 240,
        "min_length": 30,
        "total_length": 1395,
        "total_number": 15
    }
}
{% endhighlight %}

#### Response

| Code | Status | Content | Scenario
| --- | --- | --- | ---
| 200 | Ok | A JSON object representing the user. See the example above. | Existing user.
| 404 | Not Found | n/a | User was not found.
| 401 | Unauthorized | n/a | Authorization failed (probably you used an invalid API token).

Error messages for **Unprocessable Entity (422)** have the following structure:

{% highlight json %}
{
  "message": "Error Message"
}
{% endhighlight %}
