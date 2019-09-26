---
description: You can configure your app to use Apple Push Notification Service (APNS) or Firebase Cloud Messaging (FCM).
keywords: mobile
seo-description: You can configure your app to use Apple Push Notification Service (APNS) or Firebase Cloud Messaging (FCM).
seo-title: App für die Verwendung von APNS oder FCM konfigurieren
solution: Marketing Cloud, Analytics
title: Configure App to use APNS or FCM
topic: Metriken
uuid: fa411f2a-ba47-4499-bbe5-1aedef6b49ad
translation-type: tm+mt
source-git-commit: 608384f1fee2a05699ff13fbd51c3cc43aeb693c

---


# Configure your app to use APNS or FCM{#configure-app-to-use-apns-or-fcm}

You can configure your app to use Apple Push Notification Service (APNS) or Firebase Cloud Messaging (FCM).

## Android-Apps {#section_41D304102CDF4586911EC1413AD35A10}

### Wenn FCM in Ihrer App nicht aktiviert ist

To configure your Android app to use FCM in this scenario:

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. Click **[!UICONTROL Get Started]** and select **[!UICONTROL Add Project]**.

1. Geben Sie einen Projektnamen ein und klicken Sie bei der Anmeldung bei Google Analytics für Firebase-Daten auf das Kontrollkästchen, um die Bedingungen für den Controller-Controller zu akzeptieren.

1. Klicken Sie auf Projekt **[!UICONTROL erstellen]** und warten Sie, bis das Projekt erstellt wird.

1. Klicken Sie auf das erstellte Projekt und die Seite **[!UICONTROL Projektübersicht]** für das erstellte Projekt sollte angezeigt werden. Klicken Sie auf die Schaltfläche mit dem Android-Symbol, um dem Projekt eine Android-App hinzuzufügen.

1. Geben Sie bei Bedarf den App-Paketnamen, den App-Nicknamen und das Signaturzertifikat ein.

1. Befolgen Sie die vom Setup-Assistenten vorgeschlagenen zusätzlichen Schritte. Nachdem Sie die Firebase-Einrichtung durch Testen der Kommunikation mit den Firebase-Servern überprüft haben, kehren Sie zur Seite **[!UICONTROL Projektübersicht]** zurück.

1. Klicken Sie auf das Zahnradsymbol rechts neben der Schaltfläche **[!UICONTROL Projektübersicht]** und klicken Sie auf **[!UICONTROL Projekteinstellungen]**.

1. Klicken Sie auf die Registerkarte **[!UICONTROL Cloud Messaging]** .

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   Beispiel:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### If FCM is enabled in your app

So konfigurieren Sie Ihre Android-App für die Verwendung von FCM in diesem Szenario:

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. Klicken Sie auf **[!UICONTROL Erste Schritte]**. Dadurch wird die Projektindex-Seite geöffnet. Suchen Sie das Projekt mit aktivierter Firebase-Funktion, das mit Ihrer Android-App verknüpft ist, und klicken Sie auf die Projektkarte.

1. Die **[!UICONTROL Projektübersicht]** für das Projekt sollte dann geladen werden. Klicken Sie auf das Zahnradsymbol rechts neben der Schaltfläche **[!UICONTROL Projektübersicht]** und klicken Sie auf **[!UICONTROL Projekteinstellungen]**.

1. Klicken Sie auf die Registerkarte **[!UICONTROL Cloud Messaging]** .

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   Beispiel:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```



## iOS apps {#section_2031DAB485FC4D2B9027E42AD90B294D}

So konfigurieren Sie Ihre iOS-App für die Verwendung von APNS:

1. Öffnen Sie [https://developer.apple.com/account](https://developer.apple.com/account) und melden Sie sich bei Ihrem [Apple Developer-Konto](https://developer.apple.com/account) an.
1. Under **[!UICONTROL iOS Apps]**, select **[!UICONTROL Identifiers]**.
1. If you have an App ID set up for push, go to Step 11.
1. Press the **[!UICONTROL +]** button to create a new App ID.
1. Geben Sie im Feld „App ID Description“ eine Beschreibung für die App-ID ein.
1. Geben Sie im Feld „App ID Suffix“ ein Suffix für die App-ID ein.

   >[!IMPORTANT]
   >
   >To support push, you must use an Explicit App ID that does **not** use a wild card (for example, `- com.tester.pushSample`).

1. Aktivieren Sie unter **[!UICONTROL App Services]** das Kontrollkästchen **[!UICONTROL Push-Benachrichtigungen]**.
1. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Klicken Sie auf **[!UICONTROL Senden]**.
1. Klicken Sie auf **[!UICONTROL Fertig]**.
1. Wählen Sie Ihre App-ID zur Verwendung von Push-Benachrichtigungen aus der Liste aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Wenn Sie bereits ein Push-Zertifikat erstellt haben, gehen Sie direkt zu Schritt 15.
1. Scrollen Sie nach unten zu **[!UICONTROL Push-Benachrichtigungen]** und klicken Sie auf die Schaltfläche **[!UICONTROL Zertifikat erstellen…]**.

   Die Schaltfläche, auf die Sie klicken, hängt davon ab, ob Sie ein Zertifikat für Entwicklung oder Produktion erstellen.
1. Gehen Sie wie folgt vor, um Ihre CSR auf der Apple-Website zu erstellen, die CSR hochzuladen und Ihr Zertifikat zu generieren.
1. Scrollen Sie nach unten zum Bereich **[!UICONTROL Push-Benachrichtigungen]** und laden Sie das soeben erstellte SSL-Zertifikat herunter.
1. Doppelklicken Sie auf das heruntergeladene Zertifikat, um es Ihrem Schlüsselbund hinzuzufügen.

### SSL certificate and private keys

So rufen Sie Ihr SSL-Zertifikat und Ihren privaten Schlüssel (APNS) ab:

1. Öffnen Sie **[!UICONTROL Keychain Access]**.
1. Klicken Sie auf **[!UICONTROL Meine Zertifikate]** und suchen Sie das entsprechende **[!UICONTROL iOS Push Services-Zertifikat]** für Ihre App und Ihre Umgebung.

   Sie erkennen das richtige Zertifikat an der Paket-ID und daran, ob es sich in Entwicklung oder in Produktion befindet.

1. Erweitern Sie das Zertifikat und vergewissern Sie sich, dass es einen privaten Schlüssel enthält.
1. Right-click the private key and select **[!UICONTROL Export "*`<name of key>`*]**.
1. Geben Sie die erforderlichen Informationen in das Dialogfeld ein und speichern Sie die neue `.p12` Datei.

   Sie müssen kein Passwort eingeben.

1. In the **[!UICONTROL Private Key]**, type the `.p12` file.

