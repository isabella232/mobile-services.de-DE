---
description: Mit der iBeacon-Verfolgung können Sie Mikrostandorte mithilfe von iBeacon und Bluetooth Low Energy messen und anvisieren.
seo-description: Mit der iBeacon-Verfolgung können Sie Mikrostandorte mithilfe von iBeacon und Bluetooth Low Energy messen und anvisieren.
seo-title: iBeacon-Verfolgung
solution: Experience Cloud,Analytics
title: iBeacon-Verfolgung
topic: Developer and implementation
uuid: 390883db-027e-4d12-8a16-86d514579db1
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '200'
ht-degree: 100%

---


# iBeacon-Verfolgung {#ibeacon-tracking}

Mit der iBeacon-Verfolgung können Sie Mikrostandorte mithilfe von iBeacon und Bluetooth Low Energy messen und anvisieren.

Die folgenden Beacon-Daten werden an Analytics und Target gesendet, wenn `trackBeacon` aufgerufen wird:

* `a.beacon.uuid`: Näherungs-UUID des Beacons
* `a.beacon.major`: Hauptnummer des Beacons, beispielsweise eine Speichernummer
* `a.beacon.minor`: Nebennummer des Beacons, beispielsweise eine eindeutige Nummer in einem Speicher
* `a.beacon.prox`: Die folgenden Werte geben an, wie nah sich der Benutzer am Beacon befindet:

   * `0` ist unbekannt
   * `1` ist unmittelbar
   * `2` ist nahe
   * `3` ist entfernt

## iBeacons verfolgen {#section_FC3F213545944A468B1E6D5D5C8E2F1F}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Konfigurationsdatei zum Projekt hinzufügen* im Abschnitt [Grundlegende Implementierung und Lebenszyklus](/help/ios/getting-started/dev-qs.md).
1. Importieren Sie die Bibliothek:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Rufen Sie `trackBeacon` auf, wenn sich ein Gerät in Reichweite eines Beacons befindet:

   ```objective-c
   [ADBMobile trackBeacon:beacon data:nil];
   ```

1. Deaktivieren Sie den aktuellen Beacon, wenn sich ein Benutzer nicht mehr in Reichweite zum Beacon befindet:

   ```objective-c
   [ADBMobile trackingClearCurrentBeacon];
   ```

## Zusätzliche Daten senden {#section_3EBE813E54A24F6FB669B2478B5661F9}

Zusätzlich zum zeitlich festgelegten Aktionsnamen können Sie bei jedem Verfolgungsaktionsaufruf zusätzliche Kontextdaten senden:

```objective-c
[ADBMobile trackBeacon:beacon data:@{@"myapp.ImageLiked" : imageName}];
```

Die Kontextdatenwerte müssen benutzerdefinierten Variablen zugeordnet werden:

![](assets/map-variable-context-ltv.png)

## Beispiele {#section_9749238BCBC148998CB18E97D7670D19}

```objective-c
- (void)locationManager:(CLLocationManager *)manager didRangeBeacons:(NSArray *)beacons inRegion:(CLBeaconRegion *)region { 
    if (beacons.count > 0) { 
        CLBeacon *beacon = beacons[0]; 
        // Adobe - track when in range of a beacon 
        [ADBMobile trackBeacon:beacon data:@{@"sampleContextData" : @"sampleContextDataVal"}]; 
    } 
} 
 
// When the user leaves the proximity of the beacon, clear the current beacon 
[ADBMobile trackingClearCurrentBeacon];
```

