---
description: Sie können Nachrichtenberichte für In-App- und Push-Nachrichten anzeigen.
keywords: mobile
seo-description: Sie können Nachrichtenberichte für In-App- und Push-Nachrichten anzeigen.
seo-title: Nachrichtenberichte anzeigen
solution: Experience Cloud,Analytics
title: Nachrichtenberichte anzeigen
topic: Metriken
uuid: 0ac73a81-388f-4dfd-84d5-21b8db4b8c83
translation-type: ht
source-git-commit: 44f531ad140827d563255fad197811185c5337c9

---


# Nachrichtenberichte anzeigen{#view-message-reports}

Sie können Nachrichtenberichte für In-App- und Push-Nachrichten anzeigen.

1. Klicken Sie auf ![Berichtssymbol](assets/icon_report.png) in der Spalte **[!UICONTROL Bericht]** einer Nachricht.
1. (**Optional**) Erstellen Sie einen fixierbaren Filter für den Bericht oder ändern Sie den Zeitraum durch Klicken auf das Symbol **[!UICONTROL Kalender]**.

   Weitere Informationen zum Erstellen eines fixierbaren Filters finden Sie unter [Fixierbaren Filter hinzufügen](/help/using/usage/reports-customize/t-sticky-filter.md).

>[!TIP]
>
>Je nach angezeigtem Nachrichtentyp unterscheidet sich der Bericht.

## In-App-Nachrichten {#section_90B79BA58E8141F78538C187EB1BF8C7}

Wenn Sie Berichte für eine In-App-Nachricht anzeigen, sieht der Bericht ähnlich wie in der folgenden Abbildung aus:

![Berichtsnachricht](assets/report_message.png)

### Metriken für In-App-Nachrichten

Im Folgenden finden Sie eine Liste der Metriken, die für In-App-Nachrichten verfügbar sind:

* **[!UICONTROL Impression]**, wenn eine Nachricht ausgelöst wird.

* **[!UICONTROL Clickthrough]**, wenn ein Benutzer auf die Schaltfläche **[!UICONTROL Clickthrough]** in einem Warnhinweis oder einer Vollbildnachricht klickt und wenn ein Benutzer die App über eine lokale Benachrichtigung öffnet.

* **[!UICONTROL Abbrechen]**, wenn ein Benutzer auf die Schaltfläche **[!UICONTROL Abbrechen]** in einem Warnhinweis oder in einer Vollbildnachricht klickt.

* **[!UICONTROL Interaktionshäufigkeit]**, hierbei handelt es sich um eine berechnete Metrik aus Adobe Analytics. Sie entspricht der Anzahl an Clickthroughs dividiert durch die Anzahl an Impressionen.

## Push-Nachrichten {#section_BEAFD858CA194185B6F88903446058E9}

Wenn Sie Berichte für eine Push-Nachricht anzeigen, sieht der Bericht ähnlich wie in der folgenden Abbildung aus:

![Push-Nachricht](assets/report_message_push.png)

In dem Diagramm oben wird die Anzahl der Benutzer angezeigt, die die Nachricht geöffnet haben.

### Metriken für Push-Nachrichten

Im Folgenden finden Sie eine Liste der Metriken, die für Push-Nachrichten verfügbar sind:

* **[!UICONTROL Zeit]**

   Der Zeitpunkt, zu dem die Nachricht von Mobile Services per Push an Geräte gesendet wurde.

* **[!UICONTROL Status]**

   Der Status der Nachricht und die verfügbaren Status sind:

   * **[!UICONTROL Abgebrochen]**
   * **[!UICONTROL Geplant]**
   * **[!UICONTROL Wird ausgeführt]**
   * **[!UICONTROL Ausgeführt]**

* **[!UICONTROL Veröffentlicht]**

   Die Anzahl der Gerätetoken, die erfolgreich an Apple Push Notification Service/Firebase Cloud Messaging (APNS/FCM) gesendet wurden, um eine Nachricht an die Benutzergeräte zu übertragen.

* **[!UICONTROL Fehlgeschlagen]**

   Die Anzahl der Gerätetoken, die nicht erfolgreich an APNS/FCM gesendet wurden. Mögliche Fehlerursachen:

   * Die pushID ist ungültig.

   * Die Push-Plattform (APNS, FCM usw.), an die die Nachricht übertragen werden sollte, existiert nicht für die entsprechende App. So könnte die Plattform z. B. iOS-Push-Token erfassen, während aber kein APNS-Service konfiguriert ist.

   * Die Nachricht kann auch fehlgeschlagen sein, weil der Push-Dienst nicht richtig konfiguriert war oder das Mobile Services-System ausgefallen ist.
   >[!IMPORTANT]
   >
   >Wenn es ungewöhnlich oft zu einem Fehlschlag kommt, überprüfen Sie die Konfiguration der Push-Dienste. Wenn die Push-Dienste korrekt konfiguriert zu sein scheinen, wenden Sie sich an die Adobe-Kundenunterstützung.

* **[!UICONTROL Auf der schwarzen Liste]**

   Die Anzahl der Gerätetoken, die für das Senden an APNS oder FCM nicht mehr gültig sind. Dies bedeutet meist, dass die App vom Gerät deinstalliert wurde oder dass der Benutzer seine Teilnahmeeinstellungen für den Erhalt von Nachrichten geändert hat. Android und iOS verhalten sich unterschiedlich, wenn Token als in der Blacklist vorhandene Token gezählt werden. Android-Token erscheinen sofort in der Anzahl der Token auf der schwarzen Liste. iOS-Token werden anfangs als veröffentlicht angezeigt, in nachfolgenden Nachrichten gelten sie jedoch aufgrund des Feedbacks von APNS als in der Blacklist vorhanden.
