
<h4 id='install-via-xcode'>Install via Xcode <a href="https://github.com/lqd-io/documentation/edit/gh-pages/_{{ page.collection }}/{{ page.version | downcase }}/sections/1-xcode.md" target="new" class="btn btn-xs btn-default btn-edit"><span class="fa fa-pencil"></span> Edit</a></h4>

* Download/clone the latest version of Liquid SDK from <a href="https://github.com/lqd-io/liquid-sdk-ios" target="_blank">https://github.com/lqd-io/liquid-sdk-ios <sup class="fa fa-external-link small"></sup></a> in your project folder.

* Drag `Liquid.xcodeproj` to your Xcode project **inside your project** blue icon.
<img src='{{ site.github.url }}/assets/ios/xcode_screen_1.jpg' alt='Drag Liquid.xcodeproj to your Xcode project' data-action='zoom'/>

* Open your project settings, select the tab **Build Phases**.
<img src='{{ site.github.url }}/assets/ios/xcode_screen_2.jpg' alt='Open your project settings, select the tab Build Phases' data-action='zoom'/>

* Open **Target Dependencies**, click "+" and select `Liquid`.

* Open **Link Binary With Libraries**, click "+" and select `libLiquid.a`.

* In your project settings, select the tab **Build Settings**.
<img src='{{ site.github.url }}/assets/ios/xcode_screen_3.jpg' alt='In your project settings, select the tab Build Settings' data-action='zoom'/>

* Search for **User Header Search Paths** and add `$(SRCROOT)/liquid-sdk-ios/Liquid` (recursive). If you store Liquid SDK into another path, you should adapt that path to your situation.

* Search for **Other Linker Flags** and add `$(inherited) -ObjC -all_load`.
