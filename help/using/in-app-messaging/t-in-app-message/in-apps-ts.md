---
description: Diese Informationen unterstützen Sie bei der Lösung von Problemen mit In-App-Nachrichten.
keywords: mobile
solution: Experience Cloud Services,Analytics
title: Fehlerbehebung von In-App-Nachrichten
topic-fix: Metrics
uuid: 8813e8d8-bb1e-46ad-83cd-98ae68f73ce6
exl-id: 6be5beef-3bde-49f8-9ec0-c5d32bd43045
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 100%

---

# Fehlerbehebung von In-App-Nachrichten {#troubleshooting-in-app-messaging}

Diese Informationen unterstützen Sie bei der Lösung von Problemen mit In-App-Nachrichten.

Wenn Sie alle Anforderungen für In-App-Nachrichten erfüllt haben, aber keine Nachrichten angezeigt werden, überprüfen Sie die folgenden Punkte:

## Enthält die Anwendung die neue Konfiguration und das neue SDK?

* Stellen Sie sicher, dass Sie die SDK-Version 4.2 (oder höher) verwenden und dass sie ordnungsgemäß konfiguriert ist.

* Sie müssen sicherstellen, dass Ihre Konfiguration (die heruntergeladene JSON-Datei) den Abschnitt [Messaging](/help/using/in-app-messaging/in-app-messaging.md) oder den Remote-Endpunkt „Nachrichten“ enthält, damit dieser vom dynamischen Tag-Management abgerufen werden kann.

## Meine Vollbildnachricht in Android wird nicht angezeigt. Ich verwende das richtige SDK, die richtige Konfiguration und meine Auslöser werden erfüllt.

Haben Sie Ihre Manifestdatei aktualisiert, um die Aktivität im Vollbildmodus zu definieren?

## Meine lokale Benachrichtigung in Android funktioniert nicht.

Stellen Sie sicher, dass der lokale Empfänger für übertragene Benachrichtigungen in Ihrer Manifestdatei deklariert ist. Weitere Informationen finden Sie in Schritt 1 unter [In-App-Nachrichten](/help/android/messaging-main/messaging/messaging.md).

## Ist die Nachricht „live“?

Anhand der Listenansicht in der Spalte **[!UICONTROL Status]** auf der „Seite In-App-Nachricht verwalten“ können Sie überprüfen, ob die Nachricht live ist.

## Sehen Sie sich die Einstellungen *einmal anzeigen*, *immer anzeigen*, *offline anzeigen* auf der Seite „Zielgruppe“ an.

Stellen Sie sicher, dass die Einstellungen korrekt sind. Überprüfen Sie auf der Seite „Zielgruppe“ die Optionen auf der Registerkarte **[!UICONTROL Auslöser]**. Hier können Sie angeben, wie oft die Nachricht angezeigt wird.

## Bei Verwendung eines Ereignisstarts als Auslöser …

Ereignis wird nur bei einer neuen Sitzung ausgelöst. Informationen dazu, wann eine Sitzung beginnt, finden Sie unter  `lifecycleTimeout` in der [ADBMobile JSON-Konfigurationsdatei](/help/ios/configuration/json-config/json-config.md).

## Ich habe meine Nachricht remote aktualisiert in der Anwendung wird jedoch nach wie vor die alte Nachricht angezeigt.

Führen Sie eine der folgenden Aufgaben aus:

* Die Aktualisierung des Endpunkts entsprechend Ihrer neuen Definition im dynamischen Tag-Management kann einige Minuten dauern.

   Versuchen Sie es nach einiger Zeit erneut.

* Die Konfiguration wird nur bei einem Neustart aktualisiert.

   Wenn die Anwendung innerhalb des Sitzungs-Timeouts des Lebenszyklus neu gestartet wurde, wurde die neue Konfiguration möglicherweise nicht heruntergeladen.

## Mein Bild passt nicht genau in den von der Vorlage bereitgestellten Raum.

Die Vollbildvorlage „In-App-Nachricht“ unterstützt die Anzeige eines Bildes von einem Remoteserver (Bild-URL) oder vom App-Paket (Paketbild). Das Bild sollte in einem Standard-Bildformat vorliegen, wie z. B. JPG, GIF oder PNG.

Da Gerätebildschirme verschiedenste Abmessungen aufweisen, passt das Bild wahrscheinlich nicht genau in den Platz der Vorlage. In Vorlagen wird immer der Mittelpunkt des Bildes angezeigt und die Seiten werden zugeschnitten (Hochformat) oder ausgeblendet (Querformat), wenn das Bild nicht passt.

Im Folgenden finden Sie die genauen Positionierungs- und Größenregeln für jede Ausrichtung:

* **Hochformat**, wobei das Bild auf eine Höhe von 195 Pixel für das Telefon und 529 Pixel für das Tablett skaliert, wenn die Bildbreite kleiner als die Gerätebreite ist, zentriert, und beschnitten wird, wenn die Bildbreite größer als die Gerätebreite ist.

* **Querformat**, wobei das Bild auf 100 % der Höhe des Geräts skaliert wird, die Breite 75 % der Gerätebreite beträgt und rechts ausgeblendet wird.

   Wenn Sie Probleme mit der Vollbildvorlage haben, können Sie die benutzerdefinierte HTML-Vorlage herunterladen und verwenden. Diese benutzerdefinierte HTML-Vorlage bietet mehr Flexibilität für Bilder und ermöglicht die vollständige Steuerung der Vorlage.

## Meine Nachrichten spiegeln keine Änderungen/Aktualisierungen wider, die ich in der Benutzeroberfläche vorgenommen habe.

Das SDK ruft neue/aktualisierte Nachrichten zum Zeitpunkt des Starts des Lebenszyklus ab. Dies ist nur dann der Fall, wenn die App länger als der Wert für das Lebenszyklus-Timeout geschlossen / im Hintergrund ausgeführt und dann erneut geöffnet wird.

Führen Sie die folgenden Schritte aus:

1. Lassen Sie die URL Ihrer Nachrichten in Ihrer Konfigurationsdatei über Curl laufen, um zu überprüfen, ob die Remote-Nachricht aktualisiert wird (z. B. `curl "https://assets.adobedtm.com/b213090c5204bf94318f4ef0539a38b487d10368/scripts/satellite-542c62859662383b1a0008f4.json"`)
1. Schließen Sie die Anwendung.
1. Warten Sie so lange, bis der in der Konfigurationsdatei angegebene Wert `lifecycleTimeout` überschritten ist.
1. Öffnen Sie die App, navigieren Sie zu der Stelle, an der die Nachricht angezeigt werden soll, und überprüfen Sie, ob sie aktualisiert wurde.
