
{% include alert.md type='warning' message="For every app you add on Liquid, two versions of the app are created: a **production** and a **development** version. These versions have completely distinct environments (i.e., different users, devices, sessions, events, targets and dynamic variables) and each app version has **its own API key**." %}

Once you've set up the permissions, you must initialize the Liquid singleton (once per app launch) with your App's **API key**. Typically, the best place to do this is on the `public void onCreate()` method in your *Application* class.

You can find your App API key on the <span class='fa fa-cog'></span> **App Settings** of Liquid's dashboard.

{% highlight java %}
// first Activity file
@Override
protected void onCreate(Bundle savedInstanceState) {

  // assuming that you're using a DEBUG flag
  if (BuildConfig.DEBUG) {
    Liquid.initialize(this, "YOUR_DEVELOPMENT_APP_TOKEN", BuildConfig.DEBUG);
  } else {
    Liquid.initialize(this, "YOUR_PRODUCTION_APP_TOKEN");
  }
}
{% endhighlight %}

From this moment on, each time you want to call a Liquid method you can do:

{% highlight java %}
Liquid.getInstance();
{% endhighlight %}

{% include alert.md type='info' message="All interactions using Liquid SDK should be done using this shared instance of `Liquid` object (and not using `LQ*` models)." %}

<div class='alert alert-warning alert-simple'><span class='fa fa-exclamation-triangle'></span> If your application supports <strong>Android SDK < 14</strong> follow <a href='#android-14' data-toggle='collapse'>these instructions</a>.</div>

{% capture android_14 %}

#### Android SDK < 14

If your application supports **Android SDK < 14**, then you have to notify Liquid when your activity lifecycle changes. On the other hand, for Android SDK versions greater or equal than **14**, Liquid will automatically do that for you.

{% highlight java %}
@Override
public void onResume() {
  super.onResume();
  Liquid.getInstance().activityResumed(this);
}

@Override
public void onPause() {
  super.onPause();
  Liquid.getInstance().activityPaused(this);
}

@Override
public void onStop() {
  super.onStop();
  Liquid.getInstance().activityStopped(this);
}

@Override
public void onStart() {
  super.onStart();
  Liquid.getInstance().activityStarted(this);
}

@Override
public void onDestroy() {
  super.onDestroy();
  Liquid.getInstance().activityDestroyed(this);
}
{% endhighlight %}

{% endcapture %}

<div id='android-14' class='collapse'>{{ android_14 | markdownify }}</div>
