---
description: Sie können die Push-Nachricht-ID als Auslöser für die In-App-Nachricht festlegen, die gesendet wird, wenn ein Anwender die App von der Push-Nachricht aus öffnet.
seo-description: Sie können die Push-Nachricht-ID als Auslöser für die In-App-Nachricht festlegen, die gesendet wird, wenn ein Anwender die App von der Push-Nachricht aus öffnet.
seo-title: In-App-Nachricht auslösen, wenn die App von einer Push-Nachricht aus geöffnet wird
title: In-App-Nachricht auslösen, wenn die App von einer Push-Nachricht aus geöffnet wird
uuid: e 1 c 8 e 29 d -1 c 2 b -47 b 2-8 ab 2-6 b 6 e 15 df 86 f 6
translation-type: tm+mt
source-git-commit: 114bce95e41c8e13695689dd2da2dbc04cb17ad7

---


# Trigger an in-app message when the app is opened from a push message{#trigger-an-in-app-message-when-the-app-is-opened-from-a-push-message}

Sie können die Push-Nachricht-ID als Auslöser für die In-App-Nachricht festlegen, die gesendet wird, wenn ein Anwender die App von der Push-Nachricht aus öffnet.

1. Ermitteln Sie die Push-Nachricht-ID für die Push-Nachricht, die an den Anwender gesendet wird.

   Sie können die Push-Nachricht-ID während des Workflows der Nachrichtenerstellung in der URL finden.

   Siehe folgendes Beispiel:

   ![](assets/brandon_task1.png)

1. Speichern und aktivieren Sie die In-App-Nachricht mit dem folgenden Auslöser:

   `“a.push.payloadID” =`

   >[!TIP]
   >
   >Die Push-Nachrichten-ID ist die ID, die Sie in Schritt 1 finden.

   Dieser Auslöser muss manuell hinzugefügt werden, da er in der Dropdown-Liste **[!UICONTROL Auslöser]nicht verfügbar ist.**

   ![](assets/brandon_task2.png)

1. Speichern und senden Sie die Push-Nachricht, die über die in Schritt 1 ermittelte Push-ID verfügt.
1. Klicken Sie durch die Push-Nachricht, um die App zu öffnen und zu überprüfen, dass die In-App-Nachricht beim Öffnen der App angezeigt wird.

   Beachten Sie beim Testen Folgendes:

   * Nach dem Speichern der In-App-Nachricht dauert es etwa 45 Sekunden, bis die gehostete Konfigurationsdatei mit der neuen Nachricht aktualisiert wird.
   * Die App sucht nach Aktualisierungen der Konfigurationsdatei (der neuen In-App-Nachricht), wenn es zu einem **neuen** Start kommt. Sie müssen also sicherstellen, dass die App einen neuen Start auslöst, wenn die Push-Nachricht angeklickt wird.
   In der Regel bedeutet dies, dass Sie sicherstellen müssen, dass es zu einem Sitzungs-Timeout gekommen ist. Der Standardwert für ein Timeout beträgt 5 Minuten.

