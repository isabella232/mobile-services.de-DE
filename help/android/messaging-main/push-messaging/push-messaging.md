---
description: Adobe Mobile und das Adobe Mobile SDK ermöglichen es Ihnen, Push-Nachrichten an Ihre Benutzer zu senden. Mit dem SDK können Sie darüber hinaus auf einfache Weise Benutzer erfassen, die Ihre App geöffnet haben, nachdem sie sich durch eine Push-Nachricht geklickt haben.
seo-description: Adobe Mobile und das Adobe Mobile SDK ermöglichen es Ihnen, Push-Nachrichten an Ihre Benutzer zu senden. Mit dem SDK können Sie darüber hinaus auf einfache Weise Benutzer erfassen, die Ihre App geöffnet haben, nachdem sie sich durch eine Push-Nachricht geklickt haben.
seo-title: Push-Nachrichten
solution: Experience Cloud,Analytics
title: Push-Nachrichten
topic: Developer and implementation
uuid: 729d4010-3733-4dff-b188-ad45bd3e7cc4
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 100%

---


# Push-Nachrichten {#push-messaging}

Adobe Mobile und das Adobe Mobile SDK ermöglichen es Ihnen, Push-Nachrichten an Ihre Benutzer zu senden. Mit dem SDK können Sie darüber hinaus auf einfache Weise Benutzer erfassen, die Ihre App geöffnet haben, nachdem sie sich durch eine Push-Nachricht geklickt haben.

Um In-App-Nachrichten zu nutzen, ist SDK-Version 4.6 (oder höher) **erforderlich**.

>[!IMPORTANT]
>
>Legen Sie die Experience Cloud ID nicht manuell in Ihrer App fest. Dies führt zur Erstellung eines neuen Unique Users, der aufgrund seines Opt-in-Status keine Push-Nachrichten erhält. Angenommen, ein Benutzer, der sich für den Empfang von Push-Nachrichten angemeldet hat, meldet sich bei Ihrer App an. Wenn Sie nach der Anmeldung die ID manuell in Ihrer App festlegen, wird ein neuer Unique User erstellt, der sich nicht für den Empfang von Push-Nachrichten entschieden hat. Dementsprechend erhält dieser neue Benutzer keine Push-Nachrichten.
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



