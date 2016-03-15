
Creates a user alias, typically to alias an anonymous user to an identified user. Aliasing a user to another one merges all user's history (profile and behaviour information) from the "old" user (typically the anonymous one) to the "new" user (typically the identified one). This means that you'll see **only one user** on Liquid dashboard, independently of the unique ID you're using on the data point's `user.unique_id`.

Furthermore, after the creation of an alias, all data points received from the old (aliased) user will be associated to the new one.

{% include alert.md type='warning' message='This process is not reversible, i.e. after creating an alias it is not possible to destroy it.' %}

#### Headers

| Header | Example | Notes |
| --- | --- | --- |
| Authorization | `Token vE_S7CluDfNVPx_UgWCpn-5CPszRCOjC` | The app API key, available at the App settings on Liquid dashboard.
| Accept | `application/json` | Optionally, use `application/vnd.lqd.v1+json` if you want to stick to a specific API version. |
| Content-Type | `application/json` | |

#### Resource URL

`https://collect.lqd.io/alias`

#### Parameters

Both parameters of this endpoint are User unique IDs. The `unique_id_alias` (the old user) is the user ID of the user that will be an alias to the `unique_id` (the new user). The typical situation is the example below, where `02318f2cdd156d78fd4431` signs up and "receives" all the analytics data from the period before the sign-up (while anonymous, with the identifier `F348DE-31E0-4ACF-B2B0-5065FF8FCFB0`).

{% include field.html key='unique_id' type='String' description='The unique ID of the reference user (tipically an identified/non-anonymous user).' example='`"02318f2cdd156d78fd4431"`' %}

{% include field.html key='unique_id_alias' type='String' description='The unique ID of the user that is being aliased (tipically an anonymous user).' example='`"F348DE-31E0-4ACF-B2B0-5065FF8FCFB0"`' %}

### Example Request

**POST**

`https://collect.lqd.io/alias`

{% highlight json %}
{
  "unique_id": "02318f2cdd156d78fd4431",
  "unique_id_alias": "F348DE-31E0-4ACF-B2B0-5065FF8FCFB0"
}
{% endhighlight %}

#### Response

| Code | Status | Content | Scenario
| --- | --- | --- | ---
| 201 | Created | n/a | Alias was successfuly created.
| 400 | Bad Request | n/a | Content is not a valid JSON.
| 401 | Unauthorized | n/a | Authorization failed (invalid API token).
| 422 | Unprocessable Entity | Production app: n/a <br/> Development app: error message (see below) | Alias is invalid.

Error messages for **Unprocessable Entity (422)** have the following structure:

{% highlight json %}
{
  "error": "Error Message",
  "details": "A string explaining the error in detail"
}
{% endhighlight %}
