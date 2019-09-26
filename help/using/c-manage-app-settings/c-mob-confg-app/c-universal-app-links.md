---
description: Mit universellen Links (iOS) und App-Links (Android) können Sie eine Verbindung zu Deep Links in Ihren iOS- oder Android-Apps herstellen.
keywords: mobile
seo-description: Mit universellen Links (iOS) und App-Links (Android) können Sie eine Verbindung zu Deep Links in Ihren iOS- oder Android-Apps herstellen.
seo-title: Apple Universal Links und Android App Links
solution: Marketing Cloud, Analytics
title: Apple Universal Links und Android App Links
topic: Metriken
uuid: 8d6441dc-4307-4454-95ea-d77ec796f918
translation-type: tm+mt
source-git-commit: e65add089499f728827321e96e439f04ebb19a73

---


# Apple Universal Links und Android App Links{#universal-links-and-app-links}

Mit universellen Links (iOS) und App-Links (Android) können Sie eine Verbindung zu Deep Links in Ihren iOS- oder Android-Apps herstellen.

>[!IMPORTANT]
>
>Ab iOS 9.2 wird Deep-Linking nicht mehr unterstützt. Sie müssen universelle Apple-Links für Deep-Linking zu Ihrer App oder Website verwenden.

## Universelle Links {#section_F8147944679A42E59CF4FD8814E5EF12}

Universelle Links ermöglichen Ihnen, eine Verbindung zu Deep Links in Ihrer iOS-App herzustellen. Sie werden in iOS 9.2 oder höher unterstützt. Beim Zugriff auf einen universellen Link leitet iOS den Link direkt an den Deep Link in Ihrer App weiter. If your app is not installed, it opens a URL for your website in a browser instead. For more information about Universal Links, see [Support Universal Links](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html).

## App-Links

App Links allow you to connect to deep links in your Android app and is supported in Android 6.0 or later. When an App Link is accessed, Android redirects the link directly to the deeplink in your app. If your app is not installed, it opens a URL for your website in a browser instead. For more information about App Links, see the [Handling Android App Links](https://developer.android.com/training/app-links/index.html).

## Create a Marketing Link by using a Universal or App Link {#section_609ADEFFB9B441C4A8C45E936D0DC859}

You can create a Marketing Link that uses a Universal or App Link.

### Configure a Universal Link

1. To set up Universal Links in your iOS app, go to Handling Universal Links in Apple.[](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links)

2. In Adobe Mobile Services, set up the site-association documents:

   a. Wählen Sie auf der Startseite der Mobile Services die App aus, für die Sie universelle Links einrichten möchten.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Ensure the iOS app that handles the Universal Links is added to the Add App Store Apps section.****

   >[!TIP]
   >
   >If the Add App Store Apps section does not display, click the Add App Store App link.********

   d. In the Universal Links and App Links Options section, select an iOS app and type the App ID.****

   f.Klicken Sie auf **[!UICONTROL Speichern]**.

   You must provide at least one iOS app selection and one App ID, or you will receive an error.

   >[!IMPORTANT]
   >
   >Sie können die Dokumente aktualisieren, indem Sie auf Aktualisieren im Abschnitt Optionen für universelle Links und Anwendungslinks klicken. However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### Verwenden eines universellen Links

1. Erstellen Sie in Adobe Mobile Services einen Marketing-Link, der universelle Links verwendet:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Klicken Sie auf Neu **[!UICONTROL erstellen]**.

   c. Under **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Use Universal Links or App Links]**.

   d. Wenn Sie die Siteverknüpfungsdokumente im Abschnitt *Einrichten von Siteverknüpfungsdokumenten in Adobe Mobile Services* konfiguriert haben, ist diese Option standardmäßig aktiviert.

   Wenn Sie die Dokumente nicht konfiguriert haben, ist die Option "Universelle Links **[!UICONTROL verwenden"oder "App-Links]** "deaktiviert und "Zwischenräume **[!UICONTROL verwenden]** "ist standardmäßig aktiviert.

   e. Wenn die Option "Universelle Links **[!UICONTROL verwenden"oder "App-Links]** "aktiviert ist, wird das Feld " **[!UICONTROL Benutzerspezifischer Pfad]** "angezeigt.

   Hierüber können Benutzer den URL-Pfad nach der Domäne sowie beliebige Abfrageparameter definieren. Wenn Sie beispielsweise wird `my/universal/link?os=9.2`die vollständige URL Ihres Marketing-Links `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`angezeigt.

   f. Klicken Sie auf die Registerkarte **[!UICONTROL Entscheidungen]** und konfigurieren Sie Ihre Entscheidungsstruktur.

   h. Wenn die iOS-App installiert ist, verarbeitet die App den Deeplink mit ihrer Logik. Das endgültige Ziel dient nur als Ausweichmöglichkeit, wenn die App nicht installiert ist. Da die App nicht installiert ist, kann das endgültige Ziel nur ein Weblink oder ein App Store sein.

   i.Klicken Sie auf **[!UICONTROL Speichern]**.

