# Notifications In Android  
Notification is a message that you can display to the user outside your app’s UI. Android Notifications provide short and precise information about the action that happened in your app. The notification displays the icon, title, and some amount of the content text.
## Appearances on a device
Notifications could be of various formats and designs depending upon the developer such as an icon in the status bar, a more detailed entry in the notification drawer, as a badge on the app's icon.
1. Status Bar Notification - When you issue a notification, it first appears as an icon in the status bar. It appears in the same layout as the current time, battery percentage
2. Notification drawer Notification - It appears in the drop-down menu. Users can swipe down on the status bar to open the notification drawer, where they can view more details and take action with the notification.
3. Heads-Up Notification  - Beginning with Android 5.0, notifications can briefly appear in a floating window called a heads-up notification. It appears on the overlay screen, ex: Whatsapp notification, OTP messages
4. Lock-Screen Notification - It appears on the lock screen. Beginning with Android 5.0, notifications can appear on the lock screen.
5. App icon badge -  In supported launchers on devices running Android 8.0 (API level 26) and higher, app icons indicate new notifications with a colored "badge" (also known as a "notification dot") on the corresponding app launcher icon.  


<p float="left">
  <img src="https://github.com/saloni33/android_documentation/blob/main/image/app_badge_icon.png" width="350" height="200" hspace="30"/>
  <img src="https://github.com/saloni33/android_documentation/blob/main/image/status_bar.png" width="350" height="200" hspace="30"/>
</p>

<p float="left">
  <img src="https://github.com/saloni33/android_documentation/blob/main/image/lock_screen.png" width="350" height="620" hspace="30"/>
  <img src="https://github.com/saloni33/android_documentation/blob/main/image/notification_drawer_image.jpeg" width="350" heigth="600" hspace="30"/>
</p>

## Create a Notification
The design of notification is quite simple, it contains an icon, title, some brief about the message(optional), and click. An example of the same is shown below:
<p align="center">
  <img src="https://github.com/saloni33/android_documentation/blob/main/image/example_image.png" width="540" height="200">
</p>
1. Small Icon - This can be set using setSmallIcon(). <br/>
2. App Name - This is provided by the app itself. <br/>
3. Timestamp - This is provided by the system but you can override it with setWhen() or hide it with setShowWhen(false). <br/>
4. Large icon - This is optional (usually used only for contact photos; do not use it for your app icon) and set with setLargeIcon(). <br/>
5. Title - This is optional and set with setContentTitle(). <br/>
6. Text - This is optional and set with setContentText(). <br/>

## Using Notification Channels 
Notification Channels provide you with the ability to group the notifications that our application sends into manageable groups. Starting in Android 8.0 (API level 26), all notifications must be assigned to a channel or they will not appear. <br/><br/>
By managing different channels, users will be able to disable specific notifications (instead of disabling all notifications),  and users can control the visual and auditory options for each channel. <br/><br/>
One app can have multiple notification channels—a separate channel for each type of notification the app issues. An app can also create notification channels in response to choices made by users of your app.<br/><br/>
For example, have a look at the <b>Clock</b> app that is installed with Android (tap Settings > App Notifications > Notifications and select Clock from the list). 

## How to Create a Notification
Below are the steps which are required for creating a notification in android - 
1. Add the support Library <br/>
Many projects made with Android Studio already include the necessary dependencies to use NotificationCompat, if not you should add the following dependencies in build.gradle file:
```
val core_version = "1.6.0"
dependencies {
    implementation "androidx.core:core:$core_version"
}
```

2. Create a basic notification <br/>
A basic notification contains an icon, title, a short description. Below are some steps, from which you can learn how to create a simple notification that a user can click on.
<p align="left">
  <img src="https://github.com/saloni33/android_documentation/blob/main/image/basic_notification.jpeg" width="350" height="150">
</p>

- Set notification content <br/>
First of all, we need to set the notification content and channel using a NotificationCompat.Builder object. <br/>
A small icon can be set using setSmallIcon(), title by setContentTitle(), text of the notification by setContentText(), and notification priority by using setPriority(). <br/>
Example code for Java is - 

``` 
NotificationCompat.Builder builder = new NotificationCompat.Builder(this, CHANNEL_ID)
        .setSmallIcon(R.drawable.notification_icon)
        .setContentTitle(textTitle)
        .setContentText(textContent)
        .setPriority(NotificationCompat.PRIORITY_DEFAULT);
```
If you want a notification to be longer, you can use setStyle() for the same.

- Create a channel and set the importance <br/>
For the version Android 8.0 and higher, you need to register the notification channel of your app with the system by passing an instance of NotificationChannel to createNotificationChannel(). <br/>  To create a notification channel, you need to follow the following steps- 
Construct a NotificationChannel object which requires unique channel_id and channel_name strings. The Importance argument is an int that specifies the level of interruption by the notification. . It can be one of the following values: </br/>
