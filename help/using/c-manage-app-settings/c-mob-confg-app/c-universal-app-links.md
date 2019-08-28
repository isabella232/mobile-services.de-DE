---
description: Mit universellen Links (ios) und App-Links (Android) können Sie eine Verbindung zu Deep Links in Ihren ios- oder Android-Apps herstellen.
keywords: mobile
seo-description: Mit universellen Links (ios) und App-Links (Android) können Sie eine Verbindung zu Deep Links in Ihren ios- oder Android-Apps herstellen.
seo-title: Apple Universal Links- und Android-App-Links
solution: Marketing Cloud, Analytics
title: Apple Universal Links- und Android-App-Links
topic: Metriken
uuid: 8 d 6441 dc -4307-4454-95 ea-d 77 ec 796 f 918
translation-type: tm+mt
source-git-commit: e65add089499f728827321e96e439f04ebb19a73

---


# Apple Universal Links- und Android-App-Links{#universal-links-and-app-links}

Mit universellen Links (ios) und App-Links (Android) können Sie eine Verbindung zu Deep Links in Ihren ios- oder Android-Apps herstellen.

>[!IMPORTANT]
>
>Ab ios 9.2 wird Deep-Linking nicht unterstützt. Sie müssen Apple Universal Links für Deep-Links zu Ihrer App oder Website verwenden.

## Universelle Links {#section_F8147944679A42E59CF4FD8814E5EF12}

Mit universellen Links können Sie eine Verbindung zu Deep Links in Ihrer ios-App herstellen und werden in ios 9.2 oder höher unterstützt. Wenn auf einen universellen Link zugegriffen wird, leitet ios den Link direkt zum Deeplink in Ihrer App weiter. Wenn Ihre App nicht installiert ist, wird stattdessen eine URL für Ihre Website in einem Browser geöffnet. Weitere Informationen zu universellen Links finden Sie unter [Universelle Links unterstützen](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html).

## App-Links

App-Links ermöglichen eine Verbindung zu Deep Links in Ihrer Android-App und werden in Android 6.0 oder höher unterstützt. Wenn auf einen App-Link zugegriffen wird, leitet Android den Link direkt zum Deeplink in Ihrer App weiter. Wenn Ihre App nicht installiert ist, wird stattdessen eine URL für Ihre Website in einem Browser geöffnet. For more information about App Links, see the [Handling Android App Links](https://developer.android.com/training/app-links/index.html).

## Erstellen eines Marketing-Links mithilfe eines universellen oder App-Links {#section_609ADEFFB9B441C4A8C45E936D0DC859}

Sie können einen Marketing-Link erstellen, der einen universellen oder App-Link verwendet.

### Konfigurieren eines universellen Links

1. Um universelle Links in Ihrer ios-App einzurichten, gehen Sie zur [Handhabung von universellen Links in Apple](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links).

2. Richten Sie in Adobe Mobile Services die Standortverknüpfungsdokumente ein:

   a. Wählen Sie auf der Mobile Services-Homepage die App aus, für die Sie universelle Links einrichten möchten.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Stellen Sie sicher, dass die ios-App, die die universellen Links verarbeitet, dem Abschnitt App Store-Apps **[!UICONTROL hinzufügen]** hinzugefügt wird.

   >[!TIP]
   >
   >Wenn **[!UICONTROL der Abschnitt App Store-Apps]** hinzufügen nicht angezeigt wird, klicken Sie auf **[!UICONTROL den Link App Store-App]** hinzufügen.

   d. Wählen Sie im Abschnitt "Optionen **[!UICONTROL für universelle Links und App-Links"]** eine ios-App aus und geben Sie die App-ID ein.

   f. Klicken Sie auf **[!UICONTROL Speichern]**.

   Sie müssen mindestens eine ios-App-Auswahl und eine App-ID bereitstellen, oder Sie erhalten einen Fehler.

   >[!IMPORTANT]
   >
   >Sie können die Dokumente aktualisieren, indem Sie auf Aktualisieren im Abschnitt Optionen für universelle Links und Anwendungslinks klicken. However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### Verwenden eines universellen Links

