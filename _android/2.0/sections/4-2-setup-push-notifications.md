
Liquid lets you combine segmentation with Push messages to send targeted campaigns to you users.

For this to work, you need to add some code that registers your device with Liquid and GCM (Google Cloud Messaging).

If you don't have a GCM Sender ID, please visit the [tutorial](/docs/dashboard/notifications#set-gcm-auth-key) about setting up GCM. The GCM Sender ID is the project number in the Google Console and should look something like "670330094152".

Then, add it to Liquid's instance:

{% highlight java %}
// MainActivity.java
Liquid liquid;

@Override
protected void onCreate(Bundle savedInstanceState) {
  liquid = Liquid.initialize(this, "YOUR_APP_TOKEN");
  liquid.setupPushNotifications(this, "YOUR_GCM_SENDER_ID");
}
{% endhighlight %}

If this is the first time Push Notifications are implemented in your app, continue on. Otherwise, if you already have your own Push Notification code set up, please skip to [this section](/docs/android/1.2#push-advanced).

### Install via Gradle

Add the dependency to your project-level build.gradle:

