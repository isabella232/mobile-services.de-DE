---
description: Informationen zur Verwendung der ADBMobile JSON-Konfigurationsdatei.
seo-description: Informationen zur Verwendung der ADBMobile JSON-Konfigurationsdatei.
seo-title: ADBMobileConfig.json config
solution: Experience Cloud,Analytics
title: ADBMobileConfig.json config
topic-fix: Developer and implementation
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
exl-id: 57d50d30-651c-4943-835e-1cbce7467baf
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 43%

---

# ADBMobileConfig.json-Konfigurationsdatei {#adbmobileconfig-json-config}

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

   (**Erforderlich für Analytics und Audience-Management**). Analytics- oder Audience Management-Server, basierend auf dem übergeordneten Knoten. Diese Variable sollte mit der Serverdomäne aufgefüllt werden, und zwar ohne das Protokollpräfix `"https://"` oder `"https://"`. Das Protokollpräfix wird automatisch von der Bibliothek verarbeitet, basierend auf der Variablen `ssl`.

   Wenn `ssl` auf `true` gesetzt ist, wird eine sichere Verbindung zu diesem Server hergestellt. Wenn `ssl` auf `false` gesetzt ist, wird eine nicht sichere Verbindung zu diesem Server hergestellt.

* **charset**

   Definiert den Zeichensatz, den Sie für die an Analytics gesendeten Daten verwenden. Der Zeichensatz wird verwendet, um eingehende Daten zum Speichern und Reporting in das UTF-8-Format umzuwandeln. Weitere Informationen dazu finden Sie unter [s.charSet](https://docs.adobe.com/content/help/de-DE/analytics/implementation/vars/config-vars/charset.html).

* **ssl**

   Aktiviert (`true`) oder deaktiviert (`false`) das Senden von Messungsdaten über SSL (`HTTPS`). Der Standardwert lautet `false`.

* **offlineEnabled**

   Bei Aktivierung (`true`) werden Treffer in die Warteschlange gestellt, während das Gerät offline ist, und später gesendet, wenn das Gerät online ist. Für Ihre Report Suite müssen Zeitstempel aktiviert sein, um die Offline-Verfolgung zu nutzen.

   Wenn in Ihrer Report Suite Zeitstempel aktiviert sind, muss Ihre `offlineEnabled` Konfigurationseigenschaft ** `true`  sein. Wenn Ihre Report Suite nicht zeitstempelfähig ist, muss Ihre `offlineEnabled` Konfigurationseigenschaft ** `false`  sein.

   Wenn dies nicht ordnungsgemäß konfiguriert ist, gehen Daten verloren. Wenn Sie nicht sicher sind, ob eine Report Suite zeitstempelfähig ist, wenden Sie sich an den Kundendienst. Wenn Sie derzeit AppMeasurement-Daten an eine Report Suite senden, die auch Daten aus JavaScript erfasst, müssen Sie möglicherweise eine separate Report Suite für Mobildaten einrichten oder einen benutzerspezifischen Zeitstempel für alle JavaScript-Treffer mit der Variablen `s.timestamp` einfügen.

   Der Standardwert lautet `false`.

* **lifecycleTimeout**

   Gibt die Dauer in Sekunden an, die zwischen dem App-Starts verstreichen muss, damit der Start als neue Sitzung erachtet wird. Dieses Time-out gilt auch, wenn Ihre Anwendung in den Hintergrund gestellt und reaktiviert wird. Die Zeit, die Ihre App im Hintergrund ist, ist nicht in der Sitzungslänge enthalten.

   Der Standardwert ist 300 Sekunden.

* **batchLimit**

   Senden von Treffern in Stapeln

   Wenn Sie beispielsweise auf `50` setzen, werden Treffer in die Warteschlange gestellt, bis 50 gespeichert sind, dann werden alle Treffer in der Warteschlange gesendet. Erfordert `offlineEnabled=true` und der Standardwert ist `0` (Keine Stapelverarbeitung).

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

   (**Erforderlich durch Zielgruppe**) Ihr zugewiesener Clientcode.

* **timeout**

   Bestimmt, wie lange die Zielgruppe auf eine Antwort wartet.

Das folgende Beispiel zeigt eine `ADBMobileConfig.json`-Datei:

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
