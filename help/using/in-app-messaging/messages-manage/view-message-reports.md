---
description: Sie können Nachrichtenberichte für In-App- und Push-Nachrichten anzeigen.
keywords: mobile
seo-description: Sie können Nachrichtenberichte für In-App- und Push-Nachrichten anzeigen.
seo-title: Anzeigen von Nachrichtenberichten
solution: Marketing Cloud,Analytics
title: Anzeigen von Nachrichtenberichten
topic: Metriken
uuid: 0ac73a81-388f-4dfd-84d5-21b8db4b8c83
translation-type: tm+mt
source-git-commit: 44f531ad140827d563255fad197811185c5337c9

---


# View message reports{#view-message-reports}

Sie können Nachrichtenberichte für In-App- und Push-Nachrichten anzeigen.

1. Click ![report icon](assets/icon_report.png) in the **[!UICONTROL Report]** column for a message.
1. (**Optional**) Create a sticky filter for the report or change the time period by clicking the **[!UICONTROL Calendar]** icon.

   For more information about creating a sticky filter, see Add a sticky filter.[](/help/using/usage/reports-customize/t-sticky-filter.md)

>[!TIP]
>
>Je nach Art der angezeigten Nachricht kann der Bericht variieren.

## In-App-Nachrichten {#section_90B79BA58E8141F78538C187EB1BF8C7}

Wenn Sie Berichte für eine In-App-Nachricht anzeigen, sieht der Bericht ähnlich wie in der folgenden Abbildung aus:

![report message](assets/report_message.png)

### In-app message metrics

Here is a list of the metrics that are available for in-app messages:

* **[!UICONTROL Impression]**, wenn eine Nachricht ausgelöst wird.

* **[!UICONTROL Click through, when a user presses the Click Through button on an alert or full-screen message, and when a user opens the app from a local notification.]******

* **[!UICONTROL Abbrechen]**, wenn ein Benutzer in einer Warnmeldung oder in einer Vollbildmeldung auf die Schaltfläche " **[!UICONTROL Abbrechen]** "klickt.

* **[!UICONTROL Interaktionsrate]**, eine berechnete Metrik aus Adobe Analytics, ist das Ergebnis der Anzahl der Durchklicks geteilt durch die Anzahl der Impressionen.

## Push messages {#section_BEAFD858CA194185B6F88903446058E9}

Wenn Sie Berichte für eine Push-Nachricht anzeigen, sieht der Bericht ähnlich wie in der folgenden Abbildung aus:

![Push-Nachricht](assets/report_message_push.png)

In dem Diagramm oben wird die Anzahl der Benutzer angezeigt, die die Nachricht geöffnet haben.

### Push-Nachrichten-Metriken

Here is a list of the metrics that are available for push messages:

* **[!UICONTROL Zeit]**

   Der Zeitpunkt, zu dem die Nachricht von Mobile Services per Push an Geräte gesendet wurde.

* **[!UICONTROL Status]**

   Der Status der Nachricht und die verfügbaren Status sind:

   * **[!UICONTROL Cancelled]**
   * **[!UICONTROL Geplant]**
   * **[!UICONTROL Ausführen]**
   * **[!UICONTROL Executed]**

* **[!UICONTROL Veröffentlicht]**

   Die Anzahl der Gerätetoken, die erfolgreich an den Apple Push Notification Service/Firebase Cloud Messaging (APNS/FCM) gesendet wurden, um die Nachricht an die Benutzergeräte zu senden.

* **[!UICONTROL Fehlgeschlagen]**

   Die Anzahl der Gerätetoken, die nicht erfolgreich an APNS/FCM gesendet wurden. Mögliche Ursachen:

   * Die pushID ist ungültig.

   * Die Push-Plattform (APNS, FCM usw.), auf die Push-Vorgänge durchgeführt wurden, ist für die Anwendung des Auftrags nicht vorhanden. So könnte die Plattform z. B. iOS-Push-Token erfassen, während aber kein APNS-Service konfiguriert ist.

   * Die Nachricht kann auch fehlgeschlagen sein, weil der Push-Dienst nicht richtig konfiguriert war oder das Mobile Services-System ausgefallen ist.
   >[!IMPORTANT]
   >
   >Wenn es ungewöhnlich oft zu einem Fehlschlag kommt, überprüfen Sie die Konfiguration der Push-Dienste. Wenn die Push-Dienste korrekt konfiguriert zu sein scheinen, wenden Sie sich an die Adobe-Kundenunterstützung.

* **[!UICONTROL Auf der schwarzen Liste]**

   Die Anzahl der Gerätetoken, die nicht mehr gültig sind, um an APNS oder FCM gesendet zu werden. Dies bedeutet meist, dass die App vom Gerät deinstalliert wurde oder dass der Benutzer seine Teilnahmeeinstellungen für den Erhalt von Nachrichten geändert hat. Android und iOS verhalten sich unterschiedlich, wenn Token als in der Blacklist vorhandene Token gezählt werden. Android-Token erscheinen sofort in der Anzahl der Token auf der schwarzen Liste. iOS-Token werden anfangs als veröffentlicht angezeigt, in nachfolgenden Nachrichten gelten sie jedoch aufgrund des Feedbacks von APNS als in der Blacklist vorhanden.
