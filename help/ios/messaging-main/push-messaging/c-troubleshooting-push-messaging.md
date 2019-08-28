---
description: Mithilfe dieser Informationen können Probleme mit Push-Nachrichten behoben werden.
keywords: mobile
seo-description: Mithilfe dieser Informationen können Probleme mit Push-Nachrichten behoben werden.
seo-title: Fehlerbehebung für Push-Nachrichten
solution: Marketing Cloud, Analytics
title: Fehlerbehebung für Push-Nachrichten
topic: Metriken
uuid: 87 d 7 dcb 6-82 a 8-46 e 3-a 6 ed -7 f 895 a 22 f 2 af
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Troubleshooting push messaging {#troubleshooting-push-messaging}

Mithilfe dieser Informationen können Probleme mit Push-Nachrichten behoben werden.

## Warum gibt es beim Senden von Push-Nachrichten manchmal Verzögerungen?

Folgende Verzögerungen können bei Push-Nachrichten für Mobile Services auftreten:

* **Warten auf einen Analytics-Treffer**

   Jede Report Suite verfügt über eine Einstellung, die festlegt, wann eingehende Analytics-Treffer verarbeitet werden sollen. Der Standardwert liegt bei 1 Stunde zur vollen Stunde. Die eigentliche Verarbeitung von Analytics-Treffern kann bis zu 30 Minuten dauern, in der Regel sind es jedoch 15 bis 20 Minuten.

   Angenommen, eine Report Suite verarbeitet Treffer stündlich. Berücksichtigt man nun die Verarbeitungszeit von maximal 30 Minuten, kann es bis zu 90 Minuten dauern, bis ein eingehender Treffer für eine Push-Nachricht verfügbar ist. Wenn ein Benutzer die App um 9:01 Uhr gestartet hat, wird der Treffer auf der Mobile Services-Benutzeroberfläche als neuer Unique User zwischen 10:15 und 10:30 Uhr angezeigt.

* **Warten auf Push-Dienst**

   Der Push-Dienst (APNS oder GCM) versendet die Nachricht möglicherweise nicht sofort. Dies kann in Ausnahmefällen 5 bis 10 Minuten in Anspruch nehmen. Auf der Seite Nachrichten können Sie überprüfen, ob die Push-Nachricht an den Push-Dienst gesendet wurde. Klicken Sie hierzu auf den Link Anzeigen der entsprechenden Nachricht. Im Bericht wird die Anzahl erfolgreicher Sendevorgänge an den Push-Dienst in der Spalte Veröffentlicht aufgeführt.

   >[!TIP]
   >
   >Die Push-Dienste garantieren nicht, dass eine Nachricht gesendet wird. Weitere Informationen zur Zuverlässigkeit der Dienste finden Sie in der entsprechenden Dokumentation:
   >
   >* **APNS**: [Servicequalität](https://developer.apple.com/documentation/usernotifications)
      >
      >
   * **GCM**: [Lebensdauer einer Nachricht](https://developers.google.com/cloud-messaging/concept-options)


## Wie kann ich mein Zertifikat für den Apple-Push-Dienst verlängern?

Zum Senden von Push-Nachrichten ist ein gültiges Zertifikat für den Push-Dienst erforderlich. Mobile Services benachrichtigt Sie, wenn Ihr Zertifikat kurz vor dem Ablauf steht oder abgelaufen ist. Wenn diese Benachrichtigung angezeigt wird, sollten Sie die folgenden Schritte durchführen, um Ihr Zertifikat zu verlängern:

1. Klicken Sie auf **[!UICONTROL App-Einstellungen verwalten]**.
2. Blättern Sie zum Löschen des aktuellen Zertifikats zu **[!UICONTROL Push-Dienste]** und klicken Sie dann auf **[!UICONTROL Löschen]**.
3. Konfigurieren und testen Sie ein neues Zertifikat.

   Weitere Informationen finden Sie unter [Voraussetzungen für die Aktivierung der Push-Benachrichtigung](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md).

4. Klicken Sie auf **[!UICONTROL Speichern]**.

## Warum kann ich meine Push-Nachrichten in einem iOS-Simulator nicht sehen?

iOS-Simulatoren unterstützen Push-Nachrichten nicht.
