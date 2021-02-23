---
description: Die Verknüpfung innerhalb von Apps und Websites ist wichtig, um die Benutzerfreundlichkeit zu erhalten. Erfahren Sie, wie universelle und App-Links funktionieren und Unterschiede bestehen.
seo-description: Mit universellen Links (iOS) und App-Links (Android) können Sie eine Verbindung zu Deep-Links in Ihren iOS- oder Android-Apps herstellen.
seo-title: Universelle Links (Apple) und App-Links (Android)
solution: Experience Cloud,Analytics
title: Handbuch zu universellen Links und App-Links
topic: Metriken
uuid: 8d6441dc-4307-4454-95ea-d77ec796f918
translation-type: tm+mt
source-git-commit: bb41caaecaefe8168d9b19e151d43ec792e24db8
workflow-type: tm+mt
source-wordcount: '1146'
ht-degree: 96%

---


# Universelle Links im Vergleich zu App-Links: Wie funktionieren sie? {#universal-links-and-app-links}

Mit universellen Links (iOS) und App-Links (Android) können Sie eine Verbindung zu Deep-Links in Ihren iOS- oder Android-Apps herstellen.

>[!IMPORTANT]
>
>Ab iOS 9.2 werden Deep-Links nicht mehr unterstützt. Sie müssen universelle Links von Apple verwenden, um Deep-Links zu Ihrer App oder Website herzustellen.

## Universelle Links {#section_F8147944679A42E59CF4FD8814E5EF12}

Universelle Links ermöglichen Ihnen, eine Verbindung zu Deep-Links in Ihrer iOS-App herzustellen. Sie werden in iOS 9.2 oder höher unterstützt. Beim Zugriff auf einen universellen Link leitet iOS den Link direkt an den Deep-Link in Ihrer App weiter. Wenn Ihre App nicht installiert ist, wird stattdessen eine URL für Ihre Website in einem Browser geöffnet. Weitere Informationen zu universellen Links finden Sie in [Universelle Links unterstützen](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html).

## App-Links

