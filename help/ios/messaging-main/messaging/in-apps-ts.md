---
description: Diese Informationen helfen Ihnen bei der Fehlerbehebung von In-App-Nachrichten.
keywords: mobile
seo-description: Diese Informationen helfen Ihnen bei der Fehlerbehebung von In-App-Nachrichten.
seo-title: Fehlerbehebung von In-App-Nachrichten
solution: Marketing Cloud,Analytics
title: Fehlerbehebung von In-App-Nachrichten
topic: Metrics
uuid: 58533aa3-2eb2-4597-8525-77e4e5975e56
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 53%

---


# Fehlerbehebung von In-App-Nachrichten{#troubleshooting-in-app-messaging}

Diese Informationen helfen Ihnen bei der Fehlerbehebung von In-App-Nachrichten.

Wenn Sie alle Anforderungen für In-App-Nachrichten erfüllt haben, aber keine Nachrichten angezeigt werden, überprüfen Sie die folgenden Punkte:

## Enthält die Anwendung die neue Konfiguration und das neue SDK?

Verify that the SDK is version 4.2 or higher and correctly configured. Stellen Sie sicher, dass Ihre Konfiguration (heruntergeladene JSON-Datei) einen Abschnitt `Messages` oder einen Remote-Endpunkt „Nachrichten“ enthält, der vom dynamischen Tag-Management abgerufen werden kann.

## My full screen message in Android is not showing up. I am using the correct SDK, configuration, and my triggers are being met.

Did you update your manifest file to define the full screen activity?

## My local notification message in Android isn&#39;t working.

Stellen Sie sicher, dass der Broadcast-Empfänger für lokale Benachrichtigungen in Ihrer Manifestdatei deklariert ist. Weitere Informationen finden Sie in Schritt 2 des Abschnitts [In-App-Nachrichten aktivieren](/help/android/messaging-main/messaging/messaging.md).

## Ist die Nachricht „live“?

Check on the list view on the Manage In-App Message page in the Status column, and verify if it is live.

## Sehen Sie sich die Einstellungen *einmal anzeigen*, *immer anzeigen*, *offline anzeigen* auf der Registerkarte „Zielgruppe“ an.

Stellen Sie sicher, dass diese Einstellungen wie erforderlich festgelegt sind. Überprüfen Sie auf der Registerkarte **[!UICONTROL Zielgruppe]** die **[!UICONTROL Auslöser]**-Optionen, mit deren Hilfe Sie festlegen können, wie oft die Nachricht angezeigt wird.

## Wenn Sie Ereignis starten als Auslöser...

Ereignis wird nur bei einer neuen Sitzung ausgelöst. Weitere Informationen dazu, wann eine Sitzung beginnt, finden Sie in der Spalte `lifecycleTimeout` in der JSON-Konfigurationsdatei. Weitere Informationen finden Sie unter [ADBMobile JSON-Konfiguration](/help/ios/configuration/json-config/json-config.md).

## Ich habe meine Nachricht remote aktualisiert, aber meine App zeigt noch die alte Nachricht an.

Führen Sie eine der folgenden Aufgaben aus:

* Die Aktualisierung des Endpunkts entsprechend Ihrer neuen Definition im dynamischen Tag-Management kann einige Minuten dauern.

   Versuchen Sie es nach einiger Zeit erneut.

* Die Konfiguration wird nur bei einem Neustart aktualisiert. 
Wenn die Anwendung innerhalb des Sitzungs-Timeouts des Lebenszyklus neu gestartet wurde, wurde die neue Konfiguration möglicherweise nicht heruntergeladen.

   Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/ios/metrics.md).

## My image does not fit exactly into the space provided by the template.

The In-App Message full-screen template supports displaying an image from a remote server (Image URL) or from the app bundle (Bundled Image). Das Bild sollte in einem Standard-Bildformat vorliegen, wie z. B. JPG, GIF oder PNG.

Da Gerätebildschirme verschiedenste Abmessungen aufweisen, passt das Bild sehr wahrscheinlich nicht genau in den Platz der Vorlage. Die Vorlage zentriert das Bild, um die Bildmitte anzuzeigen, und schneidet Überschüssiges ab (Hochformat) bzw. lässt die Bildseiten verblassen (Querformat).

Im Folgenden finden Sie die genauen Positionierungs- und Größenregeln für jede Ausrichtung:

* **Hochformat**:
   * Eine Höhe von 195 px für Smartphones
   * Eine Höhe von 529 px für Tablets
   * Centered if the image width is smaller than the device width.
   * Cropped if the image width is greater than the device width.

* **Querformat**:
   * The image scaled to 100% of the height of the device.
   * The width is 75% of the device, with a fade out on the right.

If you have issues with the full-screen template, you can download and use the Custom HTML template. This template provides more flexibility for images and allows full control of the template.

## In-App-Nachrichten auf einem iPhone X werden nicht im Vollbildmodus angezeigt.

So zeigen Sie In-App-Nachrichten im Vollbildmodus auf einem iPhone X an:

1. Fügen Sie im Meta-Tag den Eintrag `viewport-fit=cover` hinzu.

   ```html
   <meta name="viewport" content="viewport-fit=cover">
   ```

1. Richten Sie die entsprechende Auffüllung im CSS für das oberste UI-Element ein, z. B.:

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
