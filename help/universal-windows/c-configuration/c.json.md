---
description: Informationen zur Verwendung der ADBMobile JSON-Konfigurationsdatei.
seo-description: Informationen zur Verwendung der ADBMobile JSON-Konfigurationsdatei.
seo-title: ADBMobileConfig.json config
solution: Experience Cloud,Analytics
title: ADBMobileConfig.json config
topic: Developer and implementation
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 39%

---


# ADBMobileConfig.json config file {#adbmobileconfig-json-config}

Informationen zur Verwendung der ADBMobile JSON-Konfigurationsdatei.

Das SDK unterstützt derzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Zielgruppe und Audience Manager. Methoden erhalten je nach Lösung unterschiedliche Präfixe. Konfigurationsmethoden erhalten das Präfix &quot;Config&quot;.

* **rsids**

   (**Erforderlich für Analytics**) Eine oder mehrere Report Suites zum Empfang von Analytics-Daten. Mehrere Report Suite-IDs sollten durch Kommata getrennt werden, wobei kein Leerzeichen dazwischen steht.

   * Hier finden Sie die Syntax für diese Methode:

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**Erforderlich für Analytics und Audience-Management**). Analytics- oder Audience Management-Server, basierend auf dem übergeordneten Knoten. Diese Variable sollte mit der Serverdomäne aufgefüllt werden, und zwar ohne das Protokollpräfix `"https://"` oder `"https://"`. Das Protokollpräfix wird automatisch von der Bibliothek auf Basis der `ssl` Variablen verarbeitet.

   Wenn `ssl` auf `true` gesetzt ist, wird eine sichere Verbindung zu diesem Server hergestellt. Wenn `ssl` auf `false` gesetzt ist, wird eine nicht sichere Verbindung zu diesem Server hergestellt.

* **charset**

   Definiert den Zeichensatz, den Sie für die an Analytics gesendeten Daten verwenden. Der Zeichensatz wird verwendet, um eingehende Daten zum Speichern und Reporting in das UTF-8-Format umzuwandeln. Weitere Informationen dazu finden Sie unter [s.charSet](https://docs.adobe.com/content/help/de-DE/analytics/implementation/vars/config-vars/charset.html).

* **ssl**

   Aktiviert (`true`) oder deaktiviert (`false`) das Senden von Messungsdaten über SSL (`HTTPS`). Der Standardwert lautet `false`.

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. Für Ihre Report Suite müssen Zeitstempel aktiviert sein, um die Offline-Verfolgung zu nutzen.

   If time stamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. if your report suite is not timestamp enabled, your `offlineEnabled` configuration property *must* be `false`.

   Wenn dies nicht ordnungsgemäß konfiguriert ist, gehen Daten verloren. Wenn Sie nicht sicher sind, ob eine Report Suite zeitstempelfähig ist, wenden Sie sich an den Kundendienst. If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

   Der Standardwert lautet `false`.

* **lifecycleTimeout**

   Gibt die Zeitdauer in Sekunden an, die vergehen muss, bevor der Start als neue Sitzung gezählt wird. Dieses Time-out gilt auch, wenn Ihre Anwendung in den Hintergrund gestellt und reaktiviert wird. Die Zeit, die Ihre App im Hintergrund ist, ist nicht in der Sitzungslänge enthalten.

   Der Standardwert ist 300 Sekunden.

* **batchLimit**

   Senden von Treffern in Stapeln

   Wenn Sie beispielsweise auf `50`setzen, werden Treffer in die Warteschlange gestellt, bis 50 gespeichert sind, dann werden alle Treffer in der Warteschlange gesendet. Erfordert `offlineEnabled=true`, und der Standardwert ist `0` (Keine Stapelverarbeitung).

* **privacyDefault**

   Die Optionen sind:

   * `optedin`: Treffer werden umgehend gesendet.
   * `optedout`: werden Treffer verworfen.
   * `optunknown` - Wenn Ihre Report Suite zeitstempelfähig ist, werden die Treffer gespeichert, bis der Datenschutzstatus in &quot;opt-in&quot;(Zugriffe werden gesendet) oder &quot;opt-out&quot;(Zugriffe werden dann verworfen) geändert wird. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

      Hiermit wird nur der Standardwert festgelegt. Wenn dieser Wert jemals im Code festgelegt oder geändert wird, wird der vom Code eingestellte Wert in lokaler Datenspeicherung gespeichert und so lange verwendet, bis er geändert wird, oder die App wird deinstalliert und dann neu installiert.

      Der Standardwert lautet `optedin`.

* **poi**

   Jedes POI-Array beinhaltet den POI-Namen, den Längen- und Breitengrad sowie den Radius (in Metern) des POI-Bereichs. Für den POI-Namen kann eine beliebige Zeichenfolge gewählt werden. Wenn beim Senden eines `trackLocation`-Aufrufs die aktuellen Koordinaten zu einem definierten POI passen, wird eine Kontextdatenvariable gefüllt und zusammen mit dem `trackLocation`-Aufruf gesendet.

   * Das folgende Codebeispiel für diese Variable:

      ```js
       "poi" [ 
                ["san francisco",37.757144,-122.44812,7000], 
                ["santa cruz",36.972935,-122.01725,600] 
             ]
      ```

* **clientCode**

   (**Erforderlich nach Zielgruppe**) Ihr zugewiesener Clientcode.

* **timeout**

   Bestimmt, wie lange die Zielgruppe auf eine Antwort wartet.

The following is an example of an `ADBMobileConfig.json` file:

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
  "timeout" : 1
 },
 "audienceManager" : {
  "server" : "myServer.demdex.com"
 }
}
```
