---
description: Informationen zur Verwendung der ADBMobile-JSON-Konfigurationsdatei.
solution: Experience Cloud,Analytics
title: ADBMobileConfig.json config
topic-fix: Developer and implementation
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
exl-id: 57d50d30-651c-4943-835e-1cbce7467baf
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 42%

---

# Konfigurationsdatei &quot;ADBMobileConfig.json&quot; {#adbmobileconfig-json-config}

Informationen zur Verwendung der ADBMobile-JSON-Konfigurationsdatei.

Das SDK unterstützt derzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target und Audience Manager. Methoden erhalten je nach Lösung unterschiedliche Präfixe. Konfigurationsmethoden erhalten das Präfix &quot;Konfiguration&quot;.

* **rsids**

   (**Erforderlich für Analytics**) Eine oder mehrere Report Suites für den Empfang von Analytics-Daten. Mehrere Report Suite-IDs sollten durch Kommata getrennt werden, wobei kein Leerzeichen dazwischen steht.

   * Hier finden Sie die Syntax für diese Methode:

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**Erforderlich für Analytics und Zielgruppen-Management**). Analytics- oder Zielgruppen-Management-Server, basierend auf dem übergeordneten Knoten. Diese Variable sollte mit der Serverdomäne aufgefüllt werden, und zwar ohne das Protokollpräfix `"https://"` oder `"https://"`. Das Protokollpräfix wird automatisch von der Bibliothek basierend auf der Variablen `ssl` verarbeitet.

   Wenn `ssl` auf `true` gesetzt ist, wird eine sichere Verbindung zu diesem Server hergestellt. Wenn `ssl` auf `false` gesetzt ist, wird eine nicht sichere Verbindung zu diesem Server hergestellt.

* **charset**

   Definiert den Zeichensatz, den Sie für die an Analytics gesendeten Daten verwenden. Der Zeichensatz wird verwendet, um eingehende Daten zum Speichern und Reporting in das UTF-8-Format umzuwandeln. Weitere Informationen finden Sie unter der Variablen [charSet](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/charset.html?lang=de) in der Adobe Analytics-Dokumentation.

* **ssl**

   Aktiviert (`true`) oder deaktiviert (`false`) das Senden von Messungsdaten über SSL (`HTTPS`). Der Standardwert lautet `false`.

* **offlineEnabled**

   Wenn aktiviert (`true`), werden Treffer in die Warteschlange gestellt, während das Gerät offline ist, und später gesendet, wenn das Gerät online ist. Für Ihre Report Suite müssen Zeitstempel aktiviert sein, um die Offline-Verfolgung zu nutzen.

   Wenn Zeitstempel für Ihre Report Suite aktiviert sind, muss die Konfigurationseigenschaft *muss* `true` `offlineEnabled` sein. Wenn Zeitstempel nicht für Ihre Report Suite aktiviert sind, muss die Konfigurationseigenschaft *muss* `false` `offlineEnabled` sein.

   Wenn dies nicht ordnungsgemäß konfiguriert ist, gehen Daten verloren. Wenn Sie nicht sicher sind, ob Zeitstempel für eine Report Suite aktiviert sind, wenden Sie sich an die Kundenunterstützung. Wenn Sie aktuell AppMeasurement-Daten in einer Report Suite erfassen, in der auch Daten aus JavaScript gesammelt werden, müssen Sie möglicherweise eine separate Report Suite für mobile Daten einrichten oder einen benutzerdefinierten Zeitstempel für alle JavaScript-Treffer einfügen, die die Variable `s.timestamp` verwenden.

   Der Standardwert lautet `false`.

* **lifecycleTimeout**

   Gibt die Dauer in Sekunden an, die zwischen dem App-Starts verstreichen muss, damit der Start als neue Sitzung erachtet wird. Dieses Time-out gilt auch, wenn Ihre Anwendung in den Hintergrund gestellt und reaktiviert wird. Die Zeit, die Ihre App im Hintergrund ist, ist nicht in der Sitzungslänge enthalten.

   Der Standardwert ist 300 Sekunden.

* **batchLimit**

   Treffer in Batches senden.

   Wenn beispielsweise auf `50` gesetzt, werden Treffer in die Warteschlange gestellt, bis 50 gespeichert sind, dann werden alle Treffer in der Warteschlange gesendet. Erfordert `offlineEnabled=true` und der Standardwert ist `0` (keine Stapelverarbeitung).

* **privacyDefault**

   Die Optionen sind:

   * `optedin`: Treffer werden umgehend gesendet.
   * `optedout`: werden Treffer verworfen.
   * `optunknown` - Wenn für Ihre Report Suite Zeitstempel aktiviert sind, werden die Treffer gespeichert, bis der Datenschutzstatus zu &quot;opt-in&quot;(anschließend werden die Treffer gesendet) oder &quot;opt-out&quot;(anschließend werden die Treffer verworfen) geändert wird. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

      Dadurch wird nur der Standardwert festgelegt. Wenn dieser Wert im Code festgelegt oder geändert wird, wird der vom Code eingestellte Wert im lokalen Speicher gespeichert und verwendet, bis er geändert wird, oder die App wird deinstalliert und dann neu installiert.

      Der Standardwert lautet `optedin`.

* **poi**

   Jedes POI-Array beinhaltet den POI-Namen, den Längen- und Breitengrad sowie den Radius (in Metern) des POI-Bereichs. Für den POI-Namen kann eine beliebige Zeichenfolge gewählt werden. Wenn beim Senden eines `trackLocation`-Aufrufs die aktuellen Koordinaten zu einem definierten POI passen, wird eine Kontextdatenvariable gefüllt und zusammen mit dem `trackLocation`-Aufruf gesendet.

   * Hier finden Sie ein Code-Beispiel für diese Variable:

      ```js
       "poi" [ 
                ["san francisco",37.757144,-122.44812,7000], 
                ["santa cruz",36.972935,-122.01725,600] 
             ]
      ```

* **clientCode**

   (**Erforderlich für Target**) Ihr zugewiesener Clientcode.

* **timeout**

   Bestimmt, wie lange das Ziel auf eine Antwort wartet.

Im Folgenden finden Sie ein Beispiel für eine `ADBMobileConfig.json` -Datei:

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
