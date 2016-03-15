
#### Install as a Project Reference (DLL)

To install the Liquid SDK adding the libraries as references, you will need to download them from the Liquid website and add the library for a Windows Phone or Windows Store project in each of the specific projects as a reference.

+ Download/clone the SDK from <a href="https://github.com/lqd-io/liquid-sdk-windows" target="_blank">https://github.com/lqd-io/liquid-sdk-windows <sup class="fa fa-external-link small"></sup></a>.

+ Open your project properties (make sure you select **\<path to repository>/liquid-sdk-windows/Liquid/src/main**):
<img src='{{ site.github.url }}/assets/windows/visual_studio_screen_1.png' data-action='zoom'/>

+ Go to the **References** pane and click **Add**.
<img src='{{ site.github.url }}/assets/windows/visual_studio_screen_2.png' data-action='zoom'/>

+ Once the Reference Manager windows is open, go to the **Browse** pane and click **Browse**.
<img src='{{ site.github.url }}/assets/windows/visual_studio_screen_3.png' data-action='zoom'/>

+ Search for the Liquid SDK **DLL files** in your file system and add `Newtonsoft.Json.dll` and `LiquidWindowsPhoneSDK.dll` (or `LiquidWindowsStoreSDK.dll`, depending on your situation).
<img src='{{ site.github.url }}/assets/windows/visual_studio_screen_4.png' data-action='zoom'/>

+ Once you have both files added, click **Ok** and you're ready to go.
