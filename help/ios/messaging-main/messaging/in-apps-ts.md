---
description: Diese Informationen helfen Ihnen bei der Fehlerbehebung von In-App-Nachrichten.
keywords: mobile
seo-description: Diese Informationen helfen Ihnen bei der Fehlerbehebung von In-App-Nachrichten.
seo-title: Fehlerbehebung von In-App-Nachrichten
solution: Marketing Cloud, Analytics
title: Fehlerbehebung von In-App-Nachrichten
topic: Metriken
uuid: 58533 aa 3-2 eb 2-4597-8525-77 e 4 e 5975 e 56
translation-type: tm+mt
source-git-commit: 1154bab39b5215e00d47ad8e66caeec15e4e98de

---


# Troubleshooting in-app messaging{#troubleshooting-in-app-messaging}

Diese Informationen helfen Ihnen bei der Fehlerbehebung von In-App-Nachrichten.

Wenn Sie alle Anforderungen für In-App-Nachrichten erfüllt haben, die Nachrichten jedoch nicht angezeigt werden, sollten Sie die folgenden Elemente überprüfen:

## Enthält die Anwendung die neue Konfiguration und das neue SDK?

Stellen Sie sicher, dass Sie das SDK, Version 4.2 oder höher verwenden und das SDK ordnungsgemäß konfiguriert ist. Ensure that you have a `Messages` section in your configuration (downloaded JSON file), or have a Messages remote endpoint, so that it can be retrieved from dynamic tag management.

## Meine Vollbildnachricht in Android wird nicht angezeigt. Ich verwende das richtige SDK, die richtige Konfiguration und die Auslösebedingungen sind erfüllt.

Haben Sie die Vollbildaktivität in Ihrer Manifestdatei definiert?

## Meine lokale Benachrichtigung in Android funktioniert nicht.

Stellen Sie sicher, dass der Broadcast-Empfänger für lokale Benachrichtigungen in Ihrer Manifestdatei deklariert ist. For more information, see step 2 in [Enabling In-App Messages](/help/android/messaging-main/messaging/messaging.md).

## Ist die Nachricht „live“?

Prüfen Sie in der Listenansicht der Seite „In-App-Nachrichten verwalten“ in der Spalte „Status“, ob die Benachrichtigung „live“ ist.

## Sehen Sie sich einmal ** an, *zeigen Sie einmal an*, *zeigen Sie Offline* -Einstellungen auf der Registerkarte "Zielgruppe" an.

Stellen Sie sicher, dass diese Einstellungen wie erforderlich festgelegt sind. Überprüfen Sie auf der Registerkarte **[!UICONTROL Zielgruppe]** die **Auslöser]-Optionen, mit deren Hilfe Sie festlegen können, wie oft die Nachricht angezeigt wird.[!UICONTROL **

## Bei Verwendung eines Ereignisstarts als Auslöser...

Ereignis wird nur bei einer neuen Sitzung ausgelöst. For more information about when a session begins, see the `lifecycleTimeout` row in the JSON Config file. Weitere Informationen finden Sie unter [adbmobile JSON-Konfiguration](/help/ios/configuration/json-config/json-config.md).

## Ich habe meine Nachricht remote aktualisiert; in der Anwendung wird jedoch nach wie vor die alte Nachricht angezeigt.

Führen Sie eine der folgenden Aufgaben durch:

* Die Aktualisierung des Endpunkts entsprechend Ihrer neuen Definition im dynamischen Tag-Management kann einige Minuten dauern.

   Versuchen Sie es nach einiger Zeit erneut.

* Die Konfiguration wird nur bei einem Neustart aktualisiert.
Wenn die Anwendung innerhalb des Sitzungs-Timeouts des Lebenszyklus neu gestartet wurde, wurde die neue Konfiguration möglicherweise nicht heruntergeladen.

   Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/ios/metrics.md).

## Mein Bild passt nicht genau in den in der Vorlage vorgesehenen Platz.

Die Vollbildvorlage für In-App-Nachrichten unterstützt die Anzeige eines Bildes entweder über einen Remote-Server (Bild-URL) oder über das App-Bundle (Bundle-Bild). Das Bild sollte in einem Standard-Bildformat vorliegen, wie z. B. JPG, GIF oder PNG.

Da Gerätebildschirme verschiedenste Abmessungen aufweisen, passt das Bild sehr wahrscheinlich nicht genau in den Platz der Vorlage. Die Vorlage zentriert das Bild, um die Bildmitte anzuzeigen, und schneidet Überschüssiges ab (Hochformat) bzw. lässt die Bildseiten verblassen (Querformat).

Im Folgenden finden Sie die genauen Positionierungs- und Größenregeln für jede Ausrichtung:

* **Hochformat**:
   * Eine Höhe von 195 px für Smartphones
   * Eine Höhe von 529 px für Tablets
   * Wird zentriert, wenn das Bild breiter ist als der Bildschirm.
   * Wird abgeschnitten, wenn das Bild schmaler ist als der Bildschirm.

* **Querformat**:
   * Das Bild wird auf 100 % der Bildschirmhöhe skaliert.
   * Die Breite beträgt 75 % des Bildschirms und die rechte Seite verblasst.

Wenn Sie Probleme mit der Vollbildvorlage haben, können Sie die benutzerdefinierte HTML-Vorlage herunterladen und verwenden. Diese Vorlage bietet mehr Flexibilität in Bezug auf Bilder und gibt Ihnen volle Kontrolle über die Vorlage.

## In-App-Nachrichten werden auf einem iPhone X nicht im Vollbildmodus angezeigt.

Gehen Sie wie folgt vor, um sicherzustellen, dass In-App-Nachrichten auf einem iPhone X angezeigt werden:

1. Add `viewport-fit=cover` in the meta tag.

   ```html
   <meta name="viewport" content="viewport-fit=cover">
   ```

1. Definieren Sie für das oberste Element der Benutzeroberfläche die passenden Werte für den Innenabstand (Padding), z. B.:

   ```html
   topelement {
     padding-top:20px;
     /*Status bar height on iOS 11.0*/
     padding-top:constant(safe-area-inset-top);
     /*Status bar height on iOS 11+ */
     padding-top:env(safe-area-inset-top);
     } 
   ```

   Diese Einstellungen verhindern, dass die Elemente der Benutzeroberfläche mit der Statusleiste kollidieren.
