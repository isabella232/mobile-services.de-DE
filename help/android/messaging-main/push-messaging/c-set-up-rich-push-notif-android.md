---
description: Sie können Grafikdateien an Ihre Android-Benachrichtigungen anhängen. Die visuelle Komponente kann das Benutzerinteresse an Push-Benachrichtigungen deutlich erhöhen.
seo-description: Sie können Grafikdateien an Ihre Android-Benachrichtigungen anhängen. Die visuelle Komponente kann das Benutzerinteresse an Push-Benachrichtigungen deutlich erhöhen.
seo-title: Multimediale Push-Benachrichtigungen empfangen
title: Multimediale Push-Benachrichtigungen empfangen
uuid: 4a0340a6-666b-49b6-907a-9afc966dfdba
translation-type: tm+mt
source-git-commit: dca3663986b3ecc6e9fb736cc99513279715225c

---


# Receive rich push notifications {#receive-rich-push-notifications}

Sie können Grafikdateien an Ihre Android-Benachrichtigungen anhängen. Die visuelle Komponente kann das Benutzerinteresse an Push-Benachrichtigungen deutlich erhöhen.

## Handle the incoming rich push message (FCM) {#section_AF1A3BC2312C4E1DA517CC90296C11E2}

Wenn die App im Vordergrund ausgeführt wird, wird die Push-Nachricht von der App verarbeitet, die die Klasse `FirebaseMessagingService` erweitert, und auf folgende Weise in der Manifestdatei deklariert:

```java
<service
    android:name=".MyFirebaseMessagingService"
    android:exported="false">
    <intent-filter>
        <action android:name="com.google.firebase.MESSAGING_EVENT" />
    </intent-filter>
</service>
```

>[!IMPORTANT]
>
>The class that contains the  implementation handles the data that is received.`onMessageReceived()`

If the push message contains a Media URL, the URL will be available in the `RemoteMessage` parameter that is passed to the `onMessageReceived()` function. Verwenden Sie den Schlüssel `attachment-url`, wie im folgenden Codebeispiel veranschaulicht:

```java
public class MyFirebaseMessagingService extends FirebaseMessagingService {
        @Override
        public void onMessageReceived(RemoteMessage remoteMessage) {
      Log.d("Remote Message", "RemoteMessage: " + remoteMessage.toString());
            // Check if message contains a data payload.
            if (remoteMessage.getData().size() > 0) {
                Log.d("Remote Message", "RemoteMessage: " + remoteMessage.getData());
                sendNotification(remoteMessage);
            }
    }
 
private void sendNotification(RemoteMessage message) {
        Intent intent = new Intent(this, MainActivity.class);
    intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
    PendingIntent pendingIntent = PendingIntent.getActivity(this, 0 /* Request code */, intent, PendingIntent.FLAG_ONE_SHOT);

     String channelId = getString(R.string.default_notification_channel_id);
     Uri defaultSoundUri = RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION);
     NotificationCompat.Builder notificationBuilder =
                new NotificationCompat.Builder(this, channelId)
                        .setSmallIcon(R.drawable.ic_stat_ic_notification)
                        .setContentTitle(getString(R.string.fcm_message))
                        .setContentText(message.getData().get("body"))
                        .setAutoCancel(true)
                        .setSound(defaultSoundUri)
                        .setContentIntent(pendingIntent);
  
    //Handle image url if present in the push message 
        String attachmentUrl = message.getData().get("attachment-url");
  
    if (attachmentUrl != null) { 
    Bitmap image = getBitmapFromURL(attachmentUrl); 
    if (image != null) { 
      notificationBuilder.setStyle(new        NotificationCompat.BigPictureStyle().bigPicture(image)); 
        } 
        } 

     NotificationManager notificationManager =
              (NotificationManager) getSystemService(Context.NOTIFICATION_SERVICE);

     // Since android Oreo notification channel is needed.
     if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
        NotificationChannel channel = new NotificationChannel(channelId,
                    "Channel human readable title",
                    NotificationManager.IMPORTANCE_DEFAULT);
            notificationManager.createNotificationChannel(channel);
     }

     notificationManager.notify(0 /* ID of notification */, notificationBuilder.build());
    }
}
```

>[!IMPORTANT]
>
>When you set `NotificationCompat.BigPictureStyle`, large images might not be displayed. Um sicherzustellen, dass große Bilder immer angezeigt werden, legen Sie den nativen `Notification.BigPictureStyle` fest.

## Sample rich push notification {#section_6819316BEDDE45108413B541CA2BB2DC}

Im Folgenden finden Sie ein Beispiel einer multimedialen Push-Benachrichtigung mit einem Bild:

![](assets/rich-push-notification_example.png)

Weitere Informationen zu multimedialen Push-Benachrichtigungen unter Android finden Sie unter [Interaktion dank multimedialer Benachrichtigungen](https://developer.android.com/distribute/best-practices/engage/rich-notifications.html).
