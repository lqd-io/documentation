
The first step is to add the `internetClientServer` capability to your `manifest` file.

#### Windows Phone or Store Manifest

* If you are on a **Windows Phone project**, open the visual editor of the Application Manifest, and check *Internet (Client & Server)* under *Capabilities*. <img src='{{ site.github.url }}/assets/windows/app_manifest_wphone.png' data-action='zoom'/>

* If you are on a **Windows Store project**, open the visual editor of the *Application Manifest*, and check *Internet (Client)* under *Capabilities*.
<img src='{{ site.github.url }}/assets/windows/app_manifest_wstore.png' data-action='zoom'/>

* Or in the Code Editor, just before the end of the `Package.appxmanifest` file, add the highlighted line:

{% highlight xml %}
<Package>
  <!-- ... -->  
  <Capabilities> 
    <Capability Name="internetClientServer" /> 
  </Capabilities>
</Package>
{% endhighlight %}
