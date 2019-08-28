---
description: Informationen, die Ihnen bei der Verwendung der Konfigurationsdatei „ADBMobile JSON“ helfen.
seo-description: Informationen, die Ihnen bei der Verwendung der Konfigurationsdatei „ADBMobile JSON“ helfen.
seo-title: config-Datei für adbmobileconfig. json
solution: Marketing Cloud, Analytics
title: config-Datei für adbmobileconfig. json
topic: Entwickler und Implementierung
uuid: a 45 b 91 cc -982 e -4 d 6 c-a 4 e 4-d 2 e 4 b 4 fa 7556
translation-type: tm+mt
source-git-commit: 1dbdb998228bd3b0ae41e774b6e9aa111d8dbe1c

---


# `ADBMobileConfig.json` config-Datei {#adbmobileconfig-json-config}

Information to help you use the `ADBMobile.json` config file.

Das SDK unterstützt zurzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target und Audience Manager. Methoden erhalten je nach Lösung unterschiedliche Präfixe. Konfigurationsmethoden ist „Config“ als Präfix vorangestellt.

* **rsids**

   (Für Analytics erforderlich) Eine oder mehrere Report Suites für den Erhalt von Analytics-Daten. Verschiedene Report Suite-IDs müssen durch Kommas getrennt und ohne Leerzeichen zwischen den einzelnen Suites angegeben werden.

   * Hier finden Sie die Codebeispiele für diese Variable:

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (Für Analytics und Zielgruppen-Management erforderlich). Der Analytics- oder Zielgruppen-Management-Server, basierend auf dem übergeordneten Knoten. This variable should be populated with the server domain, without an `https://` or `https://` protocol prefix. Das Protokollpräfix wird anhand der Variable `ssl` automatisch von der Bibliothek verarbeitet.

   Wenn `ssl` auf `true` gesetzt ist, wird eine sichere Verbindung zu diesem Server hergestellt. Wenn `ssl` auf `false` gesetzt ist, wird eine nicht sichere Verbindung zu diesem Server hergestellt.

* **charset**

   Definiert den Zeichensatz, den Sie für die an Analytics gesendeten Daten verwenden. Der Zeichensatz wird verwendet, um eingehende Daten zum Speichern und Reporting in das UTF-8-Format umzuwandeln. For more information, see [s.charSet](https://marketing.adobe.com/resources/help/en_US/sc/implement/charset.html).

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (HTTPS). Der Standardwert lautet `false`.

* **offlineEnabled**

   Wenn aktiviert (true), werden Treffer in die Warteschlange versetzt, während das Gerät offline ist, und später gesendet, wenn das Gerät online ist. Für Ihre Report Suite müssen Zeitstempel aktiviert sein, um die Offline-Verfolgung zu nutzen.

   >[!IMPORTANT]
   >
   >IIf time stamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be true. Wenn Zeitstempel nicht für Ihre Report Suite aktiviert sind, `offlineEnabled`muss die Konfigurationseigenschaft ** „false“ lauten. Wenn dies nicht ordnungsgemäß konfiguriert ist, gehen Daten verloren. Wenn Sie sich nicht sicher sind, ob Zeitstempel für Ihre Report Suite aktiviert sind, wenden Sie sich bitte an Kundenunterstützung. Wenn Sie aktuell AppMeasurement-Daten in einer Report Suite erfassen, in der auch Daten aus JavaScript gesammelt werden, müssen Sie möglicherweise eine separate Report Suite für mobile Daten einrichten oder einen benutzerdefinierten Zeitstempel für JavaScript-Treffer einfügen, die die Variable `s.timestamp` nutzen.

* **lifecycleTimeout**

   Legt die Dauer in Sekunden fest, die zwischen verschiedenen Startvorgängen einer App verstreichen muss, damit ein Startvorgang als neue Sitzung gilt. Dieses Zeitlimit wird auch angewendet, wenn eine Anwendung in den Hintergrund verschoben und später reaktiviert wird. Die Dauer, für die die App im Hintergrund ausgeführt wird, wird nicht in die Sitzungsdauer eingerechnet. Der Standardwert ist 300 Sekunden.

* **batchLimit**

   Sendet die Treffer als Stapel. Wenn der Wert 50 festgelegt wird, werden Treffer in der Warteschlange gespeichert, bis eine Anzahl von 50 erreicht ist, die dann zusammen gesendet werden. Erforderlich `offlineEnabled=true`. Der Standardwert ist `0` (Kein Stapel).

* **privacyDefault**

   * `optedin` - Treffer werden sofort gesendet.
   * `optedout` - werden Treffer verworfen.
   * `optunknown`: Wenn für Ihre Report Suite Zeitstempel aktiviert sind, werden Treffer so lange gespeichert, bis der Datenschutzstatus in „opt-in“ (Treffer werden gesendet) oder „opt-out“ (Treffer werden verworfen) geändert wird. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

      Der Standardwert lautet `optedin`.

      >[!TIP]
      >
      >Dadurch wird nur der Standardwert festgelegt. Wenn dieser Wert im Code eingestellt oder geändert wird, dann wird der vom Code eingestellte Wert lokal gespeichert und ab diesem Zeitpunkt verwendet, bis er geändert wird oder die Anwendung deinstalliert und dann wieder neu installiert wird.

* **poi**

   Jedes POI-Array beinhaltet den POI-Namen, den Längen- und Breitengrad sowie den Radius (in Metern) des POI-Bereichs. Für den POI-Namen kann eine beliebige Zeichenfolge gewählt werden. Wenn beim Senden eines `trackLocation`-Aufrufs die aktuellen Koordinaten zu einem definierten POI passen, wird eine Kontextdatenvariable gefüllt und zusammen mit dem `trackLocation`-Aufruf gesendet.

   * Hier finden Sie das Codebeispiel für diese Variable:

      ```js
      "poi": [
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

