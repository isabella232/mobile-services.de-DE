---
description: Adobe Mobile und das Adobe Mobile-SDK ermöglichen es Ihnen, Push-Nachrichten an Benutzer zu senden. Mit dem SDK können Sie darüber hinaus einfach Benutzer erfassen, die Ihre App nach dem Aufrufen einer Push-Nachricht geöffnet haben.
seo-description: Adobe Mobile und das Adobe Mobile-SDK ermöglichen es Ihnen, Push-Nachrichten an Benutzer zu senden. Mit dem SDK können Sie darüber hinaus einfach Benutzer erfassen, die Ihre App nach dem Aufrufen einer Push-Nachricht geöffnet haben.
seo-title: Push-Benachrichtigung
solution: Experience Cloud,Analytics
title: Push-Benachrichtigung
topic: Entwickler und Implementierung
uuid: 729d4010-3733-4dff-b188-ad45bd3e7cc4
translation-type: ht
source-git-commit: 17cb91a28966cf32f955a2cb724e89ab228de5b8

---


# Push-Nachrichten {#push-messaging}

Adobe Mobile und das Adobe Mobile-SDK ermöglichen es Ihnen, Push-Nachrichten an Benutzer zu senden. Mit dem SDK können Sie darüber hinaus einfach Benutzer erfassen, die Ihre App nach dem Aufrufen einer Push-Nachricht geöffnet haben.

Um In-App-Nachrichten zu nutzen, ist SDK-Version 4.6 (oder höher) **erforderlich**.

>[!IMPORTANT]
>
>Legen Sie die Experience Cloud ID nicht manuell in Ihrer App fest. Dies verursacht die Erstellung eines neuen Unique User, der aufgrund seines „opt-in“-Status keine Push-Nachrichten empfängt. Beispiel: Ein Benutzer, der dem Empfang von Push-Nachrichten zugestimmt hat (opt-in), meldet sich bei Ihrer App an. Nach dem Anmelden wird, sofern Sie die ID manuell in Ihrer App festgelegt haben, ein neuer Unique User erstellt, der dem Empfang von Push-Nachrichten nicht zugestimmt hat. Dementsprechend erhält dieser neue Benutzer keine Push-Nachrichten.
>
>Das Verschieben Ihrer App in eine neue Report Suite wird nicht unterstützt. Wenn Sie zu einer neuen Berichtssuite migrieren, kann Ihre Push-Konfiguration kaputt gehen und Nachrichten werden möglicherweise nicht gesendet.

## Push-Nachrichten aktivieren {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

>[!TIP]
>
>Wenn Ihre App bereits für Nachrichten über Firebase Cloud Messaging (FCM) eingerichtet ist, sind einige der folgenden Schritte möglicherweise bereits abgeschlossen.

1. Überprüfen Sie, ob die Datei `ADBMobileConfig.json` die erforderlichen Einstellungen für Push-Nachrichten enthält.

   Im Objekt `"marketingCloud"` muss die zugehörige Eigenschaft `"org"` für Push-Nachrichten konfiguriert sein.

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

1. Die Registrierungs-ID/Das Registrierungs-Token muss mithilfe der Methode `Config.setPushIdentifier(final String registrationId)` an das SDK übergeben werden.

   ```js
   Config.setPushIdentifier(token); // token was obtained in step 2
   ```

1. Aktivieren Sie das Reporting, indem Sie Ihre Aktivität in der Methode `collectLifecycleData` übergeben.

   Im Folgenden finden Sie die Anforderungen für die Aktivierung des Push-Clickthrough-Reportings:

   * In Ihrer `FireBaseMessageService`-Implementierung muss das Bundle-Objekt, das die Nachrichtendaten enthält, die mit dem Objekt „RemoteMessage“ an die Methode `onMessageReceived` übergeben werden, zum Intent hinzugefügt werden, der zum Öffnen der Zielaktivität eines Clickthroughs verwendet wird. Dies kann mithilfe der `putExtras`-Methode erfolgen. Weitere Informationen dazu finden Sie unter [putExtras](https://developer.android.com/reference/android/content/Intent.html#putExtras(android.os.Bundle)).
   ```java
   Intent intent = new Intent(this, MainActivity.class);
      intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
   // get the bundle from the RemoteMessage object
      intent.putExtras(message.toIntent().getExtras());
   ```

   * In der Zielaktivität des Clickthroughs muss die Aktivität mit dem Aufruf `collectLifecycleData` an das SDK übergeben werden.

      Beachten Sie die folgenden Informationen:

      * Verwenden Sie `Config.collectLifecycleData(this)` oder `Config.collectLifecycleData(this, contextData)`.

      * Verwenden Sie **nicht** `Config.collectLifecycleData()`.



