---
description: Adobe Mobile und das Adobe Mobile-SDK ermöglichen es Ihnen, Push-Nachrichten an Benutzer zu senden. Mit dem SDK können Sie darüber hinaus einfach Benutzer erfassen, die Ihre App nach dem Aufrufen einer Push-Nachricht geöffnet haben.
seo-description: Adobe Mobile und das Adobe Mobile-SDK ermöglichen es Ihnen, Push-Nachrichten an Benutzer zu senden. Mit dem SDK können Sie darüber hinaus einfach Benutzer erfassen, die Ihre App nach dem Aufrufen einer Push-Nachricht geöffnet haben.
seo-title: Push-Benachrichtigung
solution: Marketing Cloud, Analytics
title: Push-Benachrichtigung
topic: Entwickler und Implementierung
uuid: 729 d 4010-3733-4 dff-b 188-ad 45 bd 3 e 7 cc 4
translation-type: tm+mt
source-git-commit: 17cb91a28966cf32f955a2cb724e89ab228de5b8

---


# Push messaging {#push-messaging}

Adobe Mobile und das Adobe Mobile-SDK ermöglichen es Ihnen, Push-Nachrichten an Benutzer zu senden. Mit dem SDK können Sie darüber hinaus einfach Benutzer erfassen, die Ihre App nach dem Aufrufen einer Push-Nachricht geöffnet haben.

Um In-App-Nachrichten zu nutzen, ist SDK-Version 4.6 (oder höher) **erforderlich**.

>[!IMPORTANT]
>
>Legen Sie die Experience Cloud ID nicht manuell in Ihrer App fest. Dies verursacht die Erstellung eines neuen Unique User, der aufgrund seines „opt-in“-Status keine Push-Nachrichten empfängt. Beispiel: Ein Benutzer, der dem Empfang von Push-Nachrichten zugestimmt hat (opt-in), meldet sich bei Ihrer App an. Nach dem Anmelden wird, sofern Sie die ID manuell in Ihrer App festgelegt haben, ein neuer Unique User erstellt, der dem Empfang von Push-Nachrichten nicht zugestimmt hat. Dementsprechend erhält dieser neue Benutzer keine Push-Nachrichten.
>
>Das Verschieben Ihrer App in eine neue Report Suite wird nicht unterstützt. Wenn Sie zu einer neuen Berichtssuite migrieren, kann Ihre Push-Konfiguration kaputt gehen und Nachrichten werden möglicherweise nicht gesendet.

## Enable push messaging {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

>[!TIP]
>
>Wenn Ihre App bereits für die Verwendung von Messaging über Firebase Cloud Messaging (FCM) eingerichtet ist, sind einige der folgenden Schritte möglicherweise bereits abgeschlossen.

1. Verify that the `ADBMobileConfig.json` file contains the required settings for push messaging.

   The `"marketingCloud"` object must have its `"org"` property configured for push messaging.

   ```js
   "marketingCloud": { 
     "org": <org-id-string> 
    }
   ```

1. Rufen Sie die Registrierungs-ID/das Token mithilfe der Firebase Cloud Messaging-API (FCM) ab.

   * Weitere Informationen zur Einrichtung von FCM finden Sie unter [Firebase Cloud Messaging-Client-App unter Android einrichten](https://firebase.google.com/docs/cloud-messaging/android/client).

   ```js
   String token = FirebaseInstanceId.getInstance().getToken();
   ```

1. The registration ID/token must be passed to the SDK by using the `Config.setPushIdentifier(final String registrationId)` method.

   ```js
   Config.setPushIdentifier(token); // token was obtained in step 2
   ```

1. Aktivieren Sie das Reporting, indem Sie Ihre Aktivität in der Methode `collectLifecycleData` übergeben.

   Im Folgenden finden Sie die Anforderungen für die Aktivierung des Push-Clickthrough-Reportings:

   * In your implementation of `FireBaseMessageService`, the Bundle object that contains the message data, which is passed into the `onMessageReceived` method with the RemoteMessage object, must be added to the Intent that is used to open the target activity on a click-through. Dies kann mithilfe der `putExtras` Methode erfolgen. For more information, see [putExtras](https://developer.android.com/reference/android/content/Intent.html#putExtras(android.os.Bundle))).

   ```java
   Intent intent = new Intent(this, MainActivity.class);
      intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
   // get the bundle from the RemoteMessage object
      intent.putExtras(message.toIntent().getExtras());
   ```

   * In der Zielaktivität des Clickthroughs muss die Aktivität mit dem Aufruf `collectLifecycleData` an das SDK übergeben werden.

      Beachten Sie die folgenden Informationen:

      * Verwenden `Config.collectLifecycleData(this)` oder `Config.collectLifecycleData(this, contextData)`.

      * ****`Config.collectLifecycleData()`Verwenden Sie nicht.



