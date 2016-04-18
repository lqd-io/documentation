
To send Push Notifications as your app, Liquid must authenticate with Apple's Push Notification Service (APNS) using your app's certificate. If you have one already, the steps you must follow are easy:

* First, access your Mac's Keychain and extract both your app's certificate and private key. You should have each environment: production and development (sandbox):
<img src='{{ site.github.url }}/assets/ios/push_notifications_certificate_step_1.png' alt='Extract Certificate From Keychain' data-action='zoom'/>

* Extract it into the **Personal Information Exchange (.p12)** format and save it on your computer with any name you like. You can add a password but it is not required:
<img src='{{ site.github.url }}/assets/ios/push_notifications_certificate_step_2.png' alt='Save Certificate As .p12' data-action='zoom'/>

* Go to your app Settings page in Liquid. In the Notification Settings section you can upload the Certificate you just extracted. Do so for your production and development app;
<img src='{{ site.github.url }}/assets/ios/push_notifications_certificate_step_3.png' alt=' In the Notification Settings section you can upload the Certificate you just extracted' data-action='zoom'/>

That's it! You should now be able to send Push Notifications to your iOS users.
