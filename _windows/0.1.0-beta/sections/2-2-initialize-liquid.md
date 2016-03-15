
{% include alert.md type='warning' message="For every app you add on Liquid, two versions of the app are created: a **production** and a **development** version. These versions have completely distinct environments (i.e., different users, devices, sessions, events, targets and dynamic variables) and each app version has **its own API key**." %}

You can initialize Liquid singleton (once per app launch) with your app API key. Typically, the best place to do this is on `protected async override void OnLaunched(LaunchActivatedEventArgs e)` method at your `App.xaml.cs` file.

{% include alert.md type='info' message="Note that you'll need to prepend `async` to the method signature, if you don't have it already." %}

You can find your App API key on the <span class='fa fa-cog'></span> **App Settings** of Liquid's dashboard.

{% highlight c# %}
// App.xaml.cs

protected async override void OnLaunched(LaunchActivatedEventArgs e)  {

  // assuming that you're using a DEBUG flag
  #if DEBUG
    await Liquid.Initialize("YOUR-DEVELOPMENT-APP-TOKEN", this, e, true);
  #else
    await Liquid.Initialize("YOUR-PRODUCTION-APP-TOKEN", this, e);
  #endif

  /* The rest of your code goes here... */ 
}
{% endhighlight %}

From this moment on, each time you want to call a Liquid method you can do:

{% highlight c# %}
Liquid.Instance;
{% endhighlight %}

{% include alert.md type='info' message="All interactions using Liquid SDK should be done using this shared instance of `Liquid` object (and not using `LQ*` models)." %}
