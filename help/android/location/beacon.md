---
description: Die Beacon-Verfolgung ermöglicht es Ihnen, Mikrostandorte mithilfe von iBeacon und Bluetooth Low Energy zu messen und anzusprechen.
keywords: android;library;mobile;sdk
seo-description: Die Beacon-Verfolgung ermöglicht es Ihnen, Mikrostandorte mithilfe von iBeacon und Bluetooth Low Energy zu messen und anzusprechen.
seo-title: Beacon-Verfolgung
solution: Marketing Cloud,Analytics
title: Beacon-Verfolgung
topic: Entwickler und Implementierung
uuid: 16c1d267-85f4-4a6a-a6d3-d6ffb0f80b29
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Beacon-Verfolgung {#beacon-tracking}

Die Beacon-Verfolgung ermöglicht es Ihnen, Mikrostandorte mithilfe von iBeacon und Bluetooth Low Energy zu messen und anzusprechen.

Die folgenden Beacon-Daten werden an Analytics und Target gesendet, wenn `trackBeacon` aufgerufen wird:

* `a.beacon.uuid` - ProximityUUID of the beacon
* `a.beacon.major` – Major-Wert des Beacons (z. B. Store-Nummer)
* `a.beacon.minor` – Minor-Wert des Beacons (z. B. die eindeutige Kennung innerhalb eines Stores)
* `a.beacon.prox`: Die Werte 0–3 geben an, wie nah sich der Benutzer am Beacon befindet.

Diese Werte haben folgende Bedeutung:

* 0 = unbekannt
* 1 = unmittelbar
* 2 = nah
* 3 = entfernt

Diese Beacon-Daten werden in Variablen für mobile Lösungen erfasst.

## Tracking-Beacons {#section_FC3F213545944A468B1E6D5D5C8E2F1F}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK- und Konfigurationsdatei zu Ihrer IntelliJ-IDEA- oder Eclipse-Projekt* in der [Core-Implementierung und im Lebenszyklus](/help/android/getting-started/dev-qs.md)hinzufügen.

1. Importieren Sie die Bibliothek:

   ```java
   import com.adobe.mobile.*;
   ```

1. Erfassen Sie den Beacon-Standort.

   Je nach Hersteller des Beacons sind für das Scannen von Bluetooth LE-Beacons verschiedene Bibliotheken von Drittanbietern verfügbar.
1. Nachdem die Beacon-Informationen abgerufen wurden, verwenden Sie den folgenden Anruf, um den Standort zu verfolgen:

   ```java
   // assumed that the following variables will have been retrieved by the 3rd party beacon library 
   String beaconUUID; 
   String major; 
   String minor; 
   Analytics.BEACON_PROXIMITY proximity;  
   // BEACON_PROXIMITY is an enum available in the SDK. Number 0-3 representing how close the 
   // user is to the beacon. 0 unknown, 1 immediate, 2 near, 3 far.  
   Analytics.trackBeacon(beaconUUID, major, minor, proximity, null);
   ```

1. Wenn der Benutzer die Nähe des Beacons verlässt, löschen Sie das aktuelle Beacon:

   ```java
   Analytics.clearBeacon();
   ```

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Zusätzlich zu den Beacon-Daten können Sie mit jedem `trackBeacon`-Aufruf weitere Kontextdaten senden:

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackBeacon(beaconUUID, major, minor, proximity, cdata);
```

Context data values must be mapped to custom variables in the Adobe Mobile services:

![](assets/map-variable-context-ltv.png)