1. Erstellen Sie in Adobe Mobile Services einen Marketing Link, der universelle Links verwendet:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Klicken **[!UICONTROL Sie auf Neu erstellen]**.

   c. Under **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Use Universal Links or App Links]**.

   d. Wenn Sie die Standortverknüpfungsdokumente im Abschnitt *Einrichten von Siteverknüpfungsdokumenten im Abschnitt "Adobe Mobile Services* " konfiguriert haben, ist diese Option standardmäßig ausgewählt.

   Wenn Sie die Dokumente nicht konfiguriert haben, ist die Option "Universelle Links **[!UICONTROL verwenden" oder" App-Verknüpfungen]** verwenden" deaktiviert, und **[!UICONTROL Zwischenräume]** werden standardmäßig verwendet.

   e. Wenn die Option "Universelle Links **[!UICONTROL verwenden" oder" App-Links]** " ausgewählt ist, wird das **[!UICONTROL Feld "Benutzerdefinierte Pfade]** " angezeigt.

   Hierüber können Benutzer den URL-Pfad nach der Domäne sowie beliebige Abfrageparameter definieren. Wenn Sie beispielsweise `my/universal/link?os=9.2`, wird Ihre vollständige Marketing Link-URL.`https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`

   f. Klicken Sie auf **[!UICONTROL die]** Registerkarte Entscheidungen und konfigurieren Sie Ihre Entscheidungsstruktur.

   h. Wenn die ios-App installiert ist, verarbeitet die App das Deeplink mit seiner Logik. Das endgültige Ziel dient nur als Ausweichmöglichkeit, wenn die App nicht installiert ist. Da die App nicht installiert ist, kann das endgültige Ziel nur ein Weblink oder App Store sein.

   i. Klicken Sie auf **[!UICONTROL Speichern]**.

>[!TIP]
>
>Sobald ein Marketing-Link gespeichert wurde, können die Marketing-Verknüpfungsoptionen nicht geändert werden. Dies liegt daran, dass Sie das Verhalten der Marketing-Links, die bereits verteilt wurden, nicht ändern möchten.


### App-Link konfigurieren

1. Um App-Links in Ihrer Android-App einzurichten, gehen Sie zum [Hinzufügen von Android-App-Links](https://developer.android.com/studio/write/app-link-indexing).

1. Richten Sie in Adobe Mobile Services die Standortverknüpfungsdokumente ein:

   a. Wählen Sie auf der Mobile Services-Homepage die App aus, für die Sie App-Links einrichten möchten.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Stellen Sie sicher, dass die Android-App, die universelle Links oder App-Links verarbeitet, dem Abschnitt **[!UICONTROL App Store-Apps]** hinzufügen hinzugefügt wird.

   >[!TIP]
   >
   >If this section does not display, click the **[!UICONTROL Add App Store App]** link.

   d. Blättern Sie zum Abschnitt "Optionen **[!UICONTROL für universelle Links und]** App-Links" .

   e. Klicken Sie auf die **[!UICONTROL Registerkarte App-Links]** (Android).

   f. Wählen Sie eine Android-App aus und geben Sie einen SHA -256-Zertifikatsfingerabdruck ein.

   g. Klicken Sie auf **[!UICONTROL Speichern]**.

   Sie müssen mindestens eine Android-App-Auswahl und ein SHA -256-Zertifikat bereitstellen oder es wird ein Fehler ausgegeben.

   >[!IMPORTANT]
   >
   >Sie können die Dokumente aktualisieren, indem Sie auf **[!UICONTROL Aktualisieren]** im Abschnitt **Optionen für universelle Links und Anwendungslinks]klicken.[!UICONTROL ** However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### App-Link verwenden

1. Erstellen Sie in Adobe Mobile Services einen Marketing Link, der App-Links verwendet:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Klicken **[!UICONTROL Sie auf Neu erstellen]**.

   c. Wählen Sie im Abschnitt **[!UICONTROL "Optionen]** für Marketing-Links" die Option **[!UICONTROL Universelle Links oder App-Links verwenden]**.

   d. Wenn Sie die Standortverknüpfungsdokumente aus Schritt 2 konfiguriert haben, ist diese Option standardmäßig ausgewählt.

   If not, the **[!UICONTROL Use Universal Links or App Links]** option is disabled, and **[!UICONTROL Use Interstitials]** is selected by default.

   e. Wenn universelle **[!UICONTROL Links oder App-Links]** verwendet werden, wird das Feld **[!UICONTROL "Benutzerdefinierte Pfade]** " angezeigt.

   Hierüber können Benutzer den URL-Pfad nach der Domäne sowie beliebige Abfrageparameter definieren. Wenn Sie beispielsweise `my/app/link?os=6.0`, wird Ihre vollständige Marketing Link-URL.`https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`

   f. Klicken Sie auf **[!UICONTROL die]** Registerkarte Entscheidungen und konfigurieren Sie Ihre Entscheidungsstruktur.

   g. Wenn die Android-App installiert ist, verarbeitet die App das Deeplink mit seiner Logik.

   Das endgültige Ziel dient nur als Fallback für die Installation der App. Da die App nicht installiert ist, kann das endgültige Ziel nur ein Weblink oder App Store sein.

   h. Klicken Sie auf **[!UICONTROL Speichern]**.

>[!TIP]
>
>After a Marketing Link is saved, the **[!UICONTROL Marketing Links Options]** cannot be altered. Dies liegt daran, dass Sie das Verhalten der Marketing-Links, die bereits verteilt wurden, nicht ändern möchten.

## Verwenden von Marketing-Links

Sie können jetzt diese Marketing-Links in Messaging und anderen Bereichen Ihrer App verwenden.

>[!IMPORTANT]
>
>Es wird keine Klick-Tracking-Anzahl mit universellen Links oder App-Links angezeigt, und Sie können auch keine Zwischenräume verwenden.

