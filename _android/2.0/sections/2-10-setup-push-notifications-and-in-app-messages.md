
To send push notifications and in-app messages to your users through Liquid's formulas you'll need to add some code that registers your device with Liquid and GCM (Google Cloud Messaging)

If you don't have a GCM Sender ID, please visit the [tutorial](#setup-push-notifications-certificates) about setting up GCM. The GCM Sender ID is the project number in the Google Console and should look something like "670330094152".

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

#### Install via Gradle

Add the dependency to your project-level build.gradle:

{% highlight java %}
// Top-level build file where you can add configuration options common to all sub-projects/modules.
dependencies {
  ...
  classpath "com.google.gms:google-services:1.5.0-beta2"
}
{% endhighlight %}

Add the plugin and the dependency to your app-level build.gradle file:

{% highlight java %}
// build.gradle file
apply plugin: "com.google.gms.google-services"
...
dependencies {
  ...
  compile "com.google.android.gms:play-services-gcm:8.3.0"
}
{% endhighlight %}

#### Add Permissions to Application Manifest

The following permissions are required, replace `YOUR_APP_PACKAGE_NAME` with your own app package name.:

{% highlight xml %}
<!-- AndroidManifest.xml -->
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />

<permission android:name="YOUR_APP_PACKAGE_NAME.C2D_MESSAGE" android:protectionLevel="signature" />
<uses-permission android:name="YOUR_APP_PACKAGE_NAME.permission.C2D_MESSAGE" />

<uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" />
<uses-permission android:name="android.permission.WAKE_LOCK" />
<uses-permission android:name="android.permission.VIBRATE"/>
{% endhighlight %}

Next, register the Google receiver and the Liquid's message handling service adding the following snippet inside the `<application>` tag:

{% highlight xml %}
<!-- AndroidManifest.xml -->
<receiver
  android:name="com.google.android.gms.gcm.GcmReceiver"
  android:permission="com.google.android.c2dm.permission.SEND" >
  <intent-filter>
      <action android:name="com.google.android.c2dm.intent.RECEIVE" />
      <action android:name="com.google.android.c2dm.intent.REGISTRATION" />
      <category android:name="YOUR_APP_PACKAGE_NAME" />
  </intent-filter>
</receiver>

<service
  android:name="io.lqd.sdk.gcm.LQMessageHandler"
  android:exported="false" >
  <intent-filter>
      <action android:name="com.google.android.c2dm.intent.RECEIVE" />
  </intent-filter>
</service>
{% endhighlight %}

{% include alert.md type='warning' message="Android devices with an SDK version older than 8.0 cannot receive Google Cloud Messaging notifications." %}

#### Advanced settings

If you already have your own mechanism to send push notifications, you just need to inform Liquid of your user GCM Registration ID, like this:

{% highlight java %}
public class YourIntentService extends GCMBaseIntentService {

  protected void onRegistered(Context context, String registrationId) {
    Liquid.getInstance().setGCMregistrationID(registrationId);
  }
}
{% endhighlight %}

##### Payload in push notifications

Liquid sends the following payload to Android devices:

* Title - `lqd_title`
* Message - `lqd_message`
* Sound - `lqd_sound`

If add custom JSON, it will be merged to the root of the payload.

{% include alert.md type='warning' message="Your JSON will have priority over the default keys (lqd_*)." %}

##### Custom icon in notifications

If you want to add a custom icon to your notification, add the following meta-data inside the `<application>` tag and place your custom icon inside the drawable folder.

{% highlight java %}
<!-- AndroidManifest.xml -->
<aplication>
...
  <meta-data android:name="io.lqd.sdk.notification_icon"
    android:resource="@drawable/CUSTOM_ICON"/>
...
</aplication>
{% endhighlight %}

##### Configure GCM Sender ID

To send Push Notifications as your App, Liquid must authenticate with Google GCM, using your App's GCM Auth Key.

Check [Setup push notifications certificates](#setup-push-notifications-certificates) section to know how to import it to Liquid dashboard.
