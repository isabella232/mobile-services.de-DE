---
description: Informationen zur Verwendung der ADBMobile-JSON-Konfigurationsdatei.
solution: Experience Cloud Services,Analytics
title: Konfigurationsdatei "ADBMobileConfig.json"
topic-fix: Developer and implementation
uuid: a45b91cc-982e-4d6c-a4e4-d2e4b4fa7556
exl-id: 520dffb8-ca47-444f-bbc9-f18413ddeb05
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 46%

---

# `ADBMobileConfig.json` Konfigurationsdatei {#adbmobileconfig-json-config}

Informationen zur Verwendung der `ADBMobile.json` Konfigurationsdatei.

Das SDK unterstützt derzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target und Audience Manager. Methoden erhalten je nach Lösung unterschiedliche Präfixe. Konfigurationsmethoden erhalten das Präfix &quot;Konfiguration&quot;.

* **rsids**

   (Für Analytics erforderlich) Eine oder mehrere Report Suites für den Empfang von Analytics-Daten. Mehrere Report Suite-IDs sollten durch Kommata getrennt werden, wobei kein Leerzeichen dazwischen steht.

   * Im Folgenden finden Sie Codebeispiele für diese Variable:

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (Für Analytics und Zielgruppen-Management erforderlich). Analytics- oder Zielgruppen-Management-Server, basierend auf dem übergeordneten Knoten. Diese Variable sollte mit der Serverdomäne aufgefüllt werden, und zwar ohne das Protokollpräfix `https://` oder `https://`. Das Protokollpräfix wird automatisch von der Bibliothek verarbeitet, die auf dem `ssl` -Variable.

   Wenn `ssl` auf `true` gesetzt ist, wird eine sichere Verbindung zu diesem Server hergestellt. Wenn `ssl` auf `false` gesetzt ist, wird eine nicht sichere Verbindung zu diesem Server hergestellt.

* **charset**

   Definiert den Zeichensatz, den Sie für die an Analytics gesendeten Daten verwenden. Der Zeichensatz wird verwendet, um eingehende Daten zum Speichern und Reporting in das UTF-8-Format umzuwandeln. Weitere Informationen finden Sie unter [charSet](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/charset.html?lang=de) in der Adobe Analytics-Dokumentation.

* **ssl**

   Aktiviert (`true`) oder deaktiviert (`false`) Messdaten über SSL (HTTPS) senden. Der Standardwert lautet `false`.

* **offlineEnabled**

   Bei Aktivierung (true) werden Treffer in die Warteschlange gestellt, während das Gerät offline ist, und später gesendet, wenn das Gerät online ist. Für Ihre Report Suite müssen Zeitstempel aktiviert sein, um die Offline-Verfolgung zu nutzen.

   >[!IMPORTANT]
   >
   >Wenn Zeitstempel für Ihre Report Suite aktiviert sind, wird Ihr `offlineEnabled` Konfigurationseigenschaft *must* wahr sein. Wenn Zeitstempel nicht für Ihre Report Suite aktiviert sind, `offlineEnabled` *muss* die Konfigurationseigenschaft „false“ lauten. Wenn dies nicht ordnungsgemäß konfiguriert ist, gehen Daten verloren. Wenn Sie sich nicht sicher sind, ob Zeitstempel für Ihre Report Suite aktiviert sind,   wenden Sie sich bitte an   Kundenunterstützung. Wenn Sie aktuell AppMeasurement-Daten in einer Report Suite erfassen, in der auch Daten aus JavaScript gesammelt werden, müssen Sie möglicherweise eine separate Report Suite für mobile Daten einrichten oder einen benutzerdefinierten Zeitstempel für alle JavaScript-Treffer einfügen, die die `s.timestamp` -Variable.

* **lifecycleTimeout**

   Gibt die Dauer in Sekunden an, die zwischen dem App-Starts verstreichen muss, damit der Start als neue Sitzung erachtet wird. Dieses Time-out gilt auch, wenn Ihre Anwendung in den Hintergrund gestellt und reaktiviert wird. Die Zeit, die Ihre App im Hintergrund ist, ist nicht in der Sitzungslänge enthalten. Der Standardwert ist 300 Sekunden.

* **batchLimit**

   Treffer in Batches senden. Wenn Sie beispielsweise auf 50 festlegen, werden Treffer in die Warteschlange gestellt, bis 50 gespeichert sind, dann werden alle Treffer in der Warteschlange gesendet. Erfordert `offlineEnabled=true`. Der Standardwert ist `0` (Keine Stapelverarbeitung).

* **privacyDefault**

   * `optedin`: Treffer werden umgehend gesendet.
   * `optedout`: werden Treffer verworfen.
   * `optunknown` - Wenn für Ihre Report Suite Zeitstempel aktiviert sind, werden die Treffer gespeichert, bis der Datenschutzstatus zu &quot;opt-in&quot;(anschließend werden die Treffer gesendet) oder &quot;opt-out&quot;(anschließend werden die Treffer verworfen) geändert wird. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

      Der Standardwert lautet `optedin`.

      >[!TIP]
      >
      >Dadurch wird nur der Standardwert festgelegt. Wenn dieser Wert im Code festgelegt oder geändert wird, wird der vom Code eingestellte Wert im lokalen Speicher gespeichert und verwendet, bis er geändert wird, oder die App wird deinstalliert und dann neu installiert.

* **poi**

   Jedes POI-Array beinhaltet den POI-Namen, den Längen- und Breitengrad sowie den Radius (in Metern) des POI-Bereichs. Für den POI-Namen kann eine beliebige Zeichenfolge gewählt werden. Wenn beim Senden eines `trackLocation`-Aufrufs die aktuellen Koordinaten zu einem definierten POI passen, wird eine Kontextdatenvariable gefüllt und zusammen mit dem `trackLocation`-Aufruf gesendet.

   * Hier finden Sie ein Code-Beispiel für diese Variable:

      ```js
      "poi": [
                  ["san francisco",37.757144,-122.44812,7000], 
                  ["santa cruz",36.972935,-122.01725,600] 
              ]
      ```

* **clientCode**

   (**Erforderlich für Target**) Ihr zugewiesener Clientcode.

* **timeout**

   Bestimmt, wie lange Target auf eine Antwort wartet.

Im Folgenden finden Sie ein Beispiel für eine `ADBMobileConfig.json` Datei:

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
