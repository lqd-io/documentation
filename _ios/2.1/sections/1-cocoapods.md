
<h4 id='install-via-cocoapods'>Install via CocoaPods <a href="https://github.com/lqd-io/documentation/edit/gh-pages/_{{ page.collection }}/{{ page.version | downcase }}/sections/1-cocoapods.md" target="new" class="btn btn-xs btn-default btn-edit"><span class="fa fa-pencil"></span> Edit</a></h4>

* Install <a href='http://cocoapods.org/' target='_blank'>CocoaPods <sup class='fa fa-external-link small'></sup></a> in your system.
* Open your **Xcode** project folder and create a file called `Podfile` with the following content: `pod 'Liquid'`.
* Run `pod install` and wait for **CocoaPod** to install Liquid SDK. From this moment on, instead of using `.xcodeproj` file, you should use `.xcworkspace`.

##### For the watchOS only:

To install Liquid on a **watchOS** project, you should follow the same steps as for iOS, but also explicitly define the platform for each of your targets, in your `Podfile`, like shown below:

{% highlight ruby %}
target 'ExampleApp' do
  platform :ios, '5.0'
  pod 'Liquid'
end

target 'ExampleApp WatchKit Extension' do
  platform :watchos, '2.0'
  pod 'Liquid'
end

target 'ExampleApp WatchKit App' do
  platform :watchos, '2.0'
  pod 'Liquid'
end
{% endhighlight %}
