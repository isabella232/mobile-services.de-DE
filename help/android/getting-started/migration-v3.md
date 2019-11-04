---
description: Diese Informationen helfen Ihnen bei der Migration von Version 3.x bzw. 2.x der Android-Bibliothek zu Version 4.x.
keywords: Android;Bibliothek;Mobile;SDK
seo-description: Diese Informationen helfen Ihnen bei der Migration von Version 3.x bzw. 2.x der Android-Bibliothek zu Version 4.x.
seo-title: Migration zur Android 4.x-Bibliothek
solution: Experience Cloud,Analytics
title: Migration zur Android 4.x-Bibliothek
topic: Entwickler und Implementierung
uuid: 906e83bb-2faf-4aa2-ac9b-3fba6b833c7e
translation-type: ht
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migration zur Android 4.x-Bibliothek {#migrating-to-the-android-x-library}

Diese Informationen helfen Ihnen bei der Migration von Version 3.x bzw. 2.x der Android-Bibliothek zu Version 4.x.

>[!IMPORTANT]
>
>Das SDK verwendet `SharedPreferences` zum Speichern von Daten, die zur Berechnung von Unique Users und Lebenszyklusmetriken benötigt werden, und anderen mit SDK-Hauptfunktionen verbundenen Daten.  Wenn Sie in `SharedPreferences` die Werte, die vom SDK erwartet werden, ändern oder entfernen, kann dies zu unerwartetem Verhalten in Form von Dateninkonsistenzen führen.

In Version 4.x der Bibliothek werden die öffentlichen Methoden in einem Header zusammengeführt. Außerdem steht die Funktionalität jetzt auch über Methoden auf Klassenebenen zur Verfügung, damit Sie Pointer, Instanzen und Singletons nicht verfolgen müssen.

## Events, Props und eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

In Version 4 können Sie keine Variablen, wie z. B. events, eVars, props, heirs und lists, in Ihrer App zuweisen. Stattdessen nutzt das SDK Kontextdaten und Verarbeitungsregeln, um Ihre App-Daten zwecks Reporting Analytics-Variablen zuzuordnen.

Verarbeitungsregeln bieten folgende Vorteile:

* Sie können Ihre Datenzuweisung ändern, ohne ein Update im App Store einzureichen.
* Sie können relevante Namen für Ihre Daten verwenden, anstatt Variablen festzulegen, die spezifisch für eine Report Suite sind.
* Es ist kaum Aufwand nötig, um zusätzliche Daten zu senden.

   Diese Werte werden nicht in Berichten angezeigt, bis sie mithilfe von Verarbeitungsregeln zugeordnet wurden.

>[!TIP]
>
>Die Werte, die Sie Variablen direkt zugewiesen haben, müssen zur HashMap `data` hinzugefügt werden.

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

## Konfigurationsdateien verschieben und auf Version 4 migrieren {#section_0B844235E0B04DD4B36976A73DB28FB5}

Die folgende Tabelle enthält die Konfigurationsvariablen, die Sie in die Konfigurationsdatei verschieben müssen.

### Verschieben der Konfigurationsdatei

1. Verschieben Sie den Wert, der in der ersten Spalte festgelegt ist, zu der Variablen in der zweiten Spalte.
1. Entfernen Sie die alte Konfigurationsvariable aus Ihrem Code.

### Migration von Version 3.x

Um von Version 3.x auf Version 4 zu migrieren, verschieben Sie den Wert der Konfigurationsvariablen/Methode in die Variable `ADBMobileConfig.json`.

| Konfigurationsvariable oder -methode | Variable in der Datei `ADBMobileConfig.json` |
|--- |--- |
| setOfflineTrackingEnabled | „offlineEnabled“ |
| setOfflineHitLimit | „batchLimit“ |
| reportSuiteIDs | „rsids“ |
| trackingServer | „server“ |
| charSet | „charset“ |
| currencyCode | „currency“ |
| ssl | „ssl“ |
| linkTrackVars | Entfernen: Nicht länger verwendet. |
| linkTrackEvents | Entfernen: Nicht länger verwendet. |

### Migration von Version 2.x

Um von Version 2.x auf Version 4 zu migrieren, verschieben Sie den Wert aus der ersten Spalte in die Variable in der zweiten Spalte.

| Konfigurationsvariable | Variable in der Datei `ADBMobileConfig.json` |
| --- |--- |
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
| useBestPractices  Alle Aufrufe für massenhafte Messung (getChurnInstance) | Entfernen: Durch Lebenszyklusmetriken ersetzt. |

## Verfolgungsaufruf und -variablen aktualisieren {#section_96E7D9B3CDAC444789503B7E7F139AB9}

Anstelle der auf das Web ausgelegten Aufrufe `track` und `trackLink` verwendet Version 4 des SDK folgende Methoden:

* `trackState`, die den verfügbaren Ansichten in der App entsprechen, z. B. `home dashboard`, `app settings` und `cart`.

   Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `trackState`-Aufrufe inkrementieren die Seitenansichten.

* `trackAction`-Aktionen, wie z. B. `logons`, `banner taps`, `feed subscriptions` und andere, die in Ihrer App auftreten und die Sie messen möchten.

Der Parameter `contextData` für die beiden Methoden besteht aus einer `HashMap<String, Object>`, die Name/Wert-Paare enthält, die als Kontextdaten gesendet werden.

## Events, Props und eVars

In Version 4 ist es nicht mehr möglich, Variablen direkt in Ihrer App zuzuweisen, beispielsweise events, eVars, props, heirs und lists. Das SDK nutzt jetzt Kontextdaten und Verarbeitungsregeln, um Ihre App-Daten zwecks Reporting Analytics-Variablen zuzuordnen.

Verarbeitungsregeln bieten folgende Vorteile:

* Sie können Ihre Datenzuweisung ändern, ohne ein Update im App Store einzureichen.
* Sie können relevante Namen für Ihre Daten verwenden, anstatt Variablen festzulegen, die spezifisch für eine Report Suite sind.
* Es ist kaum Aufwand nötig, um zusätzliche Daten zu senden.

   Diese Werte werden nicht in Berichten angezeigt, bis sie mithilfe von Verarbeitungsregeln zugeordnet wurden. Weitere Informationen finden Sie unter [Verarbeitungsregeln und Kontextdaten](/help/android/getting-started/proc-rules.md).

Werte, die Sie Variablen direkt zugewiesen haben, müssen zur HashMap `data` hinzugefügt werden. Das bedeutet, dass Aufrufe von `setProp`, `setEvar` sowie Zuweisungen zu persistenten Kontextdaten entfernt und die Werte zum Parameter `data` hinzugefügt werden müssen.

## AppSection/Server, GeoZip, Transaktions-ID, Kampagne und andere Standardvariablen

Daten, die Sie für das Messobjekt festgelegt haben, einschließlich der oben aufgeführten Variablen, müssen zur HashMap `data` hinzugefügt werden. Die einzigen Daten, die mit dem Aufruf `trackState` oder `trackAction` gesendet werden, beinhalten die Nutzlast des Parameters `data`.

### Verfolgungsaufrufe ersetzen

Ersetzen Sie folgende Methoden durch einen Aufruf von `trackState` oder `trackAction`:

* **Migration von Version 3.x**

   * `trackAppState (trackState)`
   * `trackEvents (trackAction)`
   * `track (trackAction)`
   * `trackLinkURL (trackAction)`

* **Migration von Version 2.x**

   * `track (trackState)`
   * `trackLink (trackAction)`

## Benutzerspezifische Besucher-ID {#section_2CF930C13BA64F04959846E578B608F3}

Ersetzen Sie die Variable `visitorID` durch einen Aufruf von `setUserIdentifier`.

## Offline-Verfolgung {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Die Offline-Verfolgung wird in der Datei `ADBMobileConfig.json` aktiviert. Alle anderen Offline-Konfigurationen erfolgen automatisch.

Entfernen Sie Aufrufe der folgenden Methoden:

**Version 3.x**

* `setOnline`
* `setOffline`

**Version 2.x**

* `forceOffline`
* `forceOnline`

## Variable „products“ {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Weitere Informationen zur Variablen „products“ finden Sie unter [Variable „products“](/help/android/analytics-main/products/products.md).

