---
description: Sie können Erlebnisoptionen für Push-Nachrichten und Rich-Push-Nachrichten, einschließlich Optionen für Name, Nachrichtentext und Ziel, konfigurieren. Sie können außerdem erweiterte Optionen konfigurieren, einschließlich Nutzlastoptionen und benutzerdefinierter Optionen für iOS-Geräte.
keywords: mobile
seo-description: Sie können Erlebnisoptionen für Push-Nachrichten und Rich-Push-Nachrichten, einschließlich Optionen für Name, Nachrichtentext und Ziel, konfigurieren. Sie können außerdem erweiterte Optionen konfigurieren, einschließlich Nutzlastoptionen und benutzerdefinierter Optionen für iOS-Geräte.
seo-title: Erlebnispush-Nachricht
solution: Marketing Cloud, Analytics
title: Erlebnispush-Nachricht
topic: Metriken
uuid: 1 a 8 baf 3 e -9 fea -452 c-b 0 fc -4 ba 8 ac 270861
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Experience: push message {#experience-push-message}

Sie können Erlebnisoptionen für Push-Nachrichten und Rich-Push-Nachrichten, einschließlich Optionen für Name, Nachrichtentext und Ziel, konfigurieren. Sie können außerdem erweiterte Optionen konfigurieren, einschließlich Nutzlastoptionen und benutzerdefinierter Optionen für iOS-Geräte.

1. Klicken Sie auf der Seite Zielgruppe für eine neue Push-Nachricht auf **[!UICONTROL Erlebnis]**.

   ![Bildschirm mit Push-Push-Nachricht](assets/experience-push-message.png)

1. Geben Sie den Namen der Nachricht ein.
1. Geben Sie in folgende Felder im Abschnitt **[!UICONTROL Meldung]Informationen ein:**

   * **[!UICONTROL Inhalt]**

      Geben Sie den Text der Nachricht ein. Sie können bis zu 140 Zeichen verwenden.

   * **[!UICONTROL Medien-URL]**

      Geben Sie die URL der Mediendatei ein, die Sie für die Push-Nachricht verwenden möchten. Anforderungen für die Verwendung von Rich-Push-Benachrichtigungen finden Sie unter *Anforderungen für Rich-Push-Benachrichtigungen* unten.

      >[!IMPORTANT]
      >
      >Beachten Sie beim Anzeigen von Bildern oder Videos in Push-Nachrichten folgende Punkte:
      > * Die `attachment-url`-Daten werden in der Push-Nutzlast verarbeitet.
      > * Die Medien-URL muss kurzzeitige Zunahmen der Anfragenanzahl verkraften können.


   * **[!UICONTROL Ziel]**

      Wählen Sie ein bestimmtes Ziel aus, wie z. B. einen Web-, Deep- oder Hybrid-Link, zu dem Benutzer nach dem Clickthrough weitergeleitet werden. For more information, see [Destinations](/help/using/acquisition-main/c-create-destinations.md).

      >[!TIP]
      >
      >When you use the * **[!UICONTROL Web Link]** or **[!UICONTROL Custom Link]** destination types, the destination type is not tracked. Nur **[!UICONTROL Deep-Links]werden verfolgt.**

## Anforderungen für Rich-Push-Benachrichtigungen

Hier finden Sie die Anforderungen zum Senden von Rich-Push-Benachrichtigungen:

* **Unterstützte Versionen**

   Rich-Push-Benachrichtigungen werden in den folgenden Versionen unterstützt:
   * Android 4.1.0 oder höher
   * iOS 10 oder höher

      >[!IMPORTANT]
      >
      >Beachten Sie die folgenden Informationen:
      >* Rich-Mails, die an frühere Versionen gesendet werden, werden weiterhin gesendet, aber nur der Text wird angezeigt.
      >* Derzeit werden keine Watches unterstützt.


* **Dateiformate**

   Im Folgenden finden Sie die unterstützten Dateiformate:
   * Bilder: JPG und PNG
   * Animationen (nur iOS): GIF
   * Videos (nur iOS): MP4

* **URL-Formate**
   * Nur HTTPS

* **Größe**
   * Bilder müssen in einem Format von 2:1 vorliegen oder abgeschnitten werden.

Weitere Informationen zur Konfiguration von Rich-Push-Benachrichtigungen finden Sie unter folgenden Themen:

* [Push-Benachrichtigungen in Android empfangen](/help/android/messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
* [Rich-Push-Benachrichtigungen in ios erhalten](/help/ios/messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)

So konfigurieren Sie eine Push-Nachricht auf der Erlebnisseite:

1. (**Optional**) Click the **[!UICONTROL Show Advanced Options]** link to configure additional options:

   * **[!UICONTROL Nutzlast: Daten]**

      Stellen Sie eine benutzerdefinierte Push-Nutzlast in JSON bereit, die per Push- oder lokale Benachrichtigung an die App gesendet wird. Der Grenzwert unter Android und iOS liegt bei 4 KB.

   * **[!UICONTROL Apple-Optionen: Kategorie]**

      Geben Sie eine Kategorie für Push- und lokale Benachrichtigungen an. Weitere Informationen finden Sie unter [Managing Your App's Notification Support](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SupportingNotificationsinYourApp.html#//apple_ref/doc/uid/TP40008194-CH4-SW9) in der *iOS Developer Library*.

   * **[!UICONTROL Apple-Optionen: Sound]**

      Geben Sie den Namen der Sounddatei an, die in Ihrem App-Bundle wiedergegeben werden soll. Es ist kein standardmäßiger Sound festgelegt. Weitere Informationen finden Sie unter [Managing Your App's Notification Support](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SupportingNotificationsinYourApp.html#//apple_ref/doc/uid/TP40008194-CH4-SW10) in der *iOS Developer Library*.

   * **[!UICONTROL Apple-Optionen: Inhalt verfügbar]**

      Wählen Sie diese Option, damit iOS beim Eintreffen der Nachricht Ihre im Hintergrund laufende App aktiviert und ihr auf der Grundlage der Nutzlast der Nachricht das Ausführen von Code erlaubt. Weitere Informationen finden Sie unter [Apple Push Notification Service](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1) in der *iOS Developer Library*.

1. (Optional) Zeigen Sie eine Vorschau des Layouts Ihrer Nachricht an, indem Sie auf folgende Symbole klicken:

   * **[! UICONTROL X Zusammenfassung}**

      Blendet den Vorschaufenster aus. Klicken ![Sie auf Vorschau](assets/icon_preview.png) , um den Vorschaufenster erneut anzuzeigen.

   * **[!UICONTROL Ausrichtung ändern]**

      To change the orientation of the preview from portrait to landscape mode, click ![orientation](assets/icon_orientation.png). Bei Watches ändert sich die Vorschau von einem runden Zifferblatt in ein eckiges Zifferblatt.

   * **[!UICONTROL Anzeigen einer Vorschau für ein Benutzer]**

      Um eine Vorschau Ihrer Nachricht anzuzeigen, wie sie auf den Watches eines Benutzers angezeigt wird, klicken Sie auf ![Symbol ansehen](assets/icon_watch.png).

   * **[!UICONTROL Vorschau auf dem Mobiltelefon eines Benutzers]**

      Um eine Vorschau Ihrer Nachricht anzuzeigen, so wie sie auf dem Mobiltelefon-Klicksymbol ![eines Benutzers angezeigt](assets/icon_phone.png)wird.

   * **[!UICONTROL Vorschau auf dem Tablet eines Benutzers]**

      Um eine Vorschau Ihrer Nachricht auf dem Tablet eines Benutzers anzuzeigen, klicken Sie auf ![das Tablet-Symbol](assets/icon_tablet.png).
   Unten in der Vorschauansicht finden Sie eine Beschreibung der Zielgruppe, die Sie im vorigen Schritt ausgewählt haben.

1. (**Optional**) Click **[!UICONTROL Test]** to push your message to specified devices for testing purposes.
1. Wählen Sie den Dienst aus und geben Sie die Push-Token für mindestens ein Gerät ein, an die Sie die Nachricht pushen möchten.

   Wenn Sie die Nachricht an mehr als ein Gerät senden möchten, geben Sie die Token in einer durch Kommas getrennten Liste an.

1. Konfigurieren die Planungsoptionen für die Nachricht.

   Weitere Informationen finden [Sie unter Planen: Push-Nachricht](/help/using/in-app-messaging/t-create-push-message/c-schedule-push-message.md).
