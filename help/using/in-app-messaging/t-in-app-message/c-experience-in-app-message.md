---
description: Konfigurieren Sie Erlebnisoptionen für In-App-Nachrichten, einschließlich Typ (Vollbild, Warnhinweis oder Benachrichtigung) und Anzeige-, Text- und Schaltflächenoptionen.
keywords: mobile
seo-description: Konfigurieren Sie Erlebnisoptionen für In-App-Nachrichten, einschließlich Typ (Vollbild, Warnhinweis oder Benachrichtigung) und Anzeige-, Text- und Schaltflächenoptionen.
seo-title: Experience  In-App Message
solution: Marketing Cloud, Analytics
title: In-App-Erlebnis
topic: Metriken
uuid: 4c6d6756-47fb-4f1b-8338-0b0c9b0fceb0
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Experience: in-app message {#experience-in-app-message}

Konfigurieren Sie Erlebnisoptionen für In-App-Nachrichten, einschließlich Typ (Vollbild, Warnhinweis oder Benachrichtigung) und Anzeige-, Text- und Schaltflächenoptionen.

1. In your app, click **[!UICONTROL Messaging]** &gt; **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]** &gt; **[!UICONTROL Create In-App]**.
1. Geben Sie auf der Seite Erlebnis einen Namen für die Nachricht ein.
1. Füllen Sie die Felder im Abschnitt **[!UICONTROL Typ]aus:**

   * **[!UICONTROL Type
Select the message type for your in-app message campaign:]**

      * **[!UICONTROL Vollbild]**
      * **[!UICONTROL Warnhinweis]**
      * **[!UICONTROL Lokale Benachrichtigung]**
   * **[!UICONTROL Vorlage]**

      Passen Sie eine dynamische Motto-Nachrichtenvorlage für Ihren Inhalt an.

      >[!TIP]
      >
      >This option is displayed only when you select the **[!UICONTROL Full Screen]** message type.

   * **[!UICONTROL Benutzerspezifische Berichte]**

      Laden Sie Ihren HTML-Inhalt (nur Vollbild). Sie müssen einen Clickthrough-Link und einen Link zum Abbrechen bereitstellen.

      1. Klicken Sie auf **[!UICONTROL Durchsuchen]und laden Sie eine HTML-Datei herunter oder ziehen Sie ein HTML-Dokument in das Fenster.**
      1. Klicken Sie auf **[!UICONTROL Beispiel herunterladen], um einen benutzerdefinierten HTML-Musterinhalt anzuzeigen.**
      >[!TIP]
      >
      >This option is displayed only when you select the **[!Full Screen]** message type.



1. Füllen Sie die Felder im Abschnitt **[!UICONTROL Anzeige]aus:**

   * **[!UICONTROL Design]**
   Wählen Sie ein Design für Ihre Nachricht aus.

   * **[!UICONTROL Layout]**

      Wählen Sie das App-Layout auf dem Gerätebildschirm aus.

   * **[!UICONTROL Bild-URL]**

      URL für ein Bild If you have sizing issues when using the full-screen template, see *My image does not fit exactly into the space provided by the template* in [Troubleshooting in-app messaging](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).

   * **[!UICONTROL Bild-Bundle]**

      Pfad zu einem Bild in Ihrem Anwendungscode-Bundle Diese Option wird verwendet, wenn kein Bild vorhanden oder das angegebene Bild nicht verfügbar ist. Das Bild kann beispielsweise nicht verfügbar sein, weil das entsprechende Gerät derzeit offline ist. If you have sizing issues when using the full-screen template, see *My image does not fit exactly into the space provided by the template* in [Troubleshooting in-app messaging](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).


1. Füllen Sie die Felder im Abschnitt **[!UICONTROL Text]aus:**

   * **[!UICONTROL Header]**

      Geben Sie den Text für den Nachrichten-Header ein.

   * **[!UICONTROL Inhalt]**

      Geben Sie den Text für den Nachrichteninhalt ein.

1. Füllen Sie die Felder im Abschnitt **[!UICONTROL Schaltflächen]aus:**

   * **[!UICONTROL Schaltfläche „Clickthrough“]**

      Beschriftung für die **[!UICONTROL Clickthrough]-Schaltfläche** Das Tippen auf diese Schaltfläche zählt als erfolgreicher Clickthrough. Der Benutzer wird zum Ziel umgeleitet.

   * **[!UICONTROL Ziel]**

      Wählen Sie ein bestimmtes Ziel aus, wie z. B. einen Web-, Deep- oder Hybrid-Link, zu dem Benutzer nach dem Clickthrough weitergeleitet werden. Die Umleitungs-URL für einen erfolgreichen Clickthrough.

      Die URL kann die folgenden Informationen enthalten:

      * `{userId}`, which is replaced with the user identifier or is blank when the user identifier is not set.
      * `{trackingId}`, der durch die aid ersetzt wird (korreliert mit dem *s_vi* -Cookie).
      * `{messageId}`, der durch die eindeutige ID der In-App-Nachricht ersetzt wird.
      * `{lifetimeValue}`, der durch den Lebenszeitwert ersetzt wird, oder 0, wenn kein Lebenszeitwert vorhanden ist.
      Im Folgenden finden Sie ein Beispiel für das Verfolgen der Benutzer-ID: `https://www.mysite.com?uid={userId}`.

      If the click-through URL uses `https://` or `https://`, the URL opens in the device browser outside the app. Ansonsten unterstützt jede Plattform Schemata, mit denen Sie die App öffnen oder auf die App verweisen können, wenn die App dafür entwickelt wurde, das benutzerdefinierte Schema zu unterstützen.

      >[!TIP]
      >
      >When you use the **[!UICONTROL Web Link]** or **[!UICONTROL Custom Link]** destination types, the destination type is not tracked. Nur **[!UICONTROL Deep-Links]werden verfolgt.** For more information, see [Destinations](/help/using/acquisition-main/c-create-destinations.md).


1. (Optional) Zeigen Sie eine Vorschau des Layouts Ihrer Nachricht an, indem Sie auf folgende Symbole klicken:

   * **[!UICONTROL Die Zusammenfassung]** blendet das Vorschaufenster aus.

      Click ![preview](assets/icon_preview.png) to redisplay the preview pane.

   * **[!UICONTROL Ausrichtung ändern]**

      To change the orientation of the preview from portrait to landscape mode, click ![orientation](assets/icon_orientation.png). Bei Watches ändert sich die Ausrichtung von einer Runde in eine quadratische Armbanduhr.

   * **[!UICONTROL Preview on a user's watch]**

      Wenn Sie eine Vorschau der Nachricht anzeigen möchten, wie sie auf der Uhr des Benutzers angezeigt wird, klicken Sie auf das Symbol ![für die Anzeige](assets/icon_watch.png).

   * **[!UICONTROL Preview on a user's mobile phone]**

      Um eine Vorschau der Nachricht anzuzeigen, wie sie auf dem Handy eines Benutzers angezeigt wird, klicken Sie auf das ![Telefonsymbol](assets/icon_phone.png).

   * **[!UICONTROL Vorschau auf dem Tablet eines Benutzers]**

      Um eine Vorschau der Nachricht auf dem Tablet eines Benutzers anzuzeigen, klicken Sie auf das Symbol ![für Tablets](assets/icon_tablet.png).

      Unten in der Vorschauansicht finden Sie eine Beschreibung der Zielgruppe, die Sie im vorigen Schritt ausgewählt haben. Unten im Vorschaufenster wird auch eine Beschreibung der Zielgruppe angegeben, die Sie im vorherigen Schritt ausgewählt haben.

1. Configure Schedule options.[](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md)
