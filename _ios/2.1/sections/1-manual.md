
#### Manual install

* Download/clone the latest version of Liquid SDK from <a href="https://github.com/lqd-io/liquid-sdk-ios" target="_blank">https://github.com/lqd-io/liquid-sdk-ios <sup class="fa fa-external-link small"></sup></a> in your project folder.

* Drag **Liquid** folder to your Xcode project.
<img src='{{ site.github.url }}/assets/ios/manual_screen_1.jpg' alt='Drag Liquid folder to your Xcode project' data-action='zoom'/>

* Select **Copy items into destination Group's folder** and choose **Create groups for any added folders**.
<img src='{{ site.github.url }}/assets/ios/manual_screen_2.jpg' alt='Create groups for any added folders' data-action='zoom'/>

* **(Only for watchOS)** After this step, you should remove both XIBs from your watchOS targets. To do that, open **Build Phases** tab, then remove all `.xib` files starting by `LQ*` in **Copy Bundle Resources** section.
