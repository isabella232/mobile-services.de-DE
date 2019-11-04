---
description: Diese Informationen helfen Ihnen beim Migrieren von den Versionen 3.x oder 2.x zu Version 4.x der iOS-Bibliothek.
seo-description: Diese Informationen helfen Ihnen beim Migrieren von den Versionen 3.x oder 2.x zu Version 4.x der iOS-Bibliothek.
seo-title: Zur iOS-Bibliothek der Version 4.x migrieren
solution: Experience Cloud,Analytics
title: Zur iOS-Bibliothek der Version 4.x migrieren
topic: Entwickler und Implementierung
uuid: 5668972b-f355-4e03-9df0-8c82ddf6809b
translation-type: ht
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Zur iOS-Bibliothek der Version 4.x migrieren{#migrating-to-the-x-ios-library}

Diese Informationen helfen Ihnen beim Migrieren von den Versionen 3.x oder 2.x zu Version 4.x der iOS-Bibliothek.

>[!IMPORTANT]
>
>Das SDK verwendet `NSUserDefaults` zum Speichern von Daten, die zur Berechnung von Unique Users und Lebenszyklusmetriken benötigt werden, und anderen mit SDK-Hauptfunktionen verbundenen Daten.  Wenn Sie in `NSUserDefaults` die Werte, die vom SDK erwartet werden, ändern oder entfernen, kann dies zu unerwartetem Verhalten in Form von Dateninkonsistenzen führen.

In Version 4.x der iOS-SDK-Bibliothek sind alle öffentlichen Methoden in einem Header vereinigt. Außerdem steht die Funktionalität jetzt auch über Methoden auf Klassenebenen zur Verfügung, damit Sie Pointer, Instanzen und Singletons nicht verfolgen müssen.

## Events, Props und eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

In Version 4 ist es nicht mehr möglich, Variablen direkt in Ihrer App zuzuweisen, beispielsweise events, eVars, props, heirs und lists. Das SDK verwendet stattdessen Kontextdaten und Verarbeitungsregeln, um Ihre App-Daten mit Analytics-Variablen für die Berichterstellung zu verknüpfen.

Verarbeitungsregeln bieten folgende Vorteile:

* Sie können Ihre Datenzuweisung ändern, ohne ein Update im App Store einzureichen.
* Sie können relevante Namen für Ihre Daten verwenden, anstatt Variablen festzulegen, die spezifisch für eine Report Suite sind.
* Es ist kaum Aufwand nötig, um zusätzliche Daten zu senden.

   Diese Werte werden nicht in Berichten angezeigt, bis sie mithilfe von Verarbeitungsregeln zugeordnet wurden.

>[!TIP]
>
>Werte, die Sie direkt Variablen zuweisen, sollten nun zum NSDictionary `data` hinzugefügt werden.

## Ungenutzte Eigenschaften entfernen {#section_145222EAA20F4CC2977DD883FDDBBFC5}

Die neue Datei `ADBMobileConfig.json` enthält anwendungsspezifische, globale Einstellungen und ersetzt die meisten Konfigurationsvariablen, die in vorherigen Versionen zum Einsatz kamen. Im Folgenden finden Sie ein Beispiel für eine `ADBMobileConfig.json`-Datei:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 5, 
        "privacyDefault" : "optedin", 
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000], 
                    ["santa cruz",36.972935,-122.01725,600] 
                ] 
    }, 
 "target" : { 
  "clientCode" : "myTargetClientCode", 
  "timeout" : 5 
 }, 
 "audienceManager" : { 
  "server" : "myServer.demdex.com" 
 } 
}
```


### Verschieben der Konfigurationsdatei

So verschieben Sie die Konfigurationsdatei:

1. Verschieben Sie den Wert, der für die Variable in der ersten Spalte festgelegt ist, zur Variablen in der zweiten Spalte.
1. Entfernen Sie die alte Konfigurationsvariable aus Ihrem Code.

### Migrationsinformationen

Die folgende Tabelle enthält die Konfigurationsvariablen, die Sie in die Konfigurationsdatei verschieben müssen.

#### Migration von Version 3.x

Verschieben Sie den Wert aus der ersten Spalte zu der Variablen in der zweiten Spalte.

| Konfigurationsvariable | Variable in der Datei `ADBMobileConfig.json` |
|--- |--- |
| offlineTrackingEnabled | „offlineEnabled“ |
| offlineHitLimit | „batchLimit“ |
| reportSuiteIDs | „rsids“ |
| trackingServer | „server“ |
| charSet | „charset“ |
| currencyCode | „currency“ |
| ssl | „ssl“ |
| linkTrackVars | Entfernen: Nicht länger verwendet. |
| linkTrackEvents | Entfernen: Nicht länger verwendet. |


#### Migration von Version 2.x

Verschieben Sie den Wert aus der ersten Spalte zu der Variablen in der zweiten Spalte.

| Konfigurationsvariable | Variable in der Datei `ADBMobileConfig.json` |
|--- |--- |
| trackOffline | „offlineEnabled“ |
| offlineLimit | „batchLimit“ |
| account | „rsids“ |
| trackingServer | „server“, entfernen Sie das Präfix `"https://"`. Das Protokollpräfix wird automatisch entsprechend der „ssl“-Einstellung hinzugefügt. |
| trackingServerSecure | Entfernen. Definieren Sie für sichere Verbindungen „server“ und aktivieren Sie dann „ssl“. |
| charSet | „charset“ |
| currencyCode | „currency“ |
| ssl | „ssl“ |
| linkTrackVars | Entfernen: Nicht länger verwendet. |
| linkTrackEvents | Entfernen: Nicht länger verwendet. |
| timestamp | Entfernen: Nicht länger konfigurierbar. |
| dc | Entfernen: Nicht länger verwendet. |
| userAgent | Entfernen: Nicht länger konfigurierbar. |
| dynamicVariablePrefix | Entfernen: Nicht länger verwendet. |
| visitorNamespace | Entfernen: Nicht länger verwendet. |
| usePlugins | Entfernen: Nicht länger verwendet. |
| useBestPractices  Alle Aufrufe für massenhafte Messung (getChurnInstance ) | Entfernen: Durch Lebenszyklusmetriken ersetzt. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](//help/ios/metrics.md). |


## Verfolgungsaufruf und -variablen aktualisieren {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Anstelle der auf das Web ausgelegten Aufrufe `track` und `trackLink` verwendet Version 4 des SDK folgende Methoden:

* `trackState:data:` Die Statusangaben entsprechen den verfügbaren Ansichten in der App, z. B. `home dashboard`, `app settings` und `cart`.

   Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `trackState`-Aufrufe inkrementieren die Seitenansichten.

* `trackAction:data:` Aktionen, wie z. B. `logons`, `banner taps`, `feed subscriptions` und andere Metriken, die in Ihrer App auftreten und die Sie messen möchten.

Beim Parameter `data` für beide dieser Methoden handelt es sich um ein `NSDictionary`, das Namen-Wert-Paare enthält, die als Kontextdaten gesendet werden.

### Events, Props und eVars

In Version 4 ist es nicht mehr möglich, Variablen direkt in Ihrer App zuzuweisen, beispielsweise events, eVars, props, heirs und lists. Das SDK nutzt jetzt Kontextdaten und Verarbeitungsregeln, um Ihre App-Daten zwecks Reporting Analytics-Variablen zuzuordnen.

Verarbeitungsregeln bieten folgende Vorteile:

* Sie können Ihre Datenzuweisung ändern, ohne ein Update im App Store einzureichen.
* Sie können relevante Namen für Ihre Daten verwenden, anstatt Variablen festzulegen, die spezifisch für eine Report Suite sind.
* Es ist kaum Aufwand nötig, um zusätzliche Daten zu senden.

   Diese Werte werden in Berichten nicht angezeigt, bis sie mithilfe von Verarbeitungsregeln zugeordnet werden. Weitere Informationen finden Sie unter [Verarbeitungsregeln und Kontextdaten](/help/ios/getting-started/proc-rules.md).

Werte, die Sie direkt zu Variablen zugewiesen haben, sollten stattdessen zum `data``NSDictionary` hinzugefügt werden. Aufrufe zu `setProp`, `setEvar` und Zuweisungen zu persistenten Kontextdaten sollten entfernt und die Daten dem Parameter `data` hinzugefügt werden.

### AppSection/Server, GeoZip, Transaktions-ID, Kampagne und andere Standardvariablen

Daten, die Sie im Messobjekt festgelegt haben, einschließlich der oben aufgeführten Variablen, sollten stattdessen zum `data``NSDictionary` hinzugefügt werden. Die einzigen Daten, die mit dem Aufruf `trackState` oder `trackAction` gesendet werden, beinhalten die Nutzlast des Parameters `data`.

### Verfolgungsaufrufe ersetzen

Ersetzen Sie in Ihrem Code folgende Methoden durch einen Aufruf von `trackState` oder `trackAction`:

#### Migration von Version 3.x

* `trackAppState (trackState)`
* `trackEvents (trackAction)`
* `track (trackAction)`
* `trackWithContextData (trackAction)`
* `trackLinkURL (trackAction)`

#### Migration von Version 2.x

* `track (trackState)`
* `trackLink (trackAction)`

## Benutzerspezifische Besucher-ID {#section_2CF930C13BA64F04959846E578B608F3}

Ersetzen Sie die Variable `visitorID` durch einen Aufruf von `setUserIdentifier:`.

## Offline-Verfolgung {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Die Offline-Verfolgung wird in der Datei `ADBMobileConfig.json` aktiviert. Alle anderen Offline-Konfigurationen erfolgen automatisch.

Entfernen Sie aus Ihrem Code Aufrufe folgender Methoden:

### Version 3.x

* `setOnline`
* `setOffline`

### Version 2.x

* `forceOffline`
* `forceOnline`

## Variable „products“ {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Da die Variable „“ in Verarbeitungsregeln nicht verfügbar ist, können Sie die folgende Syntax zum Festlegen von `products`products verwenden:

```objective-c
//create a processing rule to set the corresponding product event. 
// for example, set prodView event when context data a.action = "product view" 
[ADBMobile trackAction:@"LikeButtonClicked"  
                  data:@{@"&&products" : @";Cool Shoe"}];
```

![](assets/prod-view.png)