---
description: In der Benutzeroberfläche von Adobe Mobile Services können Sie festlegen, ob die Push-Nachricht sofort, später oder regelmäßig gesendet werden soll. Hierbei können Sie zwischen täglicher, wöchentlicher und monatlicher Wiederholung wählen.
keywords: mobile
seo-description: In der Benutzeroberfläche von Adobe Mobile Services können Sie festlegen, ob die Push-Nachricht sofort, später oder regelmäßig gesendet werden soll. Hierbei können Sie zwischen täglicher, wöchentlicher und monatlicher Wiederholung wählen.
seo-title: Push-Nachricht planen
solution: Marketing Cloud, Analytics
title: Push-Nachricht planen
topic: Metriken
uuid: 6810 e 27 a -016 f -4286-8 fe 2-9972 d 85 fa 326
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Zeitplan: Push-Nachrichten{#schedule-push-message}

In der Benutzeroberfläche von Adobe Mobile Services können Sie festlegen, ob die Push-Nachricht sofort, später oder regelmäßig gesendet werden soll. Hierbei können Sie zwischen täglicher, wöchentlicher und monatlicher Wiederholung wählen.

>[!TIP]
>
>Benutzer können die Planungseinstellungen für einen Push-Nachrichtenauftrag jederzeit ändern. Wenn keine passenden Daten für eine wiederkehrende geplante Nachricht – also eine Nachricht, die beispielsweise alle 31 Tage, immer am 31. Februar oder am jeweils fünften Dienstag des aktuellen Monats gesendet wird – vorhanden sind, wird keine Nachricht gesendet.

Berücksichtigen Sie folgende Informationen:

* Das richtige Datum und Uhrzeitformat ist `hh:mm` und `mm/dd/yyyy`.

* Sie können eine geplante Nachricht auf folgende Weise bearbeiten:

   * Ändern Sie das Datum in ein späteres Datum.
   * Ändern Sie das Wiederholungsintervall.

      Wenn Sie die Nachricht ursprünglich täglich gesendet haben, können Sie beispielsweise einstellen, dass sich die Nachricht nun wöchentlich wiederholen soll.

## Vor der Planung wiederkehrender Push-Nachrichten

Sie **müssen** folgende Informationen verinnerlichen, bevor Sie wiederkehrende Push-Nachrichten planen:

* Die Optionen, die in der Dropdownliste **[!UICONTROL Wiederholen]angezeigt werden, hängen vom eingegebenen bzw. ausgewählten Datum ab.**

   Wenn Sie beispielsweise eingegeben `Saturday, October 7`haben, werden die folgenden Optionen angezeigt:

   * **[!UICONTROL Nie]**
   * **[!UICONTROL Jeden Tag]**
   * **[!UICONTROL Jeden Samstag]**
   * **[!UICONTROL Am 7. jeden Monats]**
   * **[!UICONTROL Am 1. Samstag jeden Monats]**

* Push-Nachrichten werden nach Greenwich-Zeit (GMT) geplant und gesendet.

   Wenn Sie beispielsweise eine wiederkehrende Nachricht geplant haben, die ab dem 7. Oktober jeden Samstag um 12:00 Uhr **PST** gesendet werden soll, wird die Nachricht tatsächlich am Samstag um 19:00 Uhr **GMT** gesendet.
* Nachrichten werden abhängig davon, ob Sie sich in den USA, in Europa oder in Asien befinden, unterschiedlich gesendet.

   Wenn Sie sich beispielsweise in San Jose, Kalifornien befinden und eine Nachricht planen, die am ***31. Oktober*** um 17:30 Uhr **PST** gesendet werden soll, wird die Nachricht tatsächlich am ***1. November*** um 00:30 Uhr **GMT** gesendet. Wenn Sie sich in Tokio befinden und eine Nachricht planen, die am ***1. Januar*** um 05:30 Uhr gesendet werden soll, wird sie tatsächlich am ***31. Dezember*** um 20:30 Uhr **GMT** gesendet.
* Push-Nachrichten werden je nach Sommer- oder Winterzeit eine Stunde früher oder später gesendet.
* In Ihrem Bericht zu Push-Nachrichten wird die Nachricht in der lokalen Zeitzone Ihres Systems angezeigt.

   Wenn Sie als Startzeit beispielsweise 12:00 Uhr **PST** festgelegt haben, wird diese zwar um 19:00 Uhr **GMT** gesendet, im Bericht wird jedoch angezeigt, dass die Nachricht um 12:00 Uhr **PST** gesendet wurde.

## Schedule a recurring push message {#section_675BD754E5A04423A1751193698A978F}

1. Wählen Sie auf der Seite "Zeitplan" für eine neue Push-Nachricht **[!UICONTROL " Geplant]** «oder **[!UICONTROL "Jetzt"]**.

   For more information, see [Create a push message](/help/using/in-app-messaging/t-create-push-message/t-create-push-message.md).

   If you selected **[!UICONTROL Now]**, the message is pushed immediately. Um zu verhindern, dass eine Nachricht sofort geplant wird, klicken Sie auf **[!UICONTROL Als Entwurf speichern]**.

   ![](assets/schedule-push-message.png)

1. If you selected **[!UICONTROL Scheduled]**, click the calendar icon and select or type a start date.
1. Geben Sie darüber hinaus eine Uhrzeit ein. 
1. Under **[!UICONTROL Repeat]**, select one of the following options:

   * **[!UICONTROL Nie]**
   * **[!UICONTROL Jeden Tag]**
   * **[!UICONTROL Jeden Dienstag]**
   * **`<Day x>`des Monats**

      Die angezeigten Optionen hängen von dem ausgewählten bzw. eingegebenen Starttag ab.
   * **`<nth day>`jedes Monats**

      Der angezeigte Wert hängt vom ausgewählten bzw. eingegebenen Startdatum ab.

1. In **[!UICONTROL End Repeat]**, type an end date and time.
1. Klicken Sie auf eine der folgenden Optionen:

   * **[!UICONTROL Als Entwurf speichern]**

      Mit dieser Option speichern Sie die Nachricht im Entwurfsformat. Sie können diese Option wählen, um eine noch nicht fertige Nachricht zu speichern oder um die Nachricht zu speichern, sodass sie von einer anderen Person bearbeitet und genehmigt werden kann, bevor sie aktiviert wird.

      If you selected **[!UICONTROL Now]** in the previous step, the draft message is sent immediately on activation. Wenn Sie ein Datum und eine Uhrzeit zum Senden der Nachricht ausgewählt haben, wird die Nachricht gemäß diesem Zeitplan gesendet.

   * **[!UICONTROL Speichern und planen]**

      Mit dieser Option wird die Nachricht zum geplanten Zeitpunkt gesendet.

Um den Nachrichtenentwurf später zu senden, führen Sie einen der folgenden Schritte durch:

* Click **[!UICONTROL Manage Messages]**, select the check box next to the message, and click **[!UICONTROL Activate Selected]**.
* Klicken Sie auf **[!UICONTROL Speichern &amp; Senden], um die Nachricht zu speichern und zu senden.**
