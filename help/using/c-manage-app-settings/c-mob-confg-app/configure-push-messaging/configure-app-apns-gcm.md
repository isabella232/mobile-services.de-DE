---
description: Sie können Ihre App so konfigurieren, dass sie den Apple Push Notification Service (APNS) oder Firebase Cloud Messaging (FCM) nutzt.
keywords: mobile
solution: Experience Cloud Services,Analytics
title: App für die Verwendung von APNS oder FCM konfigurieren
topic-fix: Metrics
uuid: fa411f2a-ba47-4499-bbe5-1aedef6b49ad
exl-id: 9064e1f3-f176-4699-b1e6-90f29e1af0d3
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 100%

---

# App für die Verwendung von APNS oder FCM konfigurieren {#configure-app-to-use-apns-or-fcm}

{#eol}

Sie können Ihre App so konfigurieren, dass sie den Apple Push Notification Service (APNS) oder Firebase Cloud Messaging (FCM) nutzt.

## Android-Apps {#section_41D304102CDF4586911EC1413AD35A10}

### Wenn FCM nicht in Ihrer App aktiviert ist:

Konfigurieren Ihrer Android-App für die Verwendung von FCM in diesem Szenario:

1. Öffnen Sie [https://firebase.google.com/](https://firebase.google.com/) und melden Sie sich mit Ihren Google Dev-Anmeldedaten an.

1. Klicken Sie auf **[!UICONTROL Get Started]** und wählen Sie **[!UICONTROL Add Project]** aus.

1. Geben Sie einen Projektnamen ein und klicken Sie auf das Kontrollkästchen, um die Controller-Controller-Bedingungen zu akzeptieren, wenn Sie Google Analytics für Firebase-Daten aktivieren.

1. Klicken Sie auf **[!UICONTROL Create project]** und warten Sie, bis das Projekt erstellt wurde.

1. Klicken Sie auf das erstellte Projekt und die Seite **[!UICONTROL Project Overview]** sollte für das erstellte Projekt angezeigt werden. Klicken Sie auf die Schaltfläche mit dem Android-Symbol, um dem Projekt eine Android-App hinzuzufügen.

1. Geben Sie bei Bedarf den App-Paketnamen, den App-Spitznamen und das Signaturzertifikat ein.

1. Befolgen Sie die vom Setup-Assistenten vorgeschlagenen zusätzlichen Schritte. Nachdem Sie die Firebase-Einrichtung durch Testen der Kommunikation mit den Firebase-Servern überprüft haben, kehren Sie zur Seite **[!UICONTROL Project Overview]** zurück.

1. Klicken Sie auf das Zahnradsymbol rechts neben der Schaltfläche **[!UICONTROL Project Overview]** und klicken Sie auf **[!UICONTROL Project Settings]**.

1. Klicken Sie auf die Registerkarte **[!UICONTROL Cloud Messaging]**.

1. Notieren Sie sich den **[!UICONTROL bestehenden Server-Schlüssel]** und die **[!UICONTROL Sender-ID]** zur späteren Verwendung.

   Beispiel:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### Wenn FCM in Ihrer App aktiviert ist:

Konfigurieren Ihrer Android-App für die Verwendung von FCM in diesem Szenario:

1. Öffnen Sie [https://firebase.google.com/](https://firebase.google.com/) und melden Sie sich mit Ihren Google Dev-Anmeldedaten an.

1. Klicken Sie auf **[!UICONTROL Get Started]**. Dadurch wird die Projektindexseite geöffnet. Suchen Sie das Projekt mit aktivierter Firebase-Funktion, das mit Ihrer Android-App verknüpft ist, und klicken Sie auf die Projektkarte.

1. Die **[!UICONTROL Project Overview]** für das Projekt sollte dann geladen werden. Klicken Sie auf das Zahnradsymbol rechts neben der Schaltfläche **[!UICONTROL Project Overview]** und klicken Sie auf **[!UICONTROL Project Settings]**.

1. Klicken Sie auf die Registerkarte **[!UICONTROL Cloud Messaging]**.

1. Notieren Sie sich den **[!UICONTROL bestehenden Server-Schlüssel]** und die **[!UICONTROL Sender-ID]** zur späteren Verwendung.

   Beispiel:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```



## iOS-Apps {#section_2031DAB485FC4D2B9027E42AD90B294D}

So konfigurieren Sie Ihre iOS-App für die Verwendung von APNS:

1. Gehen Sie zu [https://developer.apple.com/account](https://developer.apple.com/account) und melden Sie sich bei Ihrem [Apple Developer-Account](https://developer.apple.com/account) an.
1. Wählen Sie unter **[!UICONTROL iOS Apps]**, die Option **[!UICONTROL Identifiers]** aus.
1. Wenn Sie eine App-ID für Push eingerichtet haben, gehen Sie direkt zu Schritt 11.
1. Klicken Sie auf die **[!UICONTROL +]**-Schaltfläche, um eine neue App-ID zu erstellen.
1. Geben Sie eine App-ID-Beschreibung ein.
1. Geben Sie ein App-ID-Suffix ein.

   >[!IMPORTANT]
   >
   >Damit Push unterstützt wird, müssen Sie eine explizite App-ID verwenden, die **keinen** Platzhalter enthält (z. B. `- com.tester.pushSample`).

1. Aktivieren Sie unter **[!UICONTROL App Services]** das Kontrollkästchen **[!UICONTROL Push-Benachrichtigungen]**.
1. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Klicken Sie auf **[!UICONTROL Senden]**.
1. Klicken Sie auf **[!UICONTROL Fertig]**.
1. Wählen Sie Ihre App-ID zur Verwendung von Push-Benachrichtigungen aus der Liste aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Wenn Sie bereits ein Push-Zertifikat erstellt haben, gehen Sie direkt zu Schritt 15.
1. Scrollen Sie nach unten zu **[!UICONTROL Push-Benachrichtigungen]** und klicken Sie auf die Schaltfläche **[!UICONTROL Zertifikat erstellen…]**.

   Die Schaltfläche, auf die Sie klicken, hängt davon ab, ob Sie ein Zertifikat für die Entwicklung oder Produktion erstellen.
1. Befolgen Sie die Schritte zum Erstellen Ihrer CSR auf der Apple-Website, zum Hochladen der CSR und zum Generieren Ihres Zertifikats.
1. Scrollen Sie nach unten zum Bereich **[!UICONTROL Push-Benachrichtigungen]** und laden Sie das soeben erstellte SSL-Zertifikat herunter.
1. Doppelklicken Sie auf das heruntergeladene Zertifikat, um es dem Schlüsselbund hinzuzufügen.

### SSL-Zertifikate und private Schlüssel

Abrufen des SSL-Zertifikats und des privaten Schlüssels (APNS):

1. Öffnen Sie **[!UICONTROL Keychain Access]**.
1. Klicken Sie auf **[!UICONTROL Meine Zertifikate]** und suchen Sie das entsprechende **[!UICONTROL iOS Push Services-Zertifikat]** für Ihre App und Ihre Umgebung.

   Sie können das richtige Zertifikat identifizieren, indem Sie die Bundle-ID abgleichen und angeben, ob es sich um eine Entwicklungs- oder eine Produktionsdatei handelt.

1. Erweitern Sie das Zertifikat und vergewissern Sie sich, dass es einen privaten Schlüssel enthält.
1. Klicken Sie mit der rechten Maustaste auf den privaten Schlüssel und wählen Sie **[!UICONTROL Exportieren *`<name of key>`*]**aus.
1. Geben Sie die erforderlichen Informationen in das Dialogfenster ein und speichern Sie die neue `.p12`-Datei.

   Sie müssen kein Passwort eingeben.

1. Geben Sie unter **[!UICONTROL Privater Schlüssel]** die `.p12`-Datei ein.
