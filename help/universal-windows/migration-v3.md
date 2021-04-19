---
description: In diesem Abschnitt wird beschrieben, wie Sie von der 3.x-Version eines vorherigen Windows Mobile SDK auf das Universal Windows Platform 4.x SDK for Experience Cloud Solutions migrieren.
seo-description: In diesem Abschnitt wird beschrieben, wie Sie von der 3.x-Version eines vorherigen Windows Mobile SDK auf das Universal Windows Platform 4.x SDK for Experience Cloud Solutions migrieren.
seo-title: Migration zu 4.x
solution: Experience Cloud,Analytics
title: Migration zu 4.x
topic-fix: Developer and implementation
uuid: bdd6c5cd-3892-4e99-b69e-77105ad66e25
exl-id: 68de505b-dcff-4a78-9f01-b1d103846281
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 26%

---

# Zu den 4.x SDKs migrieren{#migrate-to-x}

In diesem Abschnitt wird beschrieben, wie Sie von der Version 3.x des Windows Mobile SDK auf das Universal Windows Platform 4.x SDK for Experience Cloud Solutions migrieren.

Mit der Umstellung auf Version 4.x können jetzt alle Funktionen über statische Methoden aufgerufen werden. Sie müssen keine eigenen Objekte mehr verfolgen.

Die folgenden Abschnitte führen Sie durch die Migration von Version 3.x auf Version 4.x.

## Ungenutzte Eigenschaften entfernen {#section_145222EAA20F4CC2977DD883FDDBBFC5}

Sie haben wahrscheinlich eine neue `ADBMobileConfig.json` Datei bemerkt, die in Ihrem Download enthalten ist. Diese Datei enthält anwendungsspezifische globale Einstellungen und ersetzt die meisten Konfigurationsvariablen, die in früheren Versionen verwendet wurden.

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

Die folgende Tabelle enthält die Konfigurationsvariablen, die Sie in die Konfigurationsdatei verschieben müssen. Verschieben Sie den für die Variable in der ersten Spalte eingestellten Wert in die Variable in der zweiten Spalte und entfernen Sie dann die alte Konfigurationsvariable aus Ihrem Code.

### Migration von 3.x

Die folgende Tabelle enthält eine Liste von Variablen in den 3.x-SDKs und den neuen Namen in den 4.x-SDKs:

| Konfigurationsvariable/Methode | Variable in der Datei `ADBMobileConfig.json`. |
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

Anstatt die webfokussierten `Track`- und `TrackLink`-Aufrufe zu verwenden, verwendet das SDK Version 4 zwei Methoden, die in der mobilen Welt etwas sinnvoller sind:

* `TrackState` Statusangaben sind die Ansichten, die in Ihrer App verfügbar sind, z. B. &quot;Home Dashboard&quot;, &quot;App-Einstellungen&quot;, &quot;Warenkorb&quot;usw. Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `trackState`-Aufrufe inkrementieren die Seitenansichten.

* `TrackAction` Aktionen sind die Vorgänge, die in Ihrer App stattfinden und die Sie messen möchten, z. B. &quot;Anmeldungen&quot;, &quot;Bannerklappen&quot;, &quot;Feed-Abonnement&quot;und andere Metriken. Durch diese Aufrufe werden die Ansichten der Seite nicht inkrementiert.

Der Parameter `contextData` für beide Methoden enthält Name-Wert-Paare, die als Kontextdaten gesendet werden.

### Events, Props und eVars

Wenn Sie sich die [SDK-Methoden](/help/universal-windows/c-configuration/methods.md) angesehen haben, fragen Sie sich wahrscheinlich, wo Sie Ereignis, eVars, Props, Erben und Listen festlegen können. In Version 4 können Sie diese Variablentypen nicht mehr direkt in Ihrer App zuweisen. Stattdessen verwendet das SDK Kontextdaten und Verarbeitungsregeln, um Ihre App-Daten Analytics-Variablen für die Berichterstellung zuzuordnen.

Verarbeitungsregeln bieten folgende Vorteile:

* Sie können Ihre Datenzuordnung ändern, ohne eine Aktualisierung an den Appstore zu senden.
* Sie können aussagekräftige Namen für Daten verwenden, anstatt Variablen festzulegen, die für eine Report Suite spezifisch sind.
* Das Senden zusätzlicher Daten hat geringe Auswirkungen. Diese Werte werden erst dann in Berichten angezeigt, wenn sie mithilfe von Verarbeitungsregeln zugeordnet werden.

Weitere Informationen finden Sie im Abschnitt *Verarbeitungsregeln* in [Analytics-Übersicht](/help/universal-windows/analytics/analytics.md).

Alle Werte, die Sie direkt Variablen zuweisen, sollten stattdessen den Kontextdaten hinzugefügt werden. Das bedeutet, dass Aufrufe von `SetProp`, `SetEvar` und Zuweisungen zu persistenten Kontextdaten entfernt und die Werte zu Kontextdaten hinzugefügt werden sollten.

### AppSection/Server, GeoZip, Transaktions-ID, Kampagne und andere Standardvariablen

Alle anderen Daten, die Sie für das Messungsobjekt eingestellt haben, einschließlich der oben aufgeführten Variablen, sollten stattdessen den Kontextdaten hinzugefügt werden. Das heißt, die einzigen Daten, die mit einem `TrackState`- oder `TrackAction`-Aufruf gesendet werden, sind die Nutzdaten im Parameter `data`.

**Verfolgungsaufrufe ersetzen**

Ersetzen Sie im gesamten Code die folgenden Methoden durch einen Aufruf von `trackState` oder `trackAction`:

**Migration von 3.x:**

* TrackAppState (TrackState)
* TrackEvents (TrackAction)
* Track (TrackAction)
* TrackLinkURL (TrackAction)

## Benutzerdefinierter ID-Dienst {#section_2CF930C13BA64F04959846E578B608F3}

Ersetzen Sie die Variable `visitorID` durch einen Aufruf von `setUserIdentifier`.

## Offline-Verfolgung {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Die Offline-Verfolgung ist in der Datei `ADBMobileConfig.json` aktiviert. Alle anderen Offlinekonfigurationen werden automatisch durchgeführt.

Entfernen Sie im gesamten Code Aufrufe der folgenden Methoden:

**Migration von 3.x:**

* SetOnline
* SetOffline

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

Der Wert von `"&&products"` (in diesem Beispiel ist der Wert `";Cool Shoe`&quot;) sollte der Produktzeichenfolgen-Syntax für den Typ des Ereignisses folgen, das Sie verfolgen.
