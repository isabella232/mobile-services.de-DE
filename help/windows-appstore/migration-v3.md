---
description: In diesem Abschnitt wird beschrieben, wie Sie von der 3.x-Version eines vorherigen Windows Mobile SDK zum Windows 8.1 Universal App Store 4.x SDK für Experience Cloud-Lösungen migrieren.
solution: Experience Cloud Services,Analytics
title: Migration zu den SDKs der Version 4.x
topic-fix: Developer and implementation
uuid: e0fe3b7b-cda5-4a91-834c-2c7e17a501a3
exl-id: d6dc34f2-61b7-4026-a66a-19284e21e69c
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 25%

---

# Migration zu den SDKs der Version 4.x {#migrate-to-the-x-sdks}

In diesem Abschnitt wird beschrieben, wie Sie von der 3.x-Version eines vorherigen Windows Mobile SDK zum Windows 8.1 Universal App Store 4.x SDK für Experience Cloud-Lösungen migrieren.

Mit der Umstellung auf Version 4.x ist nun über statische Methoden auf alle Funktionen zugegriffen werden kann, sodass Ihre eigenen Objekte nicht mehr verfolgt werden.

Die folgenden Abschnitte führen Sie durch die Migration von Version 3.x zu Version 4.x.

## Ungenutzte Eigenschaften entfernen {#section_145222EAA20F4CC2977DD883FDDBBFC5}

Sie haben wahrscheinlich eine neue `ADBMobileConfig.json` Datei, die im Download enthalten ist. Diese Datei enthält anwendungsspezifische globale Einstellungen und ersetzt die meisten Konfigurationsvariablen, die in früheren Versionen verwendet wurden. Im Folgenden finden Sie ein Beispiel für eine `ADBMobileConfig.json`-Datei:

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

Die folgende Tabelle enthält die Konfigurationsvariablen, die Sie in die Konfigurationsdatei verschieben müssen. Verschieben Sie den für die Variable festgelegten Wert in der ersten Spalte in die Variable in der zweiten Spalte und entfernen Sie dann die alte Konfigurationsvariable aus Ihrem Code.

## Migration von 3.x

| Konfigurationsvariable/Methode | Variable in der `ADBMobileConfig.json` -Datei. |
|--- |--- |
| offlineTrackingEnabled | „offlineEnabled“ |
| reportSuiteIDs | „rsids“ |
| trackingServer | „server“ |
| charSet | „charset“ |
| currencyCode | „currency“ |
| ssl | „ssl“ |
| setOfflineHitLimit | Entfernen, wird nicht mehr verwendet. |
| linkTrackVars | Entfernen, wird nicht mehr verwendet. |
| linkTrackEvents | Entfernen, wird nicht mehr verwendet. |

## Verfolgungsaufruf und -variablen aktualisieren {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Statt die Web-fokussierte `Track` und `TrackLink` -Aufrufe verwendet das SDK Version 4 zwei Methoden, die in der mobilen Welt etwas sinnvoller sind:

* `TrackState` Status sind die Ansichten, die in Ihrer App verfügbar sind, z. B. &quot;Startseiten-Dashboard&quot;, &quot;App-Einstellungen&quot;, &quot;Warenkorb&quot;usw. Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `trackState`-Aufrufe inkrementieren die Seitenansichten.

* `TrackAction` Bei Aktionen handelt es sich um die Dinge, die in Ihrer App vor sich gehen, die Sie messen möchten, z. B. &quot;Anmeldungen&quot;, &quot;Banner-Tippvorgänge&quot;, &quot;Feed-Abonnements&quot;und andere Metriken. Diese Aufrufe erhöhen nicht die Seitenansichten.

Die `contextData` -Parameter für beide dieser Methoden enthalten Name-Wert-Paare, die als Kontextdaten gesendet werden.

## Ereignisse, Props und eVars

Wenn Sie sich die [SDK-Methoden](/help/windows-appstore/c-configuration/methods.md), fragen Sie sich wahrscheinlich, wo Sie Ereignisse, eVars, Props, Erben und Listen festlegen können. In Version 4 können Sie diese Variablentypen nicht mehr direkt in Ihrer App zuweisen. Stattdessen verwendet das SDK Kontextdaten und Verarbeitungsregeln, um Ihre App-Daten Analytics-Variablen für die Berichterstellung zuzuordnen.

Verarbeitungsregeln bieten Ihnen verschiedene Vorteile:

* Sie können Ihre Datenzuordnung ändern, ohne eine Aktualisierung an den Appstore zu senden.
* Sie können aussagekräftige Namen für Daten verwenden, anstatt Variablen festzulegen, die für eine Report Suite spezifisch sind.
* Das Senden zusätzlicher Daten hat geringe Auswirkungen. Diese Werte werden erst dann in Berichten angezeigt, wenn sie mithilfe von Verarbeitungsregeln zugeordnet werden.

Weitere Informationen finden Sie unter *Verarbeitungsregeln* in [Analytics](/help/windows-appstore/analytics/analytics.md).

Alle Werte, die Sie Variablen direkt zugewiesen haben, sollten stattdessen zu Kontextdaten hinzugefügt werden. Das bedeutet, dass `SetProp`, `SetEvar`, und Zuweisungen zu persistenten Kontextdaten sollten entfernt und die Werte zu Kontextdaten hinzugefügt werden.

**AppSection/Server, GeoZip, Transaktions-ID, Kampagne und andere Standardvariablen**

Alle anderen Daten, die Sie für das Messobjekt festgelegt haben, einschließlich der oben aufgeführten Variablen, sollten stattdessen zu Kontextdaten hinzugefügt werden.

Um es einfach zu sagen, die einzigen Daten, die mit einer `TrackState` oder `TrackAction` -Aufruf ist die Payload in der `data` Parameter.

### Verfolgungsaufrufe ersetzen

Ersetzen Sie im gesamten Code die folgenden Methoden durch einen Aufruf von `trackState` oder `trackAction`:

### Migration von 3.x

* `TrackAppState` (TrackState)
* `TrackEvents` (TrackAction)
* `Track` (TrackAction)
* `TrackLinkURL` (TrackAction)

## Benutzerspezifische Besucher-ID {#section_2CF930C13BA64F04959846E578B608F3}

Ersetzen Sie die Variable `visitorID` durch einen Aufruf von `setUserIdentifier`.

## Offline-Verfolgung {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Die Offline-Verfolgung ist in der Variablen `ADBMobileConfig.json` -Datei. Alle anderen Offline-Konfigurationen erfolgen automatisch.

Entfernen Sie im gesamten Code Aufrufe der folgenden Methoden:

### Migration von 3.x

* `SetOnline`
* `SetOffline`

## Variable „products“ {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Da die Variable „products“ in Verarbeitungsregeln nicht verfügbar ist, können Sie die folgende Syntax zum Festlegen von `products` verwenden:

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

In diesem Beispiel wird der Wert von `"&&products"` is `";Cool Shoe`&quot; und sollte der Syntax der Produktzeichenfolge für den Ereignistyp folgen, den Sie verfolgen.
