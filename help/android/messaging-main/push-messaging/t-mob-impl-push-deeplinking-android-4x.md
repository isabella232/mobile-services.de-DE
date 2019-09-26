---
description: Nachdem Sie die Deep-Link-URL in der Adobe Mobile Services-Benutzeroberfläche konfiguriert haben, befindet sich diese URL in der Push-Payload mit dem Schlüssel „adb_deeplink“.
seo-description: Nachdem Sie die Deep-Link-URL in der Adobe Mobile Services-Benutzeroberfläche konfiguriert haben, befindet sich diese URL in der Push-Payload mit dem Schlüssel „adb_deeplink“.
seo-title: Push-Nachrichten mit Deep-Links implementieren
title: Push-Nachrichten mit Deep-Links implementieren
uuid: e24f9248-8d48-4e57-84af-3a05b72e2a09
translation-type: tm+mt
source-git-commit: 13ff2cb549c4b82a4e0285e1c7c6b3f9c1a5bd4b

---


# Implement push messaging with deep linking {#implement-push-messaging-with-deep-linking}

Nachdem Sie die Deep-Link-URL in der Adobe Mobile Services-Benutzeroberfläche konfiguriert haben, befindet sich diese URL in der Push-Payload mit dem Schlüssel „adb_deeplink“.

Sie können die URL abrufen, indem Sie `remoteMessage.getData().get("adb_deeplink")` in der `FirebaseMessagingService`.

>[!TIP]
>
>Je nachdem, ob die Nutzlast über eine Deep-Linking-URL verfügt, können Sie unterschiedliche Absichten definieren.

1. Führen Sie eine der folgenden Aufgaben aus:

   * Wenn sich die Deep-Link-URL in der Push-Payload **befindet**, erstellen Sie den Intent `ACTION_VIEW` mit der URL.

      Wenn der Benutzer auf die Push-Nachricht klickt, wird ein Deep-Link ausgelöst.

   * Wenn sich die Deep-Link-URL **nicht** in der Push-Payload befindet, erstellen Sie einen Intent, der eine Ihrer Aktivitäten öffnet.

## Beispiel

Here is a sample implementation for the class extending from `FirebaseMessagingService`:

```java
public void onMessageReceived(RemoteMessage message) { 
 
       Map<String, String> data = message.getData(); 
       String messageStr = data.get("message"); 
       String deepLink = data.get("adb_deeplink"); 
 
       sendNotification(deepLink, messageStr, data); 
    } 
 
private void sendNotification(String deeplink, String message, Map<String, String> data) { 
       Intent intent; 
 
       if (deeplink!=null) { 
           intent = new Intent(Intent.ACTION_VIEW, Uri.parse(deeplink)); 
       } else { 
           intent = new Intent(this, MainActivity.class); 
       } 
 
       intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP); 
 
       //put the data map into the intent to track clickthroughs 
       Bundle pushData = new Bundle(); 
       Set<String> keySet = data.keySet(); 
       for (String key : keySet) { 
           pushData.putString(key, data.get(key)); 
       } 
 
       intent.putExtras(pushData); 
 
       PendingIntent pendingIntent = PendingIntent.getActivity(this, 0, intent, 
               PendingIntent.FLAG_ONE_SHOT); 
 
       Uri defaultSoundUri= RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION); 
 
       NotificationCompat.Builder notificationBuilder = new NotificationCompat.Builder(this) 
                .setSmallIcon(R.drawable.icon) 
                .setContentTitle("FCM Deep Link Push") 
                .setContentText(message) 
                .setAutoCancel(true) 
                .setSound(defaultSoundUri) 
                .setContentIntent(pendingIntent); 
 
       NotificationManager notificationManager =  
       (NotificationManager)getApplicationContext().getSystemService(Context.NOTIFICATION_SERVICE); 
           notificationManager.notify(0, notificationBuilder.build()); 
       } 
```
