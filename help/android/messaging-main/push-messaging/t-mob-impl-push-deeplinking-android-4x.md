---
description: Nachdem Sie die Deep-Link-URL in der Adobe Mobile Services-Benutzeroberfläche konfiguriert haben, befindet sich diese URL in der Push-Payload mit dem Schlüssel „adb_deeplink“.
title: Push-Nachrichten mit Deep-Linking implementieren
uuid: e24f9248-8d48-4e57-84af-3a05b72e2a09
exl-id: ab97db32-d9d2-41ec-aae8-a951c7745df8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 74%

---

# Push-Nachrichten mit Deep-Links implementieren {#implement-push-messaging-with-deep-linking}

Nachdem Sie die Deep-Link-URL in der Adobe Mobile Services-Benutzeroberfläche konfiguriert haben, befindet sich diese URL in der Push-Payload mit dem Schlüssel „adb_deeplink“.

Sie können die URL abrufen, indem Sie `remoteMessage.getData().get("adb_deeplink")` in `FirebaseMessagingService` aufrufen.

>[!TIP]
>
>Sie können je nachdem, ob die Payload über eine Deep-Link-URL verfügt, verschiedene Intents definieren.

1. Führen Sie eine der folgenden Aufgaben aus:

   * Wenn sich die Deep-Link-URL in der Push-Payload **befindet**, erstellen Sie den Intent `ACTION_VIEW` mit der URL.

      Wenn der Benutzer auf die Push-Nachricht klickt, wird ein Deep-Link ausgelöst.

   * Wenn die Deep-Link-URL **nicht** in der Push-Payload ist, erstellen Sie einen Intent, der eine Ihrer Aktivitäten öffnet.

## Beispiel

Hier finden Sie eine Beispielimplementierung für die Klasse, die sich von `FirebaseMessagingService` erstreckt:

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
