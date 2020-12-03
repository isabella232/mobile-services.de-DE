---
description: Sie können die Push-Nachricht-ID als Auslöser für die In-App-Nachricht festlegen, die gesendet wird, wenn ein Anwender die App von der Push-Nachricht aus öffnet.
seo-description: Sie können die Push-Nachricht-ID als Auslöser für die In-App-Nachricht festlegen, die gesendet wird, wenn ein Anwender die App von der Push-Nachricht aus öffnet.
seo-title: Auslösen einer In-App-Nachricht, wenn die App aus einer Push-Nachricht geöffnet wird
title: Auslösen einer In-App-Nachricht, wenn die App aus einer Push-Nachricht geöffnet wird
uuid: e1c8e29d-1c2b-47b2-8ab2-6b6e15df86f6
translation-type: tm+mt
source-git-commit: 114bce95e41c8e13695689dd2da2dbc04cb17ad7
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 59%

---


# In-App-Nachricht auslösen, wenn die App von einer Push-Nachricht aus geöffnet wird{#trigger-an-in-app-message-when-the-app-is-opened-from-a-push-message}

Sie können die Push-Nachricht-ID als Auslöser für die In-App-Nachricht festlegen, die gesendet wird, wenn ein Anwender die App von der Push-Nachricht aus öffnet.

1. Ermitteln Sie die Push-Nachricht-ID für die Push-Nachricht, die an den Anwender gesendet wird.

   Sie können die Push-Nachrichten-ID während des Nachrichtenerstellungsarbeitsablaufs in der URL suchen.

   Siehe folgendes Beispiel:

   ![](assets/brandon_task1.png)

1. Speichern und aktivieren Sie die In-App-Nachricht mit dem folgenden Auslöser:

   `“a.push.payloadID” =`

   >[!TIP]
   >
   >Bei der Push-Nachricht-ID handelt es sich um die ID, die Sie in Schritt 1 ermittelt haben.

   Dieser Auslöser muss manuell hinzugefügt werden, da er in der Dropdown-Liste **[!UICONTROL Auslöser]** nicht verfügbar ist.

   ![](assets/brandon_task2.png)

1. Speichern und senden Sie die Push-Nachricht, die über die in Schritt 1 ermittelte Push-ID verfügt.
1. Klicken Sie durch die Push-Nachricht, um die App zu öffnen und zu überprüfen, dass die In-App-Nachricht beim Öffnen der App angezeigt wird.

   Beachten Sie beim Testen die folgenden Informationen:

   * Nach dem Speichern der In-App-Nachricht dauert es etwa 45 Sekunden, bis die gehostete Konfigurationsdatei mit der neuen Nachricht aktualisiert wird.
   * Die App sucht nach Konfigurationsdatei-Aktualisierungen (der neuen In-App-Nachricht), wenn ein **neuer** Start stattfindet. Daher müssen Sie sicherstellen, dass die App einen neuen Start auslöst, wenn auf die Push-Nachricht geklickt wird.

   Dies bedeutet in der Regel, dass Sie sicherstellen müssen, dass der Sitzungs-Timeout aufgetreten ist. Der standardmäßige Timeout beträgt 5 Minuten.

