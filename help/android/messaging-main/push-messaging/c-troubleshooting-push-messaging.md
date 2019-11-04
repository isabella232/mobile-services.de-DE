---
description: Mithilfe dieser Informationen können Probleme mit Push-Nachrichten behoben werden.
keywords: mobile
seo-description: Mithilfe dieser Informationen können Probleme mit Push-Nachrichten behoben werden.
seo-title: Fehlerbehebung bei Push-Nachrichten
solution: Experience Cloud,Analytics
title: Fehlerbehebung bei Push-Nachrichten
topic: Metriken
uuid: 9c4a9371-6691-4a2c-a6c1-b9f901a41599
translation-type: ht
source-git-commit: 12e01e112debffd877dd62f1fd2505724b2aae7d

---


# Fehlerbehebung bei Push-Nachrichten {#troubleshooting-push-messaging}

Mithilfe dieser Informationen können Probleme mit Push-Nachrichten behoben werden.

## Warum gibt es beim Senden von Push-Nachrichten manchmal Verzögerungen?

Folgende Verzögerungen können bei Push-Nachrichten für Mobile Services auftreten:

* Warten auf einen Analytics-Treffer

   Jede Report Suite verfügt über eine Einstellung, die festlegt, wann eingehende Analytics-Treffer verarbeitet werden sollen. Der Standardwert liegt bei 1 Stunde zur vollen Stunde. Die eigentliche Verarbeitung von Analytics-Treffern kann bis zu 30 Minuten dauern, in der Regel sind es jedoch 15 bis 20 Minuten. Angenommen, eine Report Suite verarbeitet Treffer stündlich. Berücksichtigt man nun die Verarbeitungszeit von maximal 30 Minuten, kann es bis zu 90 Minuten dauern, bis ein eingehender Treffer für eine Push-Nachricht verfügbar ist. Wenn ein Benutzer die App um 9:01 Uhr gestartet hat, wird der Treffer auf der Mobile Services-Benutzeroberfläche als neuer Unique User zwischen 10:15 und 10:30 Uhr angezeigt.

* Warten auf Push-Dienst

   Der Push-Dienst (APNS oder FCM) versendet die Nachricht möglicherweise nicht sofort. Dies kann in Ausnahmefällen 5 bis 10 Minuten in Anspruch nehmen. Auf der Seite Nachrichten können Sie überprüfen, ob die Push-Nachricht an den Push-Dienst gesendet wurde. Klicken Sie hierzu auf den Link **[!UICONTROL Anzeigen]** der entsprechenden Nachricht. Im Bericht wird die Anzahl erfolgreicher Sendevorgänge an den Push-Dienst in der Spalte **[!UICONTROL Veröffentlicht]** aufgeführt.

   >[!TIP]
   >
   >Die Push-Dienste garantieren nicht, dass eine Nachricht gesendet wird.

   Weitere Informationen zur Zuverlässigkeit der Dienste finden Sie in der entsprechenden Dokumentation:

   * **APNS**: [Servicequalität](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   * **FCM**: [Lebensdauer einer Nachricht](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)

## Warum werden meine Push-Nachrichten abgeschnitten oder erweitern sich nicht?

Bei einigen Android-Geräten müssen Sie `NotificationCompat.BigTextStyle` beim Anzeigen von Nachrichten verwenden.
