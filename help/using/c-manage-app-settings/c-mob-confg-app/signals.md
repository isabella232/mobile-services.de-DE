---
description: Mit Postbacks können Sie durch Adobe Mobile erfasste Daten an einen Drittanbieterserver senden. Mit denselben Triggern und Eigenschaften wie bei der Anzeige einer In-App-Nachricht können Sie Adobe Mobile Services so konfigurieren, dass es benutzerdefinierte Daten an ein Drittanbieterziel sendet.
seo-description: Mit Postbacks können Sie durch Adobe Mobile erfasste Daten an einen Drittanbieterserver senden. Mit denselben Triggern und Eigenschaften wie bei der Anzeige einer In-App-Nachricht können Sie Adobe Mobile Services so konfigurieren, dass es benutzerdefinierte Daten an ein Drittanbieterziel sendet.
seo-title: Postbacks konfigurieren
title: Postbacks konfigurieren
uuid: a026575c-057b-4868-b6c8-9514cbc32b4d
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 100%

---


# Postbacks konfigurieren {#configure-postbacks}

Mit Postbacks können Sie durch Adobe Mobile erfasste Daten an einen Drittanbieterserver senden. Mit denselben Triggern und Eigenschaften wie bei der Anzeige einer In-App-Nachricht können Sie Adobe Mobile Services so konfigurieren, dass es benutzerdefinierte Daten an ein Drittanbieterziel sendet.

>[!IMPORTANT]
>
>Um Postbacks zu verwenden, müssen Sie SDK-Version 4.6 oder höher installieren. Weitere Informationen finden Sie unter [Android – Postbacks](/help/android/analytics-main/postbacks/postbacks.md) oder [iOS – Postbacks](/help/ios/analytics-main/postback/postback.md).

1. Klicken Sie auf den Namen der gewünschten App, um die zugehörige Seite App-Einstellungen verwalten aufzurufen, und klicken Sie dann oben rechts auf den Link **[!UICONTROL Postbacks verwalten]**.
1. Klicken Sie auf **[!UICONTROL Postback erstellen]**.
1. Geben Sie folgende Informationen in die Felder ein:

   * **[!UICONTROL Postback-Typ]**

      Wählen Sie **[!UICONTROL Benutzerdefiniert aus]**. In der Zukunft werden Vorlagen verfügbar sein.

   * **[!UICONTROL Name]**

      Geben Sie einen beschreibenden Namen für den Postback an.

   * **[!UICONTROL URL]**

      Geben Sie eine gültige Endpunkt-URL an (mit entsprechenden Abfrageparametern, die für GET-Anfragen benötigt werden). Sie erhalten diese URL von der Partei, an die Sie die Daten senden (Werbeserver oder Ihr eigener Endpunkt). Beispiel `https://my.server.com/?user=bob&amp;zip=90210&amp;c16=4.6.0-iOS&amp;c27=cln,132`.

   * **[!UICONTROL Kontextvariable]**

      Markieren Sie Teile der URL und wählen Sie die gewünschte Kontextvariable aus der Dropdown-Liste aus. Sie können auch Kontextvariablen in die URL einfügen. Die URL ersetzt alle Vorlagenvariablen durch Werte aus dem Treffer.

   * **[!UICONTROL Post-Körper hinzufügen]**

      Geben Sie weiteren Textinhalt für den Post an, beispielsweise bei einer Post-Anfrage. Wenn Sie Text für den Post-Körper angeben, geben Sie auch den Content-Typ für den Post-Körper an. Beispiel: `application/json`.

   * **[!UICONTROL Zeitüberschreitung (in Sekunden)]**

      Geben Sie an, wie lange (in Sekunden) auf den Postback gewartet werden soll.

   * **[!UICONTROL Auslöser]**

      Geben Sie einen oder mehrere Daten-Tags und Bedingungen an, die den Postback auslösen. Beispielsweise können Sie als Auslöser **[!UICONTROL Abgestürzt]** und als Bedingung **[!UICONTROL Vorhanden]** auswählen, damit der Postback bei einem Absturz der App ausgelöst wird. Sie können auch angeben, welche Metriken den Postback aktivieren. Beispielsweise können Sie als Auslöser **[!UICONTROL Gerätename]** und als Bedingungen **[!UICONTROL Gleich]** und **[!UICONTROL iPhone 6 Plus]** auswählen, damit der Postback bei einem Absturz der App auf iPhone 6 Plus-Geräten aktiviert wird.

   * **[!UICONTROL Eigenschaft(en)]**
   Geben Sie an, wer die Nachricht sehen kann, wenn sie ausgelöst wird. Zu den Optionen gehören **[!UICONTROL Sitzungslänge]**, **[!UICONTROL Erster Starttermin]** und **[!UICONTROL App-ID]**.

1. Klicken Sie auf **[!UICONTROL Speichern]**, um den Postback zu erstellen und zur Liste **[!UICONTROL Postbacks verwalten]** hinzuzufügen.

   Um den Postback künftig zu aktivieren, führen Sie einen der folgenden Schritte durch:

   * Aktivieren Sie in der Liste **[!UICONTROL Postbacks verwalten]** das Kontrollkästchen neben dem Postback und klicken Sie auf **[!UICONTROL Auswahl aktivieren]**.
   * Klicken Sie auf **[!UICONTROL Speichern und aktivieren]**, um die Änderungen zu speichern und den Postback sofort zu aktivieren.
