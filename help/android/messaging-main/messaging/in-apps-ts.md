---
description: Diese Informationen helfen Ihnen bei der Fehlerbehebung von In-App-Nachrichten.
keywords: mobile
solution: Experience Cloud Services,Analytics
title: Fehlerbehebung bei In-App-Nachrichten
topic-fix: Metrics
uuid: 39c3a21d-92c2-4004-b00f-99b6f91d3696
exl-id: 6c7d97ed-3b0a-48ff-b761-1485aea5e96d
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 100%

---

# Fehlerbehebung bei In-App-Nachrichten {#troubleshooting-in-app-messaging}

Diese Informationen helfen Ihnen bei der Fehlerbehebung von In-App-Nachrichten.

Wenn Sie alle Anforderungen für In-App-Nachrichten erfüllt haben, aber keine Nachrichten angezeigt werden, überprüfen Sie die folgenden Punkte:

## Enthält die Anwendung die neue Konfiguration und das neue SDK?

Stellen Sie sicher, dass Ihre Konfiguration (heruntergeladene JSON-Datei) einen Abschnitt [In-App-Nachrichten](/help/android/messaging-main/messaging/messaging.md) oder einen Remote-Endpunkt „Nachrichten“ enthält, der vom dynamischen Tag-Management abgerufen werden kann.

## Meine Vollbildnachricht in Android wird nicht angezeigt. Ich verwende das richtige SDK, die richtige Konfiguration und meine Auslöser werden erfüllt.

Haben Sie Ihre Manifestdatei aktualisiert, um die Aktivität im Vollbildmodus zu definieren?

## Meine lokale Benachrichtigung in Android funktioniert nicht.

Stellen Sie sicher, dass der Broadcast-Empfänger für lokale Benachrichtigungen in Ihrer Manifestdatei deklariert ist. Weitere Informationen finden Sie in Schritt 2 des Abschnitts *In-App-Nachrichten aktivieren* in [In-App-Nachrichten](/help/android/messaging-main/messaging/messaging.md).

## Ist die Nachricht „live“?

Um sicherzustellen, dass die Nachricht „live“ ist, überprüfen Sie auf der Seite „In-App-Nachrichten verwalten“ in der Spalte **[!UICONTROL Status]** die Liste der Nachrichten.

## Sehen Sie sich die Einstellungen *einmal anzeigen*, *immer anzeigen*, *offline anzeigen* auf der Registerkarte „Zielgruppe“ an.

Stellen Sie sicher, dass diese Einstellungen wie erforderlich festgelegt sind. Überprüfen Sie auf der Registerkarte **[!UICONTROL Zielgruppe]** die **[!UICONTROL Auslöser]**-Optionen, mit deren Hilfe Sie festlegen können, wie oft die Nachricht angezeigt wird.

## Bei Verwendung eines Ereignisstarts als Auslöser

Ereignis wird nur bei einer neuen Sitzung ausgelöst. Weitere Informationen dazu, wann eine Sitzung beginnt, finden Sie in der Spalte `lifecycleTimeout` unter [JSON-Konfiguration](/help/android/configuration/json-config/json-config.md).

## Ich habe meine Nachricht remote aktualisiert, in der Anwendung wird jedoch nach wie vor die alte Nachricht angezeigt.

Beachten Sie die folgenden Informationen:

* Die Aktualisierung des Endpunkts entsprechend Ihrer neuen Definition im dynamischen Tag-Management kann einige Minuten dauern. Versuchen Sie es nach einiger Zeit erneut.
* Die Konfiguration wird nur bei einem Neustart aktualisiert. Wenn die Anwendung innerhalb des Sitzungs-Timeouts des Lebenszyklus neu gestartet wurde, wurde die neue Konfiguration möglicherweise nicht heruntergeladen.

Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/android/metrics.md).

## Mein Bild passt nicht genau in den von der Vorlage bereitgestellten Raum.

Die Vollbildvorlage „In-App-Nachricht“ unterstützt die Anzeige eines Bildes von einem Remoteserver (Bild-URL) oder vom App-Paket (Paketbild). Das Bild sollte in einem Standard-Bildformat vorliegen, wie z. B. JPG, GIF oder PNG. Da Gerätebildschirme verschiedenste Abmessungen aufweisen, passt das Bild sehr wahrscheinlich nicht genau in den Platz der Vorlage. Die Vorlage zentriert das Bild, um die Bildmitte anzuzeigen, und schneidet Überschüssiges ab (Hochformat) bzw. lässt die Bildseiten verblassen (Querformat).

Im Folgenden finden Sie die genauen Positionierungs- und Größenregeln für jede Ausrichtung:

* **Hochformat**
   * Eine Höhe von 195 px für Smartphones.
   * Eine Höhe von 529 px für Tablets.
   * Zentriert, wenn die Bildbreite geringer als die Gerätebreite ist.
   * Zugeschnitten, wenn die Bildbreite größer als die Gerätebreite ist.

* **Querformat**
   * Das Bild wurde auf 100 % der Höhe des Geräts skaliert.
   * Die Breite beträgt 75 % des Geräts, wobei sich eine Ausblendung auf der rechten Seite befindet.
   Wenn Sie Probleme mit der Vollbildvorlage haben, können Sie die benutzerdefinierte HTML-Vorlage herunterladen und verwenden. Diese Vorlage bietet mehr Flexibilität für Bilder und ermöglicht die vollständige Steuerung der Vorlage.
