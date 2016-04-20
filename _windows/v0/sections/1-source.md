
<h4 id='install-using-the-source-code'>Install using the Source Code <a href="https://github.com/lqd-io/documentation/edit/gh-pages/_{{ page.collection }}/{{ page.version | downcase }}/sections/1-source.md" target="new" class="btn btn-xs btn-default btn-edit"><span class="fa fa-pencil"></span> Edit</a></h4>

To install the Liquid SDK adding the libraries as references, you will need to download them from the Liquid website and add the library for a Windows Phone or Windows Store project in each of the specific projects.

+ Download/clone the SDK from <a href="https://github.com/lqd-io/liquid-sdk-windows" target="_blank">https://github.com/lqd-io/liquid-sdk-windows <i class="fa fa-external-link"></i></a>.

+ Right-click your project Solution, follow **Add...** and select **Existing Project...**
<img src='{{ site.github.url }}/assets/windows/source_screen_1.png' data-action='zoom'/>

+ Search for the Liquid SDK **Project** in your file system and add `LiquidWindowsPhoneSDK.csproj` (or `LiquidWindowsStoreSDK.csproj`, depending on your situation).
<img src='{{ site.github.url }}/assets/windows/source_screen_2.png' data-action='zoom'/>