>[!TIP]
>
>Sobald ein Marketing-Link gespeichert wurde, können die Optionen für Marketing-Links nicht mehr geändert werden. This is because you do not want to change the behavior of the Marketing Links that may have already been distributed.


### App-Link konfigurieren

1. Um App-Links in Ihrer Android-App einzurichten, gehen Sie zu "Android-App-Links [hinzufügen"](https://developer.android.com/studio/write/app-link-indexing).

1. Richten Sie in Adobe Mobile Services die Siteverknüpfungsdokumente ein:

   a. Wählen Sie auf der Startseite der Mobile Services die App aus, für die Sie App-Links einrichten möchten.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Stellen Sie sicher, dass die Android-App, die universelle Links oder App-Links verarbeitet, zum Abschnitt App Store-Apps **[!UICONTROL hinzufügen hinzugefügt wird]** .

   >[!TIP]
   >
   >If this section does not display, click the **[!UICONTROL Add App Store App]** link.

   d. Blättern Sie zum Abschnitt Optionen für **[!UICONTROL universelle Links und App-Links]** .

   e. Klicken Sie auf die Registerkarte **[!UICONTROL App-Links (Android)]** .

   f. Select an Android app and type a SHA-256 certificate fingerprint.

   g.Klicken Sie auf **[!UICONTROL Speichern]**.

   Sie müssen mindestens eine Android-App-Auswahl und ein SHA-256-Zertifikat angeben, andernfalls wird ein Fehler ausgegeben.

   >[!IMPORTANT]
   >
   >Sie können die Dokumente aktualisieren, indem Sie auf **[!UICONTROL Aktualisieren]** im Abschnitt **Optionen für universelle Links und Anwendungslinks]klicken.[!UICONTROL ** However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### App-Link verwenden

1. Erstellen Sie in Adobe Mobile Services einen Marketing-Link, der App-Links verwendet:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Klicken Sie auf Neu **[!UICONTROL erstellen]**.

   c. Wählen Sie im Abschnitt **[!UICONTROL Optionen]** für Marketing-Links die Option Universelle Links oder App-Links **[!UICONTROL verwenden]**.

   d. Wenn Sie die Siteverknüpfungsdokumente aus Schritt 2 konfiguriert haben, ist diese Option standardmäßig aktiviert.

   If not, the **[!UICONTROL Use Universal Links or App Links]** option is disabled, and **[!UICONTROL Use Interstitials]** is selected by default.

   e. Wenn "Universelle Links **[!UICONTROL verwenden"oder "App-Links]** "aktiviert ist, wird das Feld " **[!UICONTROL Benutzerspezifischer Pfad]** "angezeigt.

   Hierüber können Benutzer den URL-Pfad nach der Domäne sowie beliebige Abfrageparameter definieren. Wenn Sie beispielsweise wird `my/app/link?os=6.0`die vollständige URL Ihres Marketing-Links `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`angezeigt.

   f. Klicken Sie auf die Registerkarte **[!UICONTROL Entscheidungen]** und konfigurieren Sie Ihre Entscheidungsstruktur.

   g. Wenn die Android-App installiert ist, verarbeitet die App den Deeplink mit ihrer Logik.

   Das endgültige Ziel dient nur als Fallback, wenn die App nicht installiert ist. Da die App nicht installiert ist, kann das endgültige Ziel nur ein Weblink oder ein App Store sein.

   h.  Click Save.****

>[!TIP]
>
>After a Marketing Link is saved, the **[!UICONTROL Marketing Links Options]** cannot be altered. Dies liegt daran, dass Sie das Verhalten der Marketing-Links, die möglicherweise bereits verteilt wurden, nicht ändern möchten.

## Using Marketing Links

You can now use these Marketing Links in messaging and other areas in your app.

>[!IMPORTANT]
>
>You will not see click tracking counts with Universal Links or App Links, and you can also not use interstitials.

