---
description: Mit dem Geostandort können Sie mithilfe von Längen- und Breitengrad und vordefinierten POIs in Ihren Android-Apps Positionsdaten messen.
seo-description: Mit dem Geostandort können Sie mithilfe von Längen- und Breitengrad und vordefinierten POIs in Ihren Android-Apps Positionsdaten messen.
seo-title: Geografische Standort und Zielpunkte
solution: Marketing Cloud, Analytics
title: Geografische Standort und Zielpunkte
topic: Entwickler und Implementierung
uuid: b 8209370-cbc 4-40 f 9-97 d 8-017 e 2 d 74 a 377
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Geo-location and points of interest {#geo-location-and-points-of-interest}

Mit dem Geostandort können Sie mithilfe von Längen- und Breitengrad und vordefinierten POIs in Ihren Android-Apps Positionsdaten messen.

Jeder `trackLocation`-Aufruf sendet folgende Informationen:

* Längengrad, Breitengrad und Standort als POI, der in der Adobe Mobile Services UI definiert ist.

   Diese Informationen werden zur automatischen Meldung an die Variablen für die mobile Lösung übergeben.

* Entfernung vom Zentrum und Präzision in Form von Kontextdaten.

   Diese Variablen werden nicht automatisch erfasst. You must map these context data variables by using the instructions in the *Sending Additional Data* section below.

## Dynamische POI-Aktualisierungen {#section_3747B310DD5147E2AAE915E762997712}

Ab Version 4.2 werden POIs in der Adobe Mobile-UI definiert und dynamisch mit der App-Konfigurationsdatei synchronisiert. Für diese Synchronisierung ist eine `analytics.poi` Einstellung in der [adbmobile JSON-Konfiguration erforderlich](/help/android/configuration/json-config/json-config.md):

```js
“analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”,
```

Wenn dies nicht konfiguriert ist, müssen Sie eine aktualisierte Version der Datei `ADBMobile.json` herunterladen und sie zu Ihrer App hinzufügen. Weitere Informationen finden Sie unter [SDK und Testwerkzeuge herunterladen](/help/android/getting-started/requirements.md).

## Tracking geo-location and POIs {#section_B1616E400A7548F9A672F97FEC75AE27}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Config File to your intellij IDEA oder Eclipse Project* in [Core Implementation and Lifecycle](/help/android/getting-started/dev-qs.md).

1. Importieren Sie die Bibliothek:

   ```java
   import com.adobe.mobile.*;
   ```

1. Rufen Sie `trackLocation` auf, um den aktuellen Standort zu verfolgen:

   ```java
   Location currentLocation = new Location("my location here"); 
   Analytics.trackLocation(currentLocation, null);
   ```

   >[!TIP]
   >
   >Sie können jederzeit aufrufen `trackLocation` .

   You can use location strategies to determine the location that is passed to the `trackLocation` call. Weitere Informationen finden Sie unter [Android-Positionierungsstrategien](https://developer.android.com/guide/topics/location/strategies.html).

Darüber hinaus wird, wenn sich der Standort innerhalb eines definierten Radius zum POI befindet, eine `a.loc.poi`-Kontextdatenvariable mit dem `trackLocation`-Treffer gesendet und als POI im Bericht **Aufschlüsselung nach Ort** aufgeführt. Außerdem wird eine `a.loc.dist`-Kontextvariable gesendet, die den Abstand von den definierten Koordinaten in Metern enthält.

## Sending additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Zusätzlich zum Standortnamen können Sie mit jedem trackLocation-Aufruf zusätzliche Kontextdaten senden:

```java
HashMap<String, Object> locationContextData = new HashMap<String, Object>(); 
locationContextData.put("myapp.location.LocationSource", "GPS"); 
 
Location currentLocation = new Location("my location here"); 
Analytics.trackLocation(currentLocation, locationContextData);
```

Die Werte der Kontextdaten müssen in der Adobe Mobile Services UI benutzerdefinierten Variablen zugewiesen werden.

![](assets/map-location-context-data.png)

## Location context data {#section_FFB71E6653F9410A89CC6ACC0C9164A9}

Längen- und Breitengrad werden jeweils mit drei verschiedenen Kontextdaten-Parametern gesendet, wobei jeder Parameter eine unterschiedliche Präzisionsstufe darstellt. Insgesamt werden also sechs Kontextdaten-Parameter gesendet.

Beispiel: Koordinaten mit dem lat = 40.93231 und dem long = -111.93152 beschreiben einen Standort mit einer Präzision von einem Meter. Der Standort wird je nach Präzisionsstufe auf die folgenden Variablen aufgeteilt:

`a.loc.lat.a`= 040.9

`a.loc.lat.b` = 32

`a.loc.lat.c` = 31

`a.loc.lon.a` = -111.9

`a.loc.lon.b` = 31

`a.loc.lon.c` = 52

Einige Präzisionsstufen werden je nach Präzision des aktuellen Standorts möglicherweise als `00` angezeigt. Wenn der Standort beispielsweise auf 100 Meter genau ist, enthalten `a.loc.lat.c` und `a.loc.lon.c` den Wert `00`.

Beachten Sie die folgenden Informationen:

* A `trackLocation` request sends in the equivalent of a `trackAction` call.

* POIs werden nicht als Teil der typischen `trackAction`- und `trackState`-Aufrufe übergeben. Sie müssen also einen `trackLocation`-Aufruf verwenden, um POIs zu verfolgen.

* `trackLocation` muss so oft wie nötig aufgerufen werden, um Standorte und POIs zu verfolgen.

   Wir empfehlen, `trackLocation` beim Start der App und dann je nach App-Anforderungen nach Bedarf aufzurufen.

* POIs werden nur eingefügt, wenn sie in der App-Konfigurationsdatei definiert sind.

   Die POIs werden nicht auf bereits gesendete `trackLocation`-Aufrufe angewendet.
* `trackLocation`-Aufrufe unterstützen das Senden zusätzlicher Kontextdaten – ähnlich wie `trackAction`-Aufrufe.

* Wenn sich die Radien zweier POIs überschneiden, wird der erste POI verwendet, der den aktuellen Standort enthält.

   Wenn sich Ihre POIs überlappen, sollten Sie die POIs in der Reihenfolge von detailliert zu allgemein aufführen, um sicherzustellen, dass der detaillierteste POI gemeldet wird.

