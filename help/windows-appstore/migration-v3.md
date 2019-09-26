---
description: Dieser Abschnitt beschreibt, wie Sie Version 3.x eines vorigen Windows-Mobile-SDK zu Version 4.x des Windows 8.1 Universal App Store-SDK für Experience Cloud-Lösungen migrieren.
seo-description: Dieser Abschnitt beschreibt, wie Sie Version 3.x eines vorigen Windows-Mobile-SDK zu Version 4.x des Windows 8.1 Universal App Store-SDK für Experience Cloud-Lösungen migrieren.
seo-title: Zu den 4.x-SDKs migrieren
solution: Marketing Cloud,Analytics
title: Zu den 4.x-SDKs migrieren
topic: Entwickler und Implementierung
uuid: e0fe3b7b-cda5-4a91-834c-2c7e17a501a3
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migrate to the 4.x SDKs {#migrate-to-the-x-sdks}

Dieser Abschnitt beschreibt, wie Sie Version 3.x eines vorigen Windows-Mobile-SDK zu Version 4.x des Windows 8.1 Universal App Store-SDK für Experience Cloud-Lösungen migrieren.

Mit dem Übergang zu Version 4.x können alle Funktionen über statische Methoden aufgerufen werden, sodass Sie Ihre eigenen Objekte nicht mehr nachverfolgen müssen.

In den folgenden Abschnitten wird die Migration von Version 3.x zu Version 4.x schrittweise erläutert.

## Remove unused properties {#section_145222EAA20F4CC2977DD883FDDBBFC5}

Wahrscheinlich haben Sie bemerkt, dass Ihr Download die neue Datei `ADBMobileConfig.json` enthält. Diese Datei enthält anwendungsspezifische globale Einstellungen und ersetzt die meisten Konfigurationsvariablen, die in früheren Versionen verwendet wurden. Im Folgenden finden Sie ein Beispiel für eine `ADBMobileConfig.json`-Datei:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 300, 
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

Die folgende Tabelle enthält die Konfigurationsvariablen, die Sie in die Konfigurationsdatei verschieben müssen. Verschieben Sie den Wertesatz für die Variable in der ersten Spalte zur Variablen in der zweiten Spalte und entfernen Sie anschließend die alte Konfigurationsvariable aus Ihrem Code.

## Migrieren von 3.x

| Konfigurationsvariable/Methode | Variable in the `ADBMobileConfig.json` file. |
|--- |--- |
| offlineTrackingEnabled | "offlineEnabled" |
| reportSuiteIDs | „rsids“ |
| trackingServer | „server“ |
| charSet | „charset“ |
| currencyCode | „currency“ |
| ssl | "ssl" |
| setOfflineHitLimit | Entfernen: Nicht länger verwendet. |
| linkTrackVars | Entfernen: Nicht länger verwendet. |
| linkTrackEvents | Entfernen: Nicht länger verwendet. |

## Update track calls and tracking variables {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Anstelle der webfokussierten Aufrufe `Track` und `TrackLink` verwendet Version 4 des SDK zwei Methoden, die in der mobilen Welt etwas sinnvoller sind:

* `TrackState` Status sind die in Ihrer App verfügbaren Ansichten wie „Startseiten-Dashboard“, „App-Einstellungen“, „Warenkorb“ usw. Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `trackState`-Aufrufe inkrementieren die Seitenansichten.

* `TrackAction` Bei Aktionen handelt es sich um die Dinge, die in Ihrer App vor sich gehen, die Sie messen möchten, beispielsweise „Anmeldungen“, „Banner-Tippvorgänge“, „Feed-Abonnements“ und andere Metriken. Durch diese Aufrufe wird die Anzahl der Seitenaufrufe nicht erhöht.

Der Parameter `contextData` für die beiden Methoden besteht aus Name/Wert-Paaren, die als Kontextdaten gesendet werden.

## Events, Props und eVars

If you've looked at the SDK methods, you are probably wondering where to set events, eVars, props, heirs, and lists. [](/help/windows-appstore/c-configuration/methods.md) In Version 4 können Sie diese Variablentypen nicht mehr direkt in Ihrer Anwendung zuweisen. Stattdessen nutzt das SDK Kontextdaten und Verarbeitungsregeln, um Ihre App-Daten zwecks Reporting Analytics-Variablen zuzuordnen.

Verarbeitungsregeln bieten mehrere Vorteile:

* Sie können Ihre Datenzuweisung ändern, ohne ein Update im App Store einzureichen.
* Sie können relevante Namen für Ihre Daten verwenden, anstatt Variablen festzulegen, die spezifisch für eine Report Suite sind.
* Es ist kaum Aufwand nötig, um zusätzliche Daten zu senden. Diese Werte werden erst dann in Berichten angezeigt, wenn sie mithilfe von Verarbeitungsregeln zugeordnet werden.

For more information, see *Processing Rules* in [Analytics](/help/windows-appstore/analytics/analytics.md).

Alle Werte, die Sie Variablen direkt zugewiesen haben, müssen stattdessen Kontextdaten hinzugefügt werden. This means that calls to `SetProp`, `SetEvar`, and assignments to persistent context data should all be removed and the values added to context data.

**AppSection/Server, GeoZip, Transaktions-ID, Kampagne und andere Standardvariablen**

Stattdessen sollten andere Daten, die Sie im Messobjekt festgelegt haben, einschließlich der oben aufgeführten Variablen, den Kontextdaten hinzugefügt werden.

Einfach gesagt sind die einzigen Daten, die in einem `TrackState`- oder `TrackAction`-Aufruf gesendet werden, die Daten, die als Nutzlast im `data`-Parameter gesendet werden.

### Replace tracking calls

Ersetzen Sie in Ihrem gesamten Code folgende Methoden durch einen Aufruf von `trackState` oder `trackAction`:

### Migrieren von 3.x

* `TrackAppState` (TrackState)
* `TrackEvents` (TrackAction)
* `Track` (TrackAction)
* `TrackLinkURL` (TrackAction)

## Custom visitor ID {#section_2CF930C13BA64F04959846E578B608F3}

Replace the `visitorID` variable with a call to `setUserIdentifier`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the  file. `ADBMobileConfig.json` All other offline configuration is done automatically.

Entfernen Sie die Aufrufe der folgenden Methoden aus Ihrem gesamten Code:

### Migrieren von 3.x

* `SetOnline`
* `SetOffline`

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Da die Variable „“ in Verarbeitungsregeln nicht verfügbar ist, können Sie die folgende Syntax zum Festlegen von `products`products verwenden:

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

In this example, the value of `"&&products"` is `";Cool Shoe`" and should follow the products string syntax for the type of event that you are tracking.