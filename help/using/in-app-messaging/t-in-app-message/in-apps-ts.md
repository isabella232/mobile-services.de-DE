---
description: Diese Informationen unterstützen Sie bei der Lösung von Problemen mit In-App-Nachrichten.
keywords: mobile
seo-description: Diese Informationen unterstützen Sie bei der Lösung von Problemen mit In-App-Nachrichten.
seo-title: Fehlerbehebung von In-App-Nachrichten
solution: Experience Cloud,Analytics
title: Fehlerbehebung von In-App-Nachrichten
topic: Metrics
uuid: 8813e8d8-bb1e-46ad-83cd-98ae68f73ce6
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 58%

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

Anhand der Listenansicht in der Spalte **[!UICONTROL Status]** auf der Seite In-App-Nachricht verwalten können Sie überprüfen, ob die Nachricht live ist.

## Sehen Sie sich die Einstellungen *einmal anzeigen*, *immer anzeigen*, *offline anzeigen* auf der Seite „Zielgruppe“ an.

Stellen Sie sicher, dass die Einstellungen korrekt sind. Überprüfen Sie auf der Seite Zielgruppe die Optionen auf der Registerkarte **[!UICONTROL Auslöser]**. Hier können Sie angeben, wie oft die Nachricht angezeigt wird.

## Bei Verwendung eines Ereignisstarts als Auslöser …

Ereignis wird nur bei einer neuen Sitzung ausgelöst. Informationen dazu, wann eine Sitzung beginnt, finden Sie unter `lifecycleTimeout` in der [ADBMobile JSON-Konfigurationsdatei](/help/ios/configuration/json-config/json-config.md).

## Ich habe meine Nachricht remote aktualisiert in der Anwendung wird jedoch nach wie vor die alte Nachricht angezeigt.

Führen Sie eine der folgenden Aufgaben aus:

* Das dynamische Tag-Management kann einige Minuten dauern, bis sein Endpunkt mit Ihrer neuen Definition aktualisiert wird.

   Gib es etwas Zeit und versuche es erneut.

* Die Konfiguration wird nur bei einem Neustart aktualisiert.

   Wenn die App während des Lebenszyklussitzungs-Timeouts neu gestartet wurde, wurde Ihre neue Konfiguration möglicherweise nicht heruntergeladen.

## Mein Bild passt nicht genau in den von der Vorlage bereitgestellten Raum.

Die Vollbildvorlage &quot;In-App-Nachricht&quot;unterstützt das Anzeigen eines Bildes von einem Remote-Server (Bild-URL) oder vom App-Bundle (Bundle-Bild). Das Bild sollte in einem Standardbildformat vorliegen, z. B. JPG, GIF oder PNG.

Da Gerätebildschirme viele verschiedene Abmessungen haben, passt das Bild wahrscheinlich nicht genau in den von der Vorlage bereitgestellten Raum. Die Vorlage konzentriert sich immer darauf, den Mittelpunkt des Bilds anzuzeigen und die Seiten zu beschneiden (Hochformat) oder (Querformat), wenn das Bild nicht passt.

Im Folgenden finden Sie die genauen Positionierungs- und Größenregeln für jede Ausrichtung:

* **Hochformat**, bei dem das Bild für Smartphones auf eine Höhe von 195 px und für Tablets auf 529 px skaliert wird, zentriert, wenn die Bildbreite kleiner als die Gerätegröße ist, und abgeschnitten, wenn die Bildbreite größer als die Gerätebreite ist.

* **Querformat**, bei dem das Bild auf 100 % der Gerätehöhe skaliert wird, die Breite 75 % des Geräts beträgt und das Bild rechts ausgeblendet wird.

   Wenn Sie Probleme mit der Vollbildvorlage haben, können Sie die benutzerdefinierte HTML-Vorlage herunterladen und verwenden. Die benutzerdefinierte HTML-Vorlage bietet mehr Flexibilität bei Bildern und ermöglicht die vollständige Steuerung der Vorlage.

## Meine Nachrichten spiegeln keine Änderungen/Aktualisierungen wider, die ich in der Benutzeroberfläche vorgenommen habe.

Das SDK ruft neue/aktualisierte Nachrichten zum Zeitpunkt des Lebenszyklusstarts ab. Dies ist nur der Fall, wenn die Anwendung für einen höheren Lebenszyklustimeout-Wert geschlossen bzw. hinterlegt und dann erneut geöffnet wird.

Führen Sie die folgenden Schritte aus:

1. Lassen Sie die URL Ihrer Nachrichten in Ihrer Konfigurationsdatei über Curl laufen, um zu überprüfen, ob die Remote-Nachricht aktualisiert wird (z. B. `curl "https://assets.adobedtm.com/b213090c5204bf94318f4ef0539a38b487d10368/scripts/satellite-542c62859662383b1a0008f4.json"`)
1. Schließen Sie die Anwendung.
1. Warten Sie so lange, bis der in der Konfigurationsdatei angegebene Wert `lifecycleTimeout` überschritten ist.
1. Öffnen Sie die App, navigieren Sie zu der Stelle, an der die Nachricht angezeigt werden soll, und überprüfen Sie, ob sie aktualisiert wurde.