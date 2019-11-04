---
description: Konfigurieren Sie Erlebnisoptionen für In-App-Nachrichten, einschließlich Typ (Vollbild, Warnhinweis oder Benachrichtigung) sowie Anzeige-, Text- und Schaltflächenoptionen.
keywords: mobile
seo-description: Konfigurieren Sie Erlebnisoptionen für In-App-Nachrichten, einschließlich Typ (Vollbild, Warnhinweis oder Benachrichtigung) sowie Anzeige-, Text- und Schaltflächenoptionen.
seo-title: Erlebnis In-App-Nachricht
solution: Experience Cloud,Analytics
title: Erlebnis In-App-Nachricht
topic: Metriken
uuid: 4c6d6756-47fb-4f1b-8338-0b0c9b0fceb0
translation-type: ht
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Erlebnis: In-App-Nachricht {#experience-in-app-message}

Konfigurieren Sie Erlebnisoptionen für In-App-Nachrichten, einschließlich Typ (Vollbild, Warnhinweis oder Benachrichtigung) sowie Anzeige-, Text- und Schaltflächenoptionen.

1. Klicken Sie in Ihrer App auf **[!UICONTROL Messaging]** &gt; **[!UICONTROL Nachrichten verwalten]** &gt; **[!UICONTROL Nachricht erstellen]** &gt; **[!UICONTROL In-App-Nachricht erstellen]**.
1. Geben Sie auf der Seite Erlebnis einen Namen für die Nachricht ein.
1. Füllen Sie die Felder im Abschnitt **[!UICONTROL Typ]** aus:

   * **[!UICONTROL Typ]**
Wählen Sie den Nachrichtentyp für die In-App-Nachrichtenkampagne aus:

      * **[!UICONTROL Vollbild]**
      * **[!UICONTROL Warnhinweis]**
      * **[!UICONTROL Lokale Benachrichtigung]**
   * **[!UICONTROL Vorlage]**

      Passen Sie eine dynamische Motto-Nachrichtenvorlage für Ihren Inhalt an.

      >[!TIP]
      >
      >Diese Option wird nur angezeigt, wenn Sie den Nachrichtentyp **[!UICONTROL Vollbild]** ausgewählt haben.

   * **[!UICONTROL Benutzerspezifische Berichte]**

      Laden Sie Ihren HTML-Inhalt (nur Vollbild). Sie müssen einen Clickthrough-Link und einen Link zum Abbrechen bereitstellen.

      1. Klicken Sie auf **[!UICONTROL Durchsuchen]** und laden Sie eine HTML-Datei herunter oder ziehen Sie ein HTML-Dokument in das Fenster.
      1. Klicken Sie auf **[!UICONTROL Beispiel herunterladen]**, um einen benutzerdefinierten HTML-Musterinhalt anzuzeigen.
      >[!TIP]
      >
      >Diese Option wird nur angezeigt, wenn Sie den Nachrichtentyp **[!FVollbild]** ausgewählt haben.



1. Füllen Sie die Felder im Abschnitt **[!UICONTROL Anzeige]** aus:

   * **[!UICONTROL Design]**
   Wählen Sie ein Design für Ihre Nachricht aus.

   * **[!UICONTROL Layout]**

      Wählen Sie das App-Layout auf dem Gerätebildschirm aus.

   * **[!UICONTROL Bild-URL]**

      URL für ein Bild. Wenn Sie bei Verwendung der Vollbildvorlage Probleme mit der Größenanpassung haben, lesen Sie den Abschnitt *Mein Bild passt nicht genau in den in der Vorlage vorgesehenen Platz* unter [Fehlerbehebung von In-App-Nachrichten](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).

   * **[!UICONTROL Bild-Bundle]**

      Pfad zu einem Bild in Ihrem Anwendungscode-Bundle. Diese Option wird verwendet, wenn kein Bild vorhanden. oder das angegebene Bild nicht verfügbar ist. Das Bild kann beispielsweise nicht verfügbar sein, weil das entsprechende Gerät derzeit offline ist. Wenn Sie bei Verwendung der Vollbildvorlage Probleme mit der Größenanpassung haben, lesen Sie den Abschnitt *Mein Bild passt nicht genau in den in der Vorlage vorgesehenen Platz* unter [Fehlerbehebung von In-App-Nachrichten](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).


1. Füllen Sie die Felder im Abschnitt **[!UICONTROL Text]** aus:

   * **[!UICONTROL Header]**

      Geben Sie den Text für den Nachrichten-Header ein.

   * **[!UICONTROL Inhalt]**

      Geben Sie den Text für den Nachrichteninhalt ein.

1. Füllen Sie die Felder im Abschnitt **[!UICONTROL Schaltflächen]** aus:

   * **[!UICONTROL Schaltfläche „Clickthrough“]**

      Beschriftung für die **[!UICONTROL Clickthrough]**-Schaltfläche Jeder Klick auf diese Schaltfläche zählt als erfolgreicher Clickthrough. Der Benutzer wird zum Ziel weitergeleitet.

   * **[!UICONTROL Ziel]**

      Wählen Sie ein bestimmtes Ziel aus, wie z. B. einen Web-, Deep- oder Hybrid-Link, zu dem Benutzer nach dem Clickthrough weitergeleitet werden. Die Umleitungs-URL für einen erfolgreichen Clickthrough.

      Die URL kann die folgenden Informationen enthalten:

      * `{userId}`, wird durch die Benutzer-ID ersetzt bzw. frei gelassen, wenn die Benutzer-ID nicht festgelegt ist.
      * `{trackingId}`, wird durch die Hilfe (entspricht dem *s_vi*-Cookie) ersetzt.
      * `{messageId}`, wird durch die eindeutige ID der In-App-Nachricht ersetzt.
      * `{lifetimeValue}`, wird durch den Lebenszeitwert ersetzt bzw. durch 0, wenn kein Wert vorhanden ist.
      Im Folgenden finden Sie ein Beispiel für das Verfolgen der Benutzer-ID: `https://www.mysite.com?uid={userId}`.

      Wenn die Clickthrough-URL `https://` oder `https://` verwendet, wird die URL außerhalb der App im Browser des Geräts geöffnet. Ansonsten unterstützt jede Plattform Schemata, mit denen Sie die App öffnen oder auf die App verweisen können, wenn die App dafür entwickelt wurde, das benutzerdefinierte Schema zu unterstützen.

      >[!TIP]
      >
      >Wenn Sie den Zieltyp **[!UICONTROL Web-Link]** oder **[!UICONTROL Benutzerspezifischer Link]** verwenden, wird der Zieltyp nicht verfolgt. Nur **[!UICONTROL Deep-Links]** werden verfolgt. Weitere Informationen finden Sie in [Ziele](/help/using/acquisition-main/c-create-destinations.md).


1. (Optional) Zeigen Sie eine Vorschau des Layouts Ihrer Nachricht an, indem Sie auf folgende Symbole klicken:

   * **[!UICONTROL Zusammenfassung]** blendet das Vorschaufenster aus.

      Um das Vorschaufenster wieder einzublenden, klicken Sie auf ![Vorschau](assets/icon_preview.png).

   * **[!UICONTROL Ausrichtung ändern]**

      Klicken Sie auf ![Ausrichtung](assets/icon_orientation.png), um die Ausrichtung der Vorschau von Hochformat in Querformat zu ändern. Bei Watches ändert sich die Vorschau von einem runden in ein eckiges Zifferblatt.

   * **[!UICONTROL Vorschau auf der Watch eines Benutzers]**

      Um eine Vorschau der Nachricht anzuzeigen, wie sie auf der Watch eines Benutzers angezeigt wird, klicken Sie auf ![Watch-Symbol](assets/icon_watch.png).

   * **[!UICONTROL Vorschau auf dem Mobiltelefon eines Benutzers]**

      Um eine Vorschau der Nachricht anzuzeigen, wie sie auf dem Mobiltelefon eines Benutzers angezeigt wird, klicken Sie auf ![Telefonsymbol](assets/icon_phone.png).

   * **[!UICONTROL Vorschau auf dem Tablet eines Benutzers]**

      Um eine Vorschau der Nachricht auf dem Tablet eines Benutzers anzuzeigen, klicken Sie auf ![Tablet-Symbol](assets/icon_tablet.png).

      Unten in der Vorschauansicht finden Sie eine Beschreibung der Zielgruppe, die Sie im vorigen Schritt ausgewählt haben. Unten im Vorschaufenster wird auch eine Beschreibung der Zielgruppe angegeben, die Sie im vorherigen Schritt ausgewählt haben.

1. Konfigurieren Sie die [Zeitplanoptionen](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md).
