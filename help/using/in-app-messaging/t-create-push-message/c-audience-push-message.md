---
description: Sie können Zielgruppenoptionen für Push-Nachrichten definieren und konfigurieren, einschließlich Datumsbereichsoptionen, Analytics-Segmenten und benutzerdefinierter Segmente.
keywords: mobile
seo-description: Sie können Zielgruppenoptionen für Push-Nachrichten definieren und konfigurieren, einschließlich Datumsbereichsoptionen, Analytics-Segmenten und benutzerdefinierter Segmente.
seo-title: Zielgruppe Definieren und Konfigurieren von Zielgruppensegmenten für Push-Nachrichten
solution: Marketing Cloud, Analytics
title: Zielgruppe Definieren und Konfigurieren von Zielgruppensegmenten für Push-Nachrichten
topic: Metriken
uuid: efd410e7-3b6c-4cf4-a26f-b11688adc491
translation-type: tm+mt
source-git-commit: f28ea0db13b8d8f209d7521d1f61f1c290e688aa

---


# Zielgruppe: Push-Nachrichten{#audience-define-and-configure-audience-segments-for-push-messages}

Sie können Zielgruppenoptionen für Push-Nachrichten definieren und konfigurieren, einschließlich Datumsbereichsoptionen, Analytics-Segmenten und benutzerdefinierter Segmente.

## Define audience segments {#section_7C4D2393CF7441959FE2381A02867CAC}

Wenn ein Zielgruppensegment für Push-Messaging erstellt wird, beinhaltet das Segment möglicherweise Benutzer aus einer oder mehreren Apps, da auch Report Suites bzw. Virtual Report Suites Daten aus einer oder mehreren Apps enthalten können. Weitere Informationen zu Virtual Report Suites finden Sie unter [Virtual report suites](/help/using/manage-apps/c-mob-vrs.md).

In Adobe Mobile Services können Marketingexperten Nachrichten an nur eine App pro Plattform pushen. Wenn sie versuchen, die Nachrichten an Segmente zu pushen, die Benutzer aus mehreren Apps enthalten, werden sie per Warnmeldung darüber benachrichtigt, dass das Fortsetzen des Vorgangs schwerwiegende Push-Fehler sowie ein mögliches Blacklisting der Benutzer verursachen kann. Wenn bei Ihnen Push-Fehler auftreten, lesen Sie den Abschnitt *Beheben von Push-Fehlern* unter [Troubleshooting push messaging](/help/using/in-app-messaging/t-create-push-message/c-schedule-push-message.md).

