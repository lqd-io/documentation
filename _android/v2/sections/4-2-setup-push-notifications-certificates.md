
Liquid needs to authenticate with the Google Cloud Messaging service in order to send push notifications to your users. We have prepared a step-by-step guide to help you get a GCM key and set it up on your app settings, **but if you already have a GCM authentication key go directly to the last step.**

#### Set up your GCM auth key

* Go to <a href="https://console.developers.google.com" target="_blank">Google Developers Console</a> and create a project for your app if you haven't already.
<img src='{{ site.github.url }}/assets/android/push_notifications_certificate_step_1.png' alt='Setup your GCM key on your app settings view' data-action='zoom'/>

* Write your project's name and click create.
<img src='{{ site.github.url }}/assets/android/push_notifications_certificate_step_2.png' alt='Setup your GCM key on your app settings view' data-action='zoom'/>

* Then follow <a href="https://developers.google.com/mobile/add?platform=android&cntapi=gcm&cnturl=https:%2F%2Fdevelopers.google.com%2Fcloud-messaging%2Fandroid%2Fclient&cntlbl=Continue%20Adding%20GCM%20Support&%3Fconfigured%3Dtrue" target="_blank">this link</a> to enable Google Services for your app and get a configuration file for your project. Choose your app name from your Developer Console. Enter the package name of your application and **Continue**.
<img src='{{ site.github.url }}/assets/android/push_notifications_certificate_step_3.png' alt='Setup your GCM key on your app settings view' data-action='zoom'/>

* Select Cloud Messaging and enable it.
<img src='{{ site.github.url }}/assets/android/push_notifications_certificate_step_4.png' alt='Setup your GCM key on your app settings view' data-action='zoom'/>

* After enabling it you will get your **Server API Key** and **Sender ID**.
<img src='{{ site.github.url }}/assets/android/push_notifications_certificate_step_5.png' alt='Setup your GCM key on your app settings view' data-action='zoom'/>

* Continue to generate configuration file. Download google-service.json and copy it in the `app/` or `mobile/` module directory in your Android project or in your application's root folder.
<img src='{{ site.github.url }}/assets/android/push_notifications_certificate_step_6.png' alt='Setup your GCM key on your app settings view' data-action='zoom'/>

* Finally copy the **Server API Key** into the **Notification Settings** in your App Settings page in Liquid.
<img src='{{ site.github.url }}/assets/android/push_notifications_certificate_step_7.png' alt='Setup your GCM key on your app settings view' data-action='zoom'/>

Besides adding your **Server API Key** to our platform, you need to prepare your Android app to correctly parse Push Notifications sent by us. This is a technical step that involves changing the code on your app; if you haven't done so, follow the steps on the [Setup push notifications and in-app messages](#setup-push-notifications-and-in-app-messages) section.