App-Links ermöglichen Ihnen, eine Verbindung zu Deep-Links in Ihrer Android-App herzustellen. Sie werden in Android 6.0 oder höher unterstützt. Beim Zugriff auf einen App-Link leitet Android den Link direkt an den Deep-Link in Ihrer App weiter. Wenn Ihre App nicht installiert ist, wird stattdessen eine URL für Ihre Website in einem Browser geöffnet. Weitere Informationen zu App-Links finden Sie in [Umgang mit Android-App-Links](https://developer.android.com/training/app-links/index.html).

## Marketinglinks mithilfe eines universellen oder App-Links erstellen {#section_609ADEFFB9B441C4A8C45E936D0DC859}

Sie können einen Marketinglink erstellen, der einen universellen Link oder einen App-Link verwendet.

### Universelle Links konfigurieren

1. Um universelle Links in Ihrer iOS-App einzurichten, gehen Sie zu [Verarbeiten universeller Links in Apple](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links).

2. Richten Sie die Standortverknüpfungsdokumente in Adobe Mobile Services ein:

   a. Wählen Sie auf der Mobile Services-Startseite die App aus, für die Sie universelle Links einrichten möchten.

   b. Klicken Sie auf **[!UICONTROL App-Einstellungen verwalten]**.

   c. Stellen Sie sicher, dass die iOS-App, die die universellen Links verarbeitet, zum Abschnitt **[!UICONTROL Appstore-Apps hinzufügen]** hinzugefügt wurde.

   >[!TIP]
   >
   >Wenn der Abschnitt **[!UICONTROL Appstore-Apps hinzufügen]** nicht angezeigt wird, klicken Sie auf den Link **[!UICONTROL Appstore-App hinzufügen]**.

   d. Wählen Sie im Abschnitt **[!UICONTROL Optionen für universelle Links und App-Links]** eine iOS-App aus und geben Sie die App-ID ein.

   f. Klicken Sie auf **[!UICONTROL Speichern]**.

   Sie müssen mindestens eine iOS-App und eine App-ID angeben. Andernfalls wird ein Fehler ausgegeben.

   >[!IMPORTANT]
   >
   >Sie können die Dokumente aktualisieren, indem Sie auf Aktualisieren im Abschnitt Optionen für universelle Links und Anwendungslinks klicken. Wenn Sie auf **[!UICONTROL Aktualisieren]** klicken, werden Sie in einem Warnhinweis darüber informiert, dass sich diese Aktion auf alle bisher erstellten universellen Links bzw. App-Links auswirkt.

### Universelle Links verwenden

1. Erstellen Sie in Adobe Mobile Services einen Marketinglink, der universelle Links verwendet:

   a. Wählen Sie die App auf der Mobile Services-Startseite aus. Klicken Sie auf **[!UICONTROL Akquise]** > **[!UICONTROL Marketing Link Builder]**.

   b. Klicken Sie auf **[!UICONTROL Neu erstellen]**.

   c. Wählen Sie unter **[!UICONTROL Optionen für Marketinglinks]** die Option **[!UICONTROL Universelle Links oder App-Links verwenden]** aus.

   d. Wenn Sie die Standortverknüpfungsdokumente im obigen Abschnitt *Standortverknüpfungsdokumente in Adobe Mobile Services einrichten* konfiguriert haben, ist diese Option standardmäßig aktiviert.

   Wenn Sie die Dokumente nicht konfiguriert haben, ist die Option **[!UICONTROL Universelle Links oder App-Links verwenden]** deaktiviert und die Option **[!UICONTROL Interstitials verwenden]** ist standardmäßig aktiviert.

   e. Wenn die Option **[!UICONTROL Universelle Links oder App-Links verwenden]** aktiviert ist, wird das Feld **[!UICONTROL Benutzerdefinierter Pfad]** angezeigt.

   Hierüber können Benutzer den URL-Pfad nach der Domäne sowie beliebige Abfrageparameter definieren. Wenn Sie beispielsweise  `my/universal/link?os=9.2` eingeben, lautet Ihre vollständige Marketinglink-URL `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`.

   f. Klicken Sie auf die Registerkarte **[!UICONTROL Entscheidungen]** und konfigurieren Sie Ihren Entscheidungsbaum.

   h. Wenn die iOS-App installiert ist, verarbeitet die App den Deep-Link mit dessen Logik. Das endgültige Ziel dient nur als Fallback, wenn die App nicht installiert ist. Da die App nicht installiert ist, kann das endgültige Ziel nur ein Web-Link oder ein Appstore sein.

   i. Klicken Sie auf **[!UICONTROL Speichern]**.

>[!TIP]
>
>Sobald ein Marketinglink gespeichert wurde, können die Optionen für Marketinglinks nicht mehr geändert werden. Dies wurde so festgelegt, damit sich das Verhalten bereits verbreiteter Marketinglinks nicht ändert.


### App-Links konfigurieren

1. Gehen Sie zu [Android-App-Links hinzufügen](https://developer.android.com/studio/write/app-link-indexing), um App-Links in Ihrer Android-App einzurichten.

1. Richten Sie die Standortverknüpfungsdokumente in Adobe Mobile Services ein:

   a. Wählen Sie auf der Mobile Services-Startseite die App aus, für die Sie App-Links einrichten möchten.

   b. Klicken Sie auf **[!UICONTROL App-Einstellungen verwalten]**.

   c. Stellen Sie sicher, dass die Android-App, die die universellen Links oder App-Links verarbeitet, zum Abschnitt **[!UICONTROL Appstore-Apps hinzufügen]** hinzugefügt wurde.

   >[!TIP]
   >
   >Wenn dieser Bereich nicht angezeigt wird, klicken Sie auf den Link **[!UICONTROL Appstore-App hinzufügen]**.

   d. Scrollen Sie zum Abschnitt **[!UICONTROL Optionen für universelle Links und App-Links]**.

   e. Klicken Sie auf die Registerkarte **[!UICONTROL App-Links (Android)]**.

   f. Wählen Sie eine Android-App aus und geben Sie einen SHA-256-Zertifikatsfingerabdruck ein.

   g. Klicken Sie auf **[!UICONTROL Speichern]**.

   Sie müssen mindestens eine Android-App und ein SHA-256-Zertifikat angeben. Andernfalls wird ein Fehler ausgegeben.

   >[!IMPORTANT]
   >
   >Sie können die Dokumente aktualisieren, indem Sie auf **[!UICONTROL Aktualisieren]** im Abschnitt **[!UICONTROL Optionen für universelle Links und Anwendungslinks]** klicken. Wenn Sie auf **[!UICONTROL Aktualisieren]** klicken, werden Sie in einem Warnhinweis darüber informiert, dass sich diese Aktion auf alle bisher erstellten universellen Links bzw. App-Links auswirkt.

### App-Links verwenden

1. Erstellen Sie in Adobe Mobile Services einen Marketinglink, der App-Links verwendet:

   a. Wählen Sie die App auf der Mobile Services-Startseite aus. Klicken Sie auf **[!UICONTROL Akquise]** > **[!UICONTROL Marketing Link Builder]**.

   b. Klicken Sie auf **[!UICONTROL Neu erstellen]**.

   c. Wählen Sie im Abschnitt **[!UICONTROL Optionen für Marketinglinks]** die Option **[!UICONTROL Universelle Links oder App-Links verwenden]** aus.

   d. Wenn Sie die Standortverknüpfungsdokumente aus Schritt 2 konfiguriert haben, ist diese Option standardmäßig ausgewählt.

   Anderenfalls ist die Option **[!UICONTROL Universelle Links oder App-Links verwenden]** deaktiviert und die Option **[!UICONTROL Interstitials verwenden]** ist standardmäßig aktiviert.

   e. Wenn die Option **[!UICONTROL Universelle Links oder App-Links verwenden]** aktiviert ist, wird das Feld **[!UICONTROL Benutzerdefinierter Pfad]** angezeigt.

   Hierüber können Benutzer den URL-Pfad nach der Domäne sowie beliebige Abfrageparameter definieren. Wenn Sie beispielsweise  `my/app/link?os=6.0` eingeben, lautet Ihre vollständige Marketinglink-URL `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`.

   f. Klicken Sie auf die Registerkarte **[!UICONTROL Entscheidungen]** und konfigurieren Sie Ihren Entscheidungsbaum.

   g. Wenn die Android-App installiert ist, verarbeitet die App den Deep-Link mit dessen Logik.

   Das endgültige Ziel dient nur als Fallback, wenn die App nicht installiert ist. Da die App nicht installiert ist, kann das endgültige Ziel nur ein Web-Link oder ein Appstore sein.

   h. Klicken Sie auf **[!UICONTROL Speichern]**.

>[!TIP]
>
>Nachdem ein Marketinglink gespeichert wurde, können die **[!UICONTROL Optionen für Marketinglinks]** nicht mehr geändert werden. Dies wurde so festgelegt, damit sich das Verhalten bereits verbreiteter Marketinglinks nicht ändert.

## Marketinglinks verwenden

Sie können diese Marketinglinks jetzt in Messaging- und anderen Bereichen Ihrer App verwenden.

>[!IMPORTANT]
>
>Klick-Tracking-Zählungen werden für universelle Links und App-Links nicht angezeigt. Außerdem können Sie keine Interstitials verwenden.

