---
description: Mit dem Geo-Standort können Sie Standortdaten unter Verwendung von Breiten-/Längengrad und der vordefinierten Zielpunkte in Ihrer iOS-App messen.
seo-description: Mit dem Geo-Standort können Sie Standortdaten unter Verwendung von Breiten-/Längengrad und der vordefinierten Zielpunkte in Ihrer iOS-App messen.
seo-title: Geografische Standort und Zielpunkte
solution: Marketing Cloud, Analytics
title: Geografische Standort und Zielpunkte
topic: Entwickler und Implementierung
uuid: c 800 ec 85-a 33 f -425 d-b 28 f-bfe 8 bf 229 ae 8
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Geo-location and points of interest {#geo-location-and-points-of-interest}

Mit dem Geo-Standort können Sie Standortdaten unter Verwendung von Breiten-/Längengrad und der vordefinierten Zielpunkte in Ihrer iOS-App messen.

Jeder `trackLocation`-Aufruf sendet Folgendes:

* Breitengrad, Längengrad und Standort in einem Zielpunkt (Point of Interest, POI), der in Adobe Mobile Services definiert ist.

   Diese Informationen werden zur automatischen Meldung an die Variablen für die mobile Lösung übergeben.

* Entfernung vom Zentrum und Präzision in Form von Kontextdaten.

   Diese Variablen werden nicht automatisch erfasst. You must map these context data variables by using the instructions in *Sending Additional Data* section below.

## Dynamische POI-Aktualisierungen {#section_3747B310DD5147E2AAE915E762997712}

Ab Version 4.2 sind POIs auf der Adobe Mobile-Oberfläche definiert und werden dynamisch mit der App-Konfigurationsdatei synchronisiert. This synchronization requires an `analytics.poi` setting in the `ADBMobile.json` file:

```js
“analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”,
```

Weitere Informationen finden Sie unter [adbmobile JSON-Konfiguration](/help/ios/configuration/json-config/json-config.md).

Falls diese nicht konfiguriert ist, muss eine aktualisierte Version der Datei `ADBMobile.json` heruntergeladen und zu Ihrer App hinzugefügt werden. Weitere Informationen und Anweisungen finden Sie unter *SDK und Testwerkzeuge* herunterladen unter [Starten](/help/ios/getting-started/requirements.md).

## Geografische Standorte und pois verfolgen {#section_B1616E400A7548F9A672F97FEC75AE27}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden *Sie unter SDK und Config File to your Project* in [Core Implementation and Lifecycle](/help/ios/getting-started/dev-qs.md).
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
   >Sie können jederzeit aufrufen `trackLocation` .

   Verwenden Sie zum Bestimmen des an den `trackLocation` Aufruf weitergeleiteten Speicherorts die Option [Abrufen des Benutzerstandorts](https://developer.apple.com/Library/ios/documentation/UserExperience/Conceptual/LocationAwarenessPG/CoreLocation/CoreLocation.html).

Wenn festgestellt wird, dass sich der Standort in einem definierten POI-Radius befindet, wird zusätzlich eine `a.loc.poi`-Kontextdatenvariable mit dem Treffer `trackLocation` gesendet und in den Standortberichten als ein POI gemeldet. Außerdem wird eine `a.loc.dist`-Kontextvariable gesendet, die den Abstand von den definierten Koordinaten in Metern enthält.

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Zusätzlich zum Standortnamen können Sie mit jedem trackLocation-Aufruf zusätzliche Kontextdaten senden:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"GPS" forKey:@"myapp.location.LocationSource"]; 
[ADBMobile trackLocation: currentLocation data:contextData];
```

Kontextdatenwerte müssen benutzerdefinierte Variablen zugeordnet werden:

![](assets/map-location-context-data.png)

## Location context data {#section_FFB71E6653F9410A89CC6ACC0C9164A9}

Der Breiten- und Längengrad werden mithilfe von drei unterschiedlichen Kontextdatenparametern für insgesamt sechs Kontextdatenparameter gesendet, wobei jeder Parameter eine unterschiedliche Genauigkeitsstufe darstellt.

Beispielsweise stehen die Koordinaten lat = 40.93231, lon = -111.93152 für einen Standort mit einer Genauigkeit von 1 m. Dieser Standort wird über die folgenden Variablen hinweg entsprechend der Genauigkeitsstufe aufgeteilt:

* `a.loc.lat.a`= 040.9
* `a.loc.lat.b` = 32
* `a.loc.lat.c` = 31
* `a.loc.lon.a` = -111.9
* `a.loc.lon.b` = 31
* `a.loc.lon.c` = 52

Einige Genauigkeitsstufen werden in Abhängigkeit der Genauigkeit des aktuellen Standorts ggf. als „00“ angezeigt. Wenn der Standort beispielsweise auf bis zu 100 m genau ist, werden `a.loc.lat.c` und `a.loc.lon.c` mit „00“ aufgefüllt.

## Weitere Informationen {#section_931AC1E0D88147E29FE1B6E3CC1E9550}

Beachten Sie die folgenden Informationen:

* A `trackLocation` request sends in the equivalent of a `trackAction` call.

* POIs werden nicht als Bestandteil von normalen `trackAction`- und `trackState` Aufrufen weitergegeben. Daher müssen Sie einen `trackLocation`-Aufruf verwenden, um POIs zu verfolgen.

* `trackLocation` muss so oft wie nötig aufgerufen werden, um Standorte und POIs zu verfolgen.

   Sie sollten `trackLocation` aufrufen, wenn die App gestartet wird und dann in Abhängigkeit der Anforderungen der Anwendung bei Bedarf.

* POIs werden nur dann aufgefüllt, nachdem sie in der App-Konfigurationsdatei aufgefüllt wurden.

   Sie werden nicht auf historische `trackLocation`-Aufrufe angewendet, die zuvor gesendet wurden.
* `trackLocation`-Aufrufe unterstützen das Senden zusätzlicher Kontextdaten – ähnlich wie `trackAction`-Aufrufe.

* Wenn sich die Radien zweier POIs überschneiden, wird der erste POI verwendet, der den aktuellen Standort enthält.

   Wenn sich die POIs überlappen, sollten Sie die POIs nach Detailstufe sortieren, um sicherzustellen, dass der POI mit der höheren Präzision verwendet wird.