Informationen zur Verwendung von Audience Manager-Daten in Ihrer Segmentdefinition finden Sie unter [Audience Analytics](https://docs-author-stg.corp.adobe.com/content/help/en/analytics/integration/audience-analytics/mc-audiences-aam.html).

>[!IMPORTANT]
>
>If app users are blacklisted, marketers can **never** send push messages to those affected users again.

Wenn Sie ein Zielgruppensegment auswählen, das Benutzer aus mehreren Apps enthält, wird möglicherweise die folgende Warnung angezeigt:

![Mehrfachname](assets/multiple_appname.png)

The app name is based on the pared down version of the appId, which is automatically sent to Adobe Analytics by the Mobile Services SDK in the `<app name> <version number> (<bundle id>)` format.

>[!TIP]
>
>Die Versionsnummer ist optional.

Bis zu sechs Zahlengruppen für die Version und fünf Zahlengruppen für die Bundle-ID werden entfernt.

Beispiel:

* `Bea[rd]cons 1.0 (123)` wird angezeigt als `Bea[rd]cons`
* `Bea[rd]cons 1.2 (1.2)` will appear as `Bea[rd]cons`
* `Bea[rd]cons 1.2.3.4.5.6.7 (1111)` wird angezeigt als `Bea[rd]cons .7`
* `Bea[rd]cons 1.2.3. (1.2.3.4.5.6)` will appear as `Bea[rd]cons (.6)`

Um mit dem Senden von Push-Nachrichten an die aufgeführten Apps fortzufahren, aktivieren Sie das Kontrollkästchen **Ja, ich möchte fortfahren** und klicken Sie auf **[!UICONTROL Senden]**.

## Best Practices

Im Folgenden finden Sie einige Best Practices, die Sie sich merken sollten:

* Um unnötige Verwirrung zu vermeiden, definieren Sie **keine** Mobile App Virtual Report Suites, die Daten aus mehreren Apps enthalten.
* Verwenden Sie **jedes Mal**, wenn Sie eine Push-Nachricht senden möchten, eine eindeutige App-ID als Teil eines Zielgruppensegments.
So wird gewährleistet, dass Push-Benachrichtigungen an ein Zielgruppensegment gesendet werden, das **nur** zu einer App gehört.

### Beispiele

Im Folgenden finden Sie einige Beispiele zur richtigen Definition von Segmenten:

**Richtig:** Der Marketingexperte stellt Push-Zertifikate für die iOS- und Android-Versionen einer App bereit, beispielsweise Adobe Photoshop. Daraufhin kann der Marketingexperte eine Push-Benachrichtigung an ein Benutzersegment senden, dass sich über beide Plattformen erstreckt.

**Falsch:** Marketingexperten stellen Push-Zertifikate für die iOS- und Android-Versionen einer App bereit, beispielsweise Adobe Photoshop. Wenn die Marketingexperten ein Segment *aller aktiven Benutzer der letzten 30 Tage* erstellen und die Nachricht an dieses Segment pushen, erhalten nur Benutzer der Adobe Photoshop-iOS- und -Android-App die Push-Benachrichtigung. Die Benutzer der iOS- bzw. Android-App von Adobe Illustrator hingegen befinden sich auf der Blacklist. Weitere Informationen und Beispiele finden Sie im Abschnitt *Beheben von Push-Nachrichtenfehlern* unter [Fehlerbehebung für Push-Nachrichten](/help/using/in-app-messaging/t-create-push-message/c-troubleshooting-push-messaging.md).

## Configure audience segments {#section_A92C60885A30421B8150820EC1CCBF13}

1. Rufen Sie die Seite Zielgruppe auf, um eine neue Push-Nachricht zu erhalten.

   For more information, see [Create a push message](/help/using/in-app-messaging/t-create-push-message/t-create-push-message.md).

   As you configure the audience options, remember the following **important** information:

   * **[!UICONTROL Geschätzte Teilnehmer-Zielgruppe]** beschreibt die Anzahl der Geräte, die dem Adobe Analytics-Segment entsprechen, **und** die Anzahl teilnehmender Geräte.

      Sie können eine Schätzung der Benutzeranzahl in Ihren ausgewählten Segmenten anzeigen, die den Empfang von Nachrichten aktiviert haben und die Push-Nachricht erhalten. Die Gesamtanzahl der App-Benutzer wird unter der Schätzung angegeben, und zwar unabhängig davon, ob der Erhalt von Nachrichten aktiviert ist.

   * **[!UICONTROL Gesamt]beschreibt die Anzahl der Geräte, die dem Adobe Analytics-Segment entsprechen.**

   * Push messages are sent to the devices that are part of a defined Adobe Analytics segment **and** that have opted-in for push messages.

      Das bedeutet, dass das SDK für die Push-Teilnehmer-eVar den Wert `True` gesendet hat.

   * Even though the device has a valid device token, unless Adobe Analytics has set the opted-in flag, the message is not pushed to the device.

   * Weitere Informationen zur Fehlerbehebung bei Push-Nachrichten finden Sie unter folgenden Themen:

      * [Push messaging in iOS](https://docs.adobe.com/content/help/en/mobile-services/ios/messaging-ios/push-messaging/push-messaging.html)

      * [Push messaging in Android](https://docs.adobe.com/content/help/en/mobile-services/android/messaging-android/push-messaging/push-messaging.html)

1. Geben Sie Informationen in folgende Felder ein:

   * **[!UICONTROL Während]**

      Geben Sie hier den Zeitraum für die geschätzte Zielgruppe an. Wählen Sie aus der Dropdownliste **[!UICONTROL Während]eine Option aus:**

   * **[!UICONTROL Mit der letzten]** können Sie einen relativen Zeitraum, wie z. B. die letzten 7, 30 oder 60 Tage, ab dem Zeitpunkt auswählen, zu dem die Nachricht gepusht werden sollte.

      Wenn Sie beispielsweise die letzten 30 Tage auswählen und die Übertragung der Nachricht für den 31. Oktober planen, setzt sich die geschätzte Zielgruppe aus den Benutzern zusammen, die den Erhalt von Push-Nachrichten in den 30 Tagen vor dem 31. Oktober aktiviert haben.

   * **[!UICONTROL Mit des statischen Bereichs]** können Sie einen statischen Bereich auswählen, indem Sie das Start- und Enddatum für den geschätzten Zielgruppenbereich festlegen.

      Um nochmals das vorangegangene Beispiel heranzuziehen: Wenn Sie einen Datumsbereich zwischen dem 1. Oktober und dem 15. Oktober auswählen, die Übertragung der Nachricht jedoch für den 31. Oktober planen, setzt sich die geschätzte Zielgruppe aus den Benutzern zusammen, die den Erhalt von Push-Nachrichten im angegebenen statischen Bereich (1. Oktober bis 15. Oktober) aktiviert haben.

   * **[!UICONTROL Analytics-Segmente]**

      Wählen Sie ein vorhandenes Adobe Analytics-Segment aus der Dropdownliste aus. For more information, see [Build segments](https://docs.adobe.com/content/help/en/analytics/components/segmentation/segmentation-workflow/seg-build.html).

   * **[!UICONTROL Benutzerdefinierte Segmente]**

      Select a metric or variable from the drop-down list (for example, **[!UICONTROL Days Since Last Use]** or **[!UICONTROL Point of Interest]**) and configure the filter as desired. Das folgende benutzerdefinierte Segment beispielsweise ist auf Benutzer ausgerichtet, die ein Smartphone mit iOS besitzen und sich in der Region Kalifornien (USA) aufhalten.
   >[!IMPORTANT]
   >
   >In the **[!UICONTROL Create Audience]** section, if you click **[!UICONTROL And]**, a dialog box appears that reminds you to ensure that each app that is listed **must** have a valid certificate. If you clicked **[!UICONTROL Or]**, the default dialog box appears. For more information about valid certificates and report suites, see [Virtual report suites](/help/using/manage-apps/c-mob-vrs.md).
