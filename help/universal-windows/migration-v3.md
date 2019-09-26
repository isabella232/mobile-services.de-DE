---
description: Dieser Abschnitt beschreibt, wie Sie von der 3.x-Version eines vorhergehenden Windows Mobile-SDK zum universellen Windows-Plattform-SDK 4.x für Experience Cloud-Lösungen migrieren.
seo-description: Dieser Abschnitt beschreibt, wie Sie von der 3.x-Version eines vorhergehenden Windows Mobile-SDK zum universellen Windows-Plattform-SDK 4.x für Experience Cloud-Lösungen migrieren.
seo-title: Zu 4.x migrieren
solution: Marketing Cloud,Analytics
title: Zu 4.x migrieren
topic: Entwickler und Implementierung
uuid: bdd6c5cd-3892-4e99-b69e-77105ad66e25
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Zu den 4.x-SDKs migrieren{#migrate-to-x}

In diesem Abschnitt wird beschrieben, wie Sie von der Version 3.x des Windows Mobile SDK auf das Universal Windows Platform 4.x SDK für Experience Cloud-Lösungen migrieren.

Mit der Umstellung auf Version 4.x können jetzt alle Funktionen über statische Methoden aufgerufen werden. Sie müssen keine eigenen Objekte mehr verfolgen.

In den folgenden Abschnitten wird die Migration von Version 3.x zu Version 4.x schrittweise erläutert.

## Remove unused properties {#section_145222EAA20F4CC2977DD883FDDBBFC5}

Wahrscheinlich haben Sie bemerkt, dass Ihr Download die neue Datei `ADBMobileConfig.json` enthält. Diese Datei enthält anwendungsspezifische globale Einstellungen und ersetzt die meisten der Konfigurationsvariablen, die in vorherigen Versionen verwendet wurden.

Im Folgenden finden Sie ein Beispiel für eine `ADBMobileConfig.json`-Datei:

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

### Migrieren von 3.x

Die folgende Tabelle enthält eine Liste der Variablen in den 3.x-SDKs und den neuen Namen in den 4.x-SDKs:

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

### Ereignisse, Props, eVars

Wenn Sie sich die [SDK-Methoden](/help/universal-windows/c-configuration/methods.md)angesehen haben, fragen Sie sich wahrscheinlich, wo Sie Ereignisse, eVars, Props, Erben und Listen festlegen können. In Version 4 können Sie diese Variablentypen nicht mehr direkt in Ihrer Anwendung zuweisen. Stattdessen nutzt das SDK Kontextdaten und Verarbeitungsregeln, um Ihre App-Daten zwecks Reporting Analytics-Variablen zuzuordnen.

Verarbeitungsregeln bieten folgende Vorteile:

* Sie können Ihre Datenzuweisung ändern, ohne ein Update im App Store einzureichen.
* Sie können relevante Namen für Ihre Daten verwenden, anstatt Variablen festzulegen, die spezifisch für eine Report Suite sind.
* Es ist kaum Aufwand nötig, um zusätzliche Daten zu senden. Diese Werte werden erst dann in Berichten angezeigt, wenn sie mithilfe von Verarbeitungsregeln zugeordnet werden.

Weitere Informationen finden Sie im Abschnitt *Verarbeitungsregeln* in der [Analytics-Übersicht](/help/universal-windows/analytics/analytics.md).

Alle Werte, die Sie Variablen direkt zugewiesen haben, müssen stattdessen Kontextdaten hinzugefügt werden. This means that calls to `SetProp`, `SetEvar`, and assignments to persistent context data should all be removed and the values added to context data.

### AppSection/Server, GeoZip, transaction ID, Campaign, and other standard variables

Stattdessen sollten andere Daten, die Sie im Messobjekt festgelegt haben, einschließlich der oben aufgeführten Variablen, den Kontextdaten hinzugefügt werden. Das heißt, die einzigen Daten, die mit einem `TrackState` oder einem `TrackAction` -Aufruf gesendet werden, sind die Nutzdaten im `data` Parameter.

**Tracking-Aufrufe ersetzen**

Ersetzen Sie in Ihrem gesamten Code folgende Methoden durch einen Aufruf von `trackState` oder `trackAction`:

**Migrieren von 3.x**:

* TrackAppState (TrackState)
* TrackEvents (TrackAction)
* Track (TrackAction)
* TrackLinkURL (TrackAction)

## Dienst für eine benutzerdefinierte ID {#section_2CF930C13BA64F04959846E578B608F3}

Replace the `visitorID` variable with a call to `setUserIdentifier`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Die Offline-Verfolgung ist in der `ADBMobileConfig.json` Datei aktiviert. Alle anderen Offlinekonfigurationen werden automatisch durchgeführt.

Entfernen Sie die Aufrufe der folgenden Methoden aus Ihrem gesamten Code:

**Migrieren von 3.x**:

* SetOnline
* SetOffline

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

The value of `"&&products"` (in this example, the value is `";Cool Shoe`") should follow the products string syntax for the type of event that you are tracking.
