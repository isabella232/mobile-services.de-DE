---
description: Mit Postbacks können Sie durch Adobe Mobile erfasste Daten an einen Drittanbieterserver senden. Mit denselben Auslösern und Eigenschaften wie bei der Anzeige einer In-App-Nachricht können Sie Mobile Services so konfigurieren, dass benutzerdefinierte Daten an ein Drittanbieterziel gesendet werden.
seo-description: Mit Postbacks können Sie durch Adobe Mobile erfasste Daten an einen Drittanbieterserver senden. Mit denselben Auslösern und Eigenschaften wie bei der Anzeige einer In-App-Nachricht können Sie Mobile Services so konfigurieren, dass benutzerdefinierte Daten an ein Drittanbieterziel gesendet werden.
seo-title: Postbacks konfigurieren
title: Postbacks konfigurieren
uuid: a026575c-057b-4868-b6c8-9514cbc32b4d
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Configure postbacks {#configure-postbacks}

Mit Postbacks können Sie durch Adobe Mobile erfasste Daten an einen Drittanbieterserver senden. Mit denselben Auslösern und Eigenschaften wie bei der Anzeige einer In-App-Nachricht können Sie Mobile Services so konfigurieren, dass benutzerdefinierte Daten an ein Drittanbieterziel gesendet werden.

>[!IMPORTANT]
>
>Um Postbacks zu verwenden, müssen Sie das 4.6 SDK oder höher installieren. Weitere Informationen finden Sie unter [Android – Postbacks](/help/android/analytics-main/postbacks/postbacks.md) oder [iOS – Postbacks](/help/ios/analytics-main/postback/postback.md).

1. Klicken Sie auf den Namen der gewünschten App, um die zugehörige Seite App-Einstellungen verwalten aufzurufen, und klicken Sie dann oben rechts auf den Link **Postbacks verwalten**.
1. Klicken Sie auf **[!UICONTROL Postback erstellen]**.
1. Geben Sie folgende Informationen in die Felder ein:

   * **[!UICONTROL Postback-Typ]**

      Wählen Sie **[!UICONTROL Benutzerdefiniert aus]**. In der Zukunft werden Vorlagen verfügbar sein.

   * **[!UICONTROL Name]**

      Geben Sie einen beschreibenden Namen für den Postback an.

   * **[!UICONTROL URL]**

      Specify a valid endpoint URL (with appropriate query parameters as needed for GET requests). Sie erhalten diese URL von der Partei, an die Sie die Daten senden (Werbeserver oder Ihr eigener Endpunkt). Beispiel `https://my.server.com/?user=bob&amp;zip=90210&amp;c16=4.6.0-iOS&amp;c27=cln,132`.

   * **[!UICONTROL Kontextvariable]**

      Markieren Sie Teile der URL und wählen Sie die gewünschte Kontextvariable aus der Dropdown-Liste aus. Sie können auch Kontextvariablen in die URL einfügen. Die URL ersetzt alle Vorlagenvariablen durch Werte aus dem Treffer.

   * **[!UICONTROL Post-Körper hinzufügen]**

      Geben Sie weiteren Textinhalt für den Post an, beispielsweise bei einer Post-Anfrage. Wenn Sie Text für den Haupttext des Beitrags angeben, geben Sie den Inhaltstyp für den Beitragstext an. Beispiel: `application/json`.

   * **[!UICONTROL Zeitüberschreitung (in Sekunden)]**

      Geben Sie an, wie lange (in Sekunden) auf den Postback gewartet werden soll.

   * **[!UICONTROL Auslöser]**

      Geben Sie einen oder mehrere Daten-Tags und Bedingungen an, die den Postback auslösen. For example, you might choose **[!UICONTROL Crashed]** as the trigger and **[!UICONTROL Exists]** as the condition to trigger the postback when the app crashes. Sie können auch angeben, welche Metriken den Postback aktivieren. For example, you can select **[!UICONTROL Device Name]** as the trigger, **[!UICONTROL Equals]**, and **[!UICONTROL iPhone 6 Plus]** as conditions to activate the postback when the app crashes on iPhone 6 Plus devices.

   * **[!UICONTROL Eigenschaft(en)]**
   Geben Sie an, wer die Nachricht sehen kann, wenn sie ausgelöst wird. Options include **[!UICONTROL Session Length**, **[!UICONTROL First Launch Date]**, and **[!UICONTROL App ID]**.

1. Klicken Sie auf **[!UICONTROL Speichern]**, um den Postback zu erstellen und zur Liste **Postbacks verwalten]hinzuzufügen.[!UICONTROL **

   Um den Postback künftig zu aktivieren, führen Sie einen der folgenden Schritte durch:

   * Aktivieren Sie in der Liste **[!UICONTROL Postbacks verwalten]** das Kontrollkästchen neben dem Postback und klicken Sie auf **[!UICONTROL Auswahl aktivieren]**.
   * Klicken Sie auf **[!UICONTROL Speichern und aktivieren], um die Änderungen zu speichern und den Postback sofort zu aktivieren.**
