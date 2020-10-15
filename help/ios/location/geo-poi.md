---
description: Mit dem Geostandort können Sie Standortdaten unter Verwendung von Breiten-/Längengrad und der vordefinierten Zielpunkte in Ihrer iOS-App messen.
seo-description: Mit dem Geostandort können Sie Standortdaten unter Verwendung von Breiten-/Längengrad und der vordefinierten Zielpunkte in Ihrer iOS-App messen.
seo-title: Geostandort und Zielpunkte
solution: Experience Cloud,Analytics
title: Geostandort und Zielpunkte
topic: Developer and implementation
uuid: c800ec85-a33f-425d-b28f-bfe8bf229ae8
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '591'
ht-degree: 100%

---


# Geostandort und Zielpunkte {#geo-location-and-points-of-interest}

Mit dem Geostandort können Sie Standortdaten unter Verwendung von Breiten-/Längengrad und der vordefinierten Zielpunkte in Ihrer iOS-App messen.

Jeder `trackLocation`-Aufruf sendet Folgendes:

* Breitengrad, Längengrad und Standort in einem Zielpunkt (Point of Interest, POI), der in Adobe Mobile Services definiert ist.

   Diese Informationen werden für die automatische Berichterstellung an die Variablen der mobilen Lösung übergeben.

* Entfernung vom Zentrum und Genauigkeit werden als Kontextdaten weitergegeben.

   Diese Variablen werden nicht automatisch erfasst. Sie müssen diese Variablen für Kontextdaten mithilfe der Anweisungen im Abschnitt *Zusätzliche Daten senden* unten zuordnen.

## Dynamische POI-Aktualisierungen {#section_3747B310DD5147E2AAE915E762997712}

Ab Version 4.2 sind POIs auf der Adobe Mobile-Oberfläche definiert und werden dynamisch mit der App-Konfigurationsdatei synchronisiert. Diese Synchronisation erfordert die Einstellung `analytics.poi` in der Datei `ADBMobile.json`:

```js
“analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”,
```

Weitere Informationen finden Sie unter [ADBMobile JSON-Konfiguration](/help/ios/configuration/json-config/json-config.md).

Falls diese nicht konfiguriert ist, muss eine aktualisierte Version der Datei `ADBMobile.json` heruntergeladen und zu Ihrer App hinzugefügt werden. Weitere Informationen und Anweisungen finden Sie unter *SDK und Testwerkzeuge herunterladen* im Abschnitt [Vorbereitung](/help/ios/getting-started/requirements.md).

## Geostandorte und Zielpunkte verfolgen {#section_B1616E400A7548F9A672F97FEC75AE27}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Konfigurationsdatei zum Projekt hinzufügen* im Abschnitt [Grundlegende Implementierung und Lebenszyklus](/help/ios/getting-started/dev-qs.md).
1. Importieren Sie die Bibliothek:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Rufen Sie `trackLocation` auf, um den aktuellen Standort zu verfolgen:

   ```objective-c
   CLLocation *currentLocation = location; 
   [ADBMobile trackLocation: currentLocation data: nil]; 
   ```

   >[!TIP]
   >
   >Sie können `trackLocation` jederzeit aufrufen.

   Um den Standort zu bestimmen, der an den `trackLocation`-Aufruf weitergeleitet wird, siehe [Standort des Benutzers ermitteln](https://developer.apple.com/Library/ios/documentation/UserExperience/Conceptual/LocationAwarenessPG/CoreLocation/CoreLocation.html).

Wenn festgestellt wird, dass sich der Standort in einem definierten POI-Radius befindet, wird zusätzlich eine `a.loc.poi`-Kontextdatenvariable mit dem Treffer `trackLocation` gesendet und in den Standortberichten als ein POI gemeldet. Außerdem wird eine `a.loc.dist`-Kontextvariable gesendet, die den Abstand von den definierten Koordinaten in Metern enthält.

## Zusätzliche Daten senden {#section_3EBE813E54A24F6FB669B2478B5661F9}

Zusätzlich zum Standortnamen können Sie mit jedem trackLocation-Aufruf zusätzliche Kontextdaten senden:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"GPS" forKey:@"myapp.location.LocationSource"]; 
[ADBMobile trackLocation: currentLocation data:contextData];
```

Die Kontextdatenwerte müssen benutzerdefinierten Variablen zugeordnet werden:

![](assets/map-location-context-data.png)

## Standort-Kontextdaten {#section_FFB71E6653F9410A89CC6ACC0C9164A9}

Die Längen- und Breitengrade werden jeweils mit drei verschiedenen Kontextdatenparametern gesendet, wobei jeder Parameter einen anderen Genauigkeitsgrad für insgesamt sechs Kontextdatenparameter darstellt.

Beispielsweise stellen die Koordinaten lat = 40,93231, lon = -111,93152 einen Standort mit einer Genauigkeit von 1 m dar. Dieser Standort wird entsprechend der Genauigkeit auf die folgenden Variablen aufgeteilt:

* `a.loc.lat.a` = 040,9
* `a.loc.lat.b` = 32
* `a.loc.lat.c` = 31
* `a.loc.lon.a` = -111,9
* `a.loc.lon.b` = 31
* `a.loc.lon.c` = 52

Einige Genauigkeitsstufen werden in Abhängigkeit der Genauigkeit des aktuellen Standorts ggf. als „00“ angezeigt. Wenn der Standort beispielsweise auf bis zu 100 m genau ist, werden `a.loc.lat.c` und `a.loc.lon.c` mit „00“ aufgefüllt.

## Weitere Informationen {#section_931AC1E0D88147E29FE1B6E3CC1E9550}

Beachten Sie die folgenden Informationen:

* Eine `trackLocation`-Anfrage sendet das Äquivalent eines `trackAction`-Aufrufs.

* POIs werden nicht als Bestandteil von normalen `trackAction`- und `trackState` Aufrufen weitergegeben. Daher müssen Sie einen `trackLocation`-Aufruf verwenden, um POIs zu verfolgen.

* `trackLocation` muss so oft wie nötig aufgerufen werden, um Standorte und POIs zu verfolgen.

   Sie sollten `trackLocation` aufrufen, wenn die App gestartet wird und dann in Abhängigkeit der Anforderungen der Anwendung bei Bedarf.

* POIs werden nur dann aufgefüllt, nachdem sie in der App-Konfigurationsdatei aufgefüllt wurden.

   Sie werden nicht auf historische `trackLocation`-Aufrufe angewendet, die zuvor gesendet wurden.
* `trackLocation`-Aufrufe unterstützen das Senden zusätzlicher Kontextdaten – ähnlich wie `trackAction`-Aufrufe.

* Wenn sich die Radien zweier POIs überschneiden, wird der erste POI verwendet, der den aktuellen Standort enthält.

   Wenn sich Ihre POIs überschneiden, sollten Sie die POIs in der Reihenfolge der größten bis zur niedrigsten Granularität auflisten, um sicherzustellen, dass der POI mit der größten Granularität gemeldet wird.

