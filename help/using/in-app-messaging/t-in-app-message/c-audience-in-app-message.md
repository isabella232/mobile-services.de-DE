---
description: Sie können Zielgruppenoptionen für In-App-Nachrichten konfigurieren, einschließlich der Anzeige-, Auslöse- und Eigenschaftsoptionen.
keywords: mobile
seo-description: Sie können Zielgruppenoptionen für In-App-Nachrichten konfigurieren, einschließlich der Anzeige-, Auslöse- und Eigenschaftsoptionen.
seo-title: Zielgruppe In-App-Nachricht
solution: Marketing Cloud, Analytics
title: Zielgruppe In-App-Nachricht
topic: Metriken
uuid: 6 c 815 d 4 c -7626-4 cf 4-9158-3 f 059 c 79317 a
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Audience: in-app message {#audience-in-app-message}

Sie können Zielgruppenoptionen für In-App-Nachrichten konfigurieren, einschließlich der Anzeige-, Auslöse- und Eigenschaftsoptionen.

1. In your app, click **[!UICONTROL Messaging]** &gt; **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]** &gt; **[!UICONTROL Create In-App]**.
1. Geben Sie auf der Seite Zielgruppe Informationen in folgende Felder ein:

   * **[!UICONTROL Ansicht]**

      Wählen Sie eine Option für das Anzeigen einer Nachricht aus:

      * **[!UICONTROL Immer]**

         Mit dieser Option wird die Nachricht jedes Mal angezeigt, wenn der Auslöser auftritt.

      * **[!UICONTROL Einmal]**

         Mit dieser Option wird die Nachricht nur beim ersten Auftreten des Auslösers angezeigt.

      * **[!UICONTROL Bis zum Clickthrough]**

         Mit dieser Option wird die Nachricht jedes Mal, wenn der Auslöser auftritt, bis zum Clickthrough des Benutzers angezeigt. Dieser Auslöser gilt nur für Vollbild- und Warnmeldungen. Die meisten Meldungen müssen weitergeleitet werden oder eine Internetressource verwenden und werden nicht offline angezeigt. Um die Meldung unabhängig von der Netzwerkverbindung anzuzeigen, aktivieren Sie das Kontrollkästchen **[!UICONTROL Offline anzeigen].**
   * **[!UICONTROL Auslöser]**

      Wählen Sie eine Option aus dem Dropdownmenü sowie eine Bedingung aus. Beispielsweise können Sie aus der ersten Dropdownliste die Option „**[!UICONTROL Gestartet]**“ und aus der zweiten Dropdownliste die Option „**Vorhanden]“ auswählen.[!UICONTROL ** Sie können auch benutzerspezifische Kontextdaten angeben, die im auslösenden Treffer enthalten sein müssen, damit die Nachricht angezeigt wird.

      >[!IMPORTANT]
      >
      >Wenn Sie mehrere Auslöser auswählen, müssen alle Auslöser für die Anzeige im selben Treffer auftreten.

   * **[!UICONTROL Eigenschaften]**
Sie können festlegen, wer die In-App-Nachricht beim Auslösen und Filtern (Segment) für Treffer anzeigen sollte, die bestimmte Daten enthalten. Sie können z. B. eine Regel definieren, bei der Zielpunkte den Begriff „Berlin“ enthalten sollen. Mit diesem Filter wird die Nachricht nur Kunden angezeigt, die sich zur Auslösezeit an einem Ihrer Zielpunkte befinden, die den Begriff „Berlin“ im Namen enthalten.



## Additional information about traits and triggers {#section_48C39EFB8CAA4F62B994FCC91DF588E6}

>[!IMPORTANT]
>
>Auslöser und Eigenschaften verwenden Daten, die von Ihrer App an Analytics übergeben werden. Diese Werte werden als Kontextdaten, zugeordnete Variablen und Metriken weitergegeben. Eine Variable ist ein textbasierter Wert, und eine Metrik ist ein numerischer Wert.

To see the mapping of these key value pairs in the Mobile Services UI and validate the value for your trigger, click **[!UICONTROL Manage App Settings]** &gt;  **[!UICONTROL Manage Variables &amp; Metrics]** &gt;, which displays the following tabs:

* **[!UICONTROL Standardvariablen und Metriken]**
* **[!UICONTROL Benutzerdefinierte Variablen]**
* **[!UICONTROL Benutzerspezifische Metriken]**

Nachdem Sie die Zuordnung validiert haben, wählen Sie den passenden Matcher oder logischen Operator, um Ihre Zielgruppe für die Nachricht zu konfigurieren.

### Selecting metrics and variables {#example_AB126F03BD1C4094B791E230B3DB1189}

![Auslöseroptionen](assets/custom_trigger_matcher_options.png)

Anhand der folgenden Szenarios können Sie bestimmen, ob eine Metrik oder eine Variable als Auslöser ausgewählt werden soll:

### Metriken

Eine Metrik ist eine Zahl, beispielsweise die Anzahl der Einkäufe.

1. Click **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]**.
1. Führen Sie die folgenden Schritte im Abschnitt **[!UICONTROL Auslöser]** auf der Registerkarte **Zielgruppe]aus:[!UICONTROL **

   1. Wählen Sie ein Standardereignis, z. B. **[!UICONTROL Gestartet]**, und wählen Sie **[!UICONTROL Vorhanden]**.
   1. Wählen Sie einen zweiten Auslöser, der ein benutzerdefinierter Datenpunkt ist und der einer Metrik zugeordnet ist.
   1. Under **[!UICONTROL Number]**, select a matcher option.

### Variablen

Eine Variable ist eine Textzeichenfolge, die eine eindeutige Kennung darstellt. Beispiele sind Land, Flughafen usw.

1. Click **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]**.
1. Führen Sie die folgenden Schritte im Abschnitt **[!UICONTROL Auslöser]** auf der Registerkarte **Zielgruppe]aus:[!UICONTROL **

   1. Wählen Sie ein Standardereignis, z. B. **[!UICONTROL Gestartet]**, und wählen Sie **[!UICONTROL Vorhanden]**.
   1. Wählen Sie einen zweiten Auslöser, der ein benutzerdefinierter Datenpunkt ist und der einer Variablen zugeordnet ist.
   1. Under **[!UICONTROL Text]**, select a matcher option.

For more information about context data, variables, and metrics, see [Managing your app](/help/using/manage-apps/manage-apps.md).
