---
description: In diesem Abschnitt wird beschrieben, wie Sie von der 3.x-Version eines vorherigen Windows Mobile SDK zum Windows 8.1 Universal App Store 4.x SDK for Experience Cloud Solutions migrieren.
seo-description: In diesem Abschnitt wird beschrieben, wie Sie von der 3.x-Version eines vorherigen Windows Mobile SDK zum Windows 8.1 Universal App Store 4.x SDK for Experience Cloud Solutions migrieren.
seo-title: Zu den 4.x-SDKs migrieren
solution: Experience Cloud,Analytics
title: Zu den 4.x-SDKs migrieren
topic: Developer and implementation
uuid: e0fe3b7b-cda5-4a91-834c-2c7e17a501a3
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 13%

---


# Zu den 4.x-SDKs migrieren {#migrate-to-the-x-sdks}

In diesem Abschnitt wird beschrieben, wie Sie von der 3.x-Version eines vorherigen Windows Mobile SDK zum Windows 8.1 Universal App Store 4.x SDK for Experience Cloud Solutions migrieren.

Mit der Umstellung auf Version 4.x sind alle Funktionen jetzt über statische Methoden verfügbar, sodass Sie Ihre eigenen Objekte nicht mehr verfolgen können.

Die folgenden Abschnitte führen Sie durch die Migration von Version 3.x auf Version 4.x.

## Ungenutzte Eigenschaften entfernen {#section_145222EAA20F4CC2977DD883FDDBBFC5}

Sie haben wahrscheinlich eine neue `ADBMobileConfig.json` Datei bemerkt, die im Download enthalten ist. Diese Datei enthält anwendungsspezifische globale Einstellungen und ersetzt die meisten Konfigurationsvariablen, die in früheren Versionen verwendet wurden. Im Folgenden finden Sie ein Beispiel für eine `ADBMobileConfig.json`-Datei:

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

Die folgende Tabelle enthält die Konfigurationsvariablen, die Sie in die Konfigurationsdatei verschieben müssen. Verschieben Sie den für die Variable in der ersten Spalte eingestellten Wert in die Variable in der zweiten Spalte und entfernen Sie dann die alte Konfigurationsvariable aus Ihrem Code.

## Migration von 3.x

| Konfigurationsvariable/Methode | Variable in the `ADBMobileConfig.json` file. |
|--- |--- |
| offlineTrackingEnabled | „offlineEnabled“ |
| reportSuiteIDs | „rsids“ |
| trackingServer | „server“ |
| charSet | „charset“ |
| currencyCode | &quot;currency&quot; |
| ssl | „ssl“ |
| setOfflineHitLimit | Entfernen, nicht mehr verwendet. |
| linkTrackVars | Entfernen, nicht mehr verwendet. |
| linkTrackEvents | Entfernen, nicht mehr verwendet. |

## Verfolgungsaufruf und -variablen aktualisieren {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Anstatt die Web-fokussierten `Track` und `TrackLink` -Aufrufe zu verwenden, verwendet das SDK Version 4 zwei Methoden, die in der mobilen Welt etwas sinnvoller sind:

* `TrackState` Statusangaben sind die Ansichten, die in Ihrer App verfügbar sind, z. B. &quot;Home Dashboard&quot;, &quot;App-Einstellungen&quot;, &quot;Warenkorb&quot;usw. Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `trackState`-Aufrufe inkrementieren die Seitenansichten.

* `TrackAction` Aktionen sind die Vorgänge, die in Ihrer App stattfinden und die Sie messen möchten, z. B. &quot;Anmeldungen&quot;, &quot;Bannerklappen&quot;, &quot;Feed-Abonnement&quot;und andere Metriken. Durch diese Aufrufe werden die Ansichten der Seite nicht inkrementiert.

The `contextData` parameter for both of these methods contains name-value pairs that are sent as context data.

## Ereignis, Props, eVars

Wenn Sie sich die [SDK-Methoden](/help/windows-appstore/c-configuration/methods.md)angesehen haben, fragen Sie sich wahrscheinlich, wo Sie Ereignis, eVars, Props, Erben und Listen einstellen können. In Version 4 können Sie diese Variablentypen nicht mehr direkt in Ihrer App zuweisen. Stattdessen verwendet das SDK Kontextdaten und Verarbeitungsregeln, um Ihre App-Daten Analytics-Variablen für den Berichte zuzuordnen.

Verarbeitungsregeln bieten mehrere Vorteile:

* Sie können Ihre Datenzuordnung ändern, ohne eine Aktualisierung an den App Store zu senden.
* Sie können aussagekräftige Namen für Daten verwenden, anstatt Variablen festzulegen, die für eine Report Suite spezifisch sind.
* Das Senden zusätzlicher Daten hat kaum Auswirkungen. Diese Werte werden erst dann in Berichten angezeigt, wenn sie mithilfe von Verarbeitungsregeln zugeordnet werden.

For more information, see *Processing Rules* in [Analytics](/help/windows-appstore/analytics/analytics.md).

Alle Werte, die Sie direkt Variablen zuweisen, sollten stattdessen den Kontextdaten hinzugefügt werden. This means that calls to `SetProp`, `SetEvar`, and assignments to persistent context data should all be removed and the values added to context data.

**AppSection/Server, GeoZip, Transaktions-ID, Kampagne und andere Standardvariablen**

Alle anderen Daten, die Sie für das Messungsobjekt eingestellt haben, einschließlich der oben aufgeführten Variablen, sollten stattdessen den Kontextdaten hinzugefügt werden.

Um es einfach zu sagen: Die einzigen Daten, die mit einem `TrackState` oder einem `TrackAction` -Aufruf gesendet werden, sind die Nutzdaten im `data` Parameter.

### Verfolgungsaufrufe ersetzen

Throughout your code, replace the following methods with a call to `trackState` or `trackAction`:

### Migration von 3.x

* `TrackAppState` (TrackState)
* `TrackEvents` (TrackAction)
* `Track` (TrackAction)
* `TrackLinkURL` (TrackAction)

## Benutzerspezifische Besucher-ID {#section_2CF930C13BA64F04959846E578B608F3}

Ersetzen Sie die Variable `visitorID` durch einen Aufruf von `setUserIdentifier`.

## Offline-Verfolgung {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the `ADBMobileConfig.json` file. All other offline configuration is done automatically.

Entfernen Sie im gesamten Code Aufrufe der folgenden Methoden:

### Migration von 3.x

* `SetOnline`
* `SetOffline`

## Variable „products“ {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Da die Variable „“ in Verarbeitungsregeln nicht verfügbar ist, können Sie die folgende Syntax zum Festlegen von `products`products verwenden:

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

In diesem Beispiel ist der Wert von `"&&products"` &quot; `";Cool Shoe`&quot;und sollte der Produktzeichenfolgen-Syntax für den Typ des Ereignisses folgen, das Sie verfolgen.