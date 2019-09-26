---
description: Informationen, die Ihnen bei der Verwendung der Konfigurationsdatei „ADBMobile JSON“ helfen.
seo-description: Informationen, die Ihnen bei der Verwendung der Konfigurationsdatei „ADBMobile JSON“ helfen.
seo-title: ADBMobileConfig.json config
solution: Marketing Cloud,Analytics
title: ADBMobileConfig.json config
topic: Entwickler und Implementierung
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# ADBMobileConfig.json config file {#adbmobileconfig-json-config}

Informationen, die Ihnen bei der Verwendung der Konfigurationsdatei „ADBMobile JSON“ helfen.

Das SDK unterstützt zurzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target und Audience Manager. Methoden erhalten je nach Lösung unterschiedliche Präfixe. Konfigurationsmethoden ist „Config“ als Präfix vorangestellt.

* **rsids**

   (**Required by Analytics**) One or more report suites to receive Analytics data. Verschiedene Report Suite-IDs müssen durch Kommas getrennt und ohne Leerzeichen zwischen den einzelnen Suites angegeben werden.

   * Hier finden Sie die Syntax für diese Methode:

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**Für Analytics und Zielgruppen-Management erforderlich**). Der Analytics- oder Zielgruppen-Management-Server, basierend auf dem übergeordneten Knoten. This variable should be populated with the server domain, without an `"https://"` or `"https://"` protocol prefix. Das Protokollpräfix wird anhand der Variable `ssl` automatisch von der Bibliothek verarbeitet.

   Wenn `ssl` auf `true` gesetzt ist, wird eine sichere Verbindung zu diesem Server hergestellt. Wenn `ssl` auf `false` gesetzt ist, wird eine nicht sichere Verbindung zu diesem Server hergestellt.

* **charset**

   Definiert den Zeichensatz, den Sie für die an Analytics gesendeten Daten verwenden. Der Zeichensatz wird verwendet, um eingehende Daten zum Speichern und Reporting in das UTF-8-Format umzuwandeln. For more information, see [s.charSet](https://marketing.adobe.com/resources/help/en_US/sc/implement/charset.html).

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (`HTTPS`). Der Standardwert lautet `false`.

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. Für Ihre Report Suite müssen Zeitstempel aktiviert sein, um die Offline-Verfolgung zu nutzen.

   If time stamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. if your report suite is not timestamp enabled, your `offlineEnabled` configuration property *must* be `false`.

   Wenn dies nicht ordnungsgemäß konfiguriert ist, gehen Daten verloren. If you are unsure whether a report suite is timestamp enabled, contact Customer Care. If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

   Der Standardwert lautet `false`.

* **lifecycleTimeout**

   Legt die Dauer in Sekunden fest, die zwischen verschiedenen Startvorgängen einer App verstreichen muss, damit ein Startvorgang als neue Sitzung gilt. Dieses Zeitlimit wird auch angewendet, wenn eine Anwendung in den Hintergrund verschoben und später reaktiviert wird. Die Dauer, für welche die App im Hintergrund ausgeführt wird, wird nicht in die Sitzungsdauer eingerechnet.

   Der Standardwert ist 300 Sekunden.

* **batchLimit**

   Sendet die Treffer als Stapel.

   For example, if set to `50`, hits are queued until 50 are stored, then all queued hits are sent. Requires , and the default value is  (No batching).`offlineEnabled=true``0`

* **privacyDefault**

   The options are:

   * `optedin` - Treffer werden sofort gesendet.
   * `optedout` - werden Treffer verworfen.
   * `optunknown`: Wenn für Ihre Report Suite Zeitstempel aktiviert sind, werden Treffer so lange gespeichert, bis der Datenschutzstatus in „opt-in“ (Treffer werden gesendet) oder „opt-out“ (Treffer werden verworfen) geändert wird. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

      Hiermit wird nur der Standardwert festgelegt. Wenn dieser Wert im Code eingestellt oder geändert wird, dann wird der vom Code eingestellte Wert lokal gespeichert und ab diesem Zeitpunkt verwendet, bis er geändert wird oder die Anwendung deinstalliert und dann wieder neu installiert wird.

      Der Standardwert lautet `optedin`.

* **poi**

   Jedes POI-Array beinhaltet den POI-Namen, den Längen- und Breitengrad sowie den Radius (in Metern) des POI-Bereichs. Für den POI-Namen kann eine beliebige Zeichenfolge gewählt werden. Wenn beim Senden eines `trackLocation`-Aufrufs die aktuellen Koordinaten zu einem definierten POI passen, wird eine Kontextdatenvariable gefüllt und zusammen mit dem `trackLocation`-Aufruf gesendet.

   * Here is the code sample for this variable:

      ```js
       "poi" [ 
                ["san francisco",37.757144,-122.44812,7000], 
                ["santa cruz",36.972935,-122.01725,600] 
             ]
      ```

* **clientCode**

   (**Required by Target**) Your assigned client code.

* **timeout**

   Bestimmt, wie lange Target auf eine Antwort wartet.

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
