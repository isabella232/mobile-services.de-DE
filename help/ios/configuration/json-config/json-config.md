---
description: Diese Informationen helfen Ihnen bei der Verwendung der ADBMobile.json-Konfigurationsdatei.
seo-description: Diese Informationen helfen Ihnen bei der Verwendung der ADBMobile.json-Konfigurationsdatei.
seo-title: ADBMobile JSON-Konfiguration
solution: Marketing Cloud,Analytics
title: ADBMobile JSON-Konfiguration
topic: Developer and implementation
uuid: d9708d59-e30a-4f6c-ab1b-d9499855d0c2
translation-type: tm+mt
source-git-commit: 86ba045b44bf6553e80727c0d61ccdd9a552d16c
workflow-type: tm+mt
source-wordcount: '1715'
ht-degree: 98%

---


# ADBMobile JSON-Konfiguration {#adbmobile-json-config}

Diese Informationen helfen Ihnen bei der Verwendung der Konfigurationsdatei `ADBMobile.json`.

## Referenz zur Konfigurationsdatei „ADBMobileConfig.json“ {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

Sie können die Konfigurationsdatei für Ihre App über mehrere Plattformen hinweg verwenden:

>[!TIP]
>
>Unter **iOS** können Sie die Datei `ADBMobileConfig.json` an jedem beliebigen Speicherort ablegen, auf den vom Bundle aus zugegriffen werden kann.

* **acquisition**

   Aktiviert die Mobile App-Akquise.

   Wenn dieser Abschnitt fehlt, aktivieren Sie die App-Akquise und laden Sie die SDK-Konfigurationsdatei erneut herunter. Weitere Informationen finden Sie unten unter *referrerTimeout*.

   * `server`: Akquiseserver, der beim ersten Start für einen Akquise-Referrer überprüft wird.
   * `appid`: Generierte ID, die diese App auf dem Akquiseserver eindeutig identifiziert.
   * Mindestens SDK-Version 4.1

* **analyticsForwardingEnabled**

   Die Eigenschaft im Objekt `audienceManager`. Wenn `Audience Manager` konfiguriert ist und `analyticsForwardingEnabled` auf `true` festgelegt ist, wird der gesamte Analytics-Datenverkehr ebenfalls an Audience Manager weitergeleitet. Der Standardwert lautet `false`.

   * Mindestens SDK-Version 4.8.0

* **backdateSessionInfo**

   Aktiviert/Deaktiviert die Möglichkeit, dass das Adobe-SDK Treffer mit Sitzungsinformationen zurückdatiert.

   Sitzungsinformationstreffer bestehen derzeit aus Abstürzen und Sitzungslängen und können aktiviert oder deaktiviert werden.

   * Wenn Sie den Wert auf `false` einstellen, werden die Treffer **deaktiviert**.

      Das SDK kehrt zum Verhalten vor 4.1 zurück, bei dem die Sitzungsinformationen für die vorherige Sitzung mit dem ersten Treffer der nachfolgenden Sitzung zusammengefasst wurden. Das Adobe-SDK fügt die Sitzungsinformationen auch an den aktuellen Lebenszyklus an, wodurch keine zu hohen Besuchszahlen erstellt werden. Da keine zu hohen Besuchszahlen mehr erstellt werden, tritt eine unmittelbare Reduktion der Besuchszahlen auf.

   * Wenn Sie keinen Wert einstellen, lautet der Standardwert `true` und Treffer werden **aktiviert**.

      Wenn die Treffer aktiviert sind, datiert das Adobe SDK den Sitzungsinformationstreffer auf 1 Sekunde nach dem letzten Treffer in der vorherigen Sitzung zurück. Das bedeutet, dass Absturz- und Sitzungsdaten dem korrekten Datum, an dem sie aufgetreten sind, entsprechen. Als eine Auswirkung davon könnte das SDK einen Besuch für den rückdatierten Treffer erstellen. Bei jedem Neustart der App wird ein Treffer zurückdatiert.

   * Mindestens SDK-Version 4.6
   >[!IMPORTANT]
   >
   >Zurückdatierte Sitzungstrefferinformationen werden in einem Sitzungsinformations-Server-Aufruf gesendet und zusätzliche Server-Aufrufe werden ggf. angewendet.


* **batchLimit**

   Grenzwert für die Anzahl der Treffer, die in aufeinanderfolgenden Aufrufen gesendet werden sollen. Wenn beispielsweise `batchLimit` auf 10 festgelegt ist, wird jeder Treffer vor dem 10. Treffer in der Warteschlange gespeichert. Beim 10. Treffer werden alle 10 Treffer nacheinander gesendet.

   * Der Standardwert lautet `0`. Das bedeutet, dass die Stapelverarbeitung nicht aktiviert ist.
   * Erfordert `offlineEnabled = true`.
   * Mindestens SDK-Version 4.1

* **charset**

   Definiert den Zeichensatz, den Sie für die an Analytics gesendeten Daten verwenden. Der Zeichensatz wird verwendet, um eingehende Daten zum Speichern und Reporting in das UTF-8-Format umzuwandeln. Weitere Informationen dazu finden Sie unter [s.charSet](https://docs.adobe.com/content/help/en/analytics/implementation/vars/config-vars/charset.html).

   * Mindestens SDK-Version 4.0

* **clientCode**

   Ihr zugewiesener Client-Code.

   >[!IMPORTANT]
   >
   >Diese Variable ist für Target erforderlich.

   * Mindestens SDK-Version 4.0

* **coopUnsafe**

   For Device Co-op members who require this value be set to `true`, you need to work with the Co-op team to request a blocklist flag on your Device Co-op account. Es gibt keinen Self-Service-Pfad zum Aktivieren dieser Kennzeichnungen.

   Beachten Sie die folgenden Informationen:

   * Wenn `coopUnsafe` auf `true` festgelegt ist, wird `coop_unsafe=1` immer an Audience Manager und Besucher-ID-Treffer angehängt.
   * Wenn Sie die serverseitige Weiterleitung von Analytics an Audience Manager aktivieren, sehen Sie auch `coop_unsafe=1` in den Analytics-Treffern.

   Zusätzliche Informationen:

   * Mindestens SDK-Version 4.16.1
   * Die boolesche Eigenschaft des Objekts `marketingCloud`, das, wenn auf `true` festgelegt, dazu führt, dass das Gerät aus der Experience Cloud-Gerätekooperation ausgeschlossen wird.
   * Der Standardwert ist `false`.
   * Diese Einstellung wird **nur** für Kunden verwendet, die an der Gerätekooperation teilnehmen.



* **environmentId**

   Die ID der Umgebung, die Sie verwenden möchten. Sie können eine gültige ID angeben (`environmentId=8`). Wenn `environmentId` nicht enthalten ist, wird die standardmäßige Produktionsumgebung verwendet.

   * Mindestens SDK-Version 4.14

* **lifecycleTimeout**

   Der Standardwert ist 300 Sekunden.

   Gibt die Dauer in Sekunden an, die zwischen dem Start der App und dem Moment verstreichen muss, in dem die App als neue Sitzung erachtet wird. Dieses Time-out gilt auch, wenn Ihre Anwendung in den Hintergrund gestellt und reaktiviert wird. Die Zeit, die Ihre App im Hintergrund ist, ist nicht in der Sitzungslänge enthalten.

   * Mindestens SDK-Version 4.0

* **messages**

   Wird automatisch von Adobe Mobile Services generiert und definiert die Einstellungen für In-App-Nachrichten. Weitere Informationen finden Sie unten im Abschnitt *Nachrichtenbeschreibung*.

   * Mindestens SDK-Version 4.2

* **offlineEnabled**

   Ist diese Option aktiviert, werden Treffer in die Warteschlange aufgenommen, während das Gerät offline ist, und erst gesendet, wenn es wieder online ist. Für Ihre Report Suite müssen Zeitstempel aktiviert sein, um die Offline-Verfolgung zu nutzen. Der Standardwert lautet `false`.

   Im Folgenden einige wichtige Hinweise:

   * Wenn Zeitstempel für Ihre Report Suite aktiviert sind, `offlineEnabled` *muss* Ihre Konfigurationseigenschaft wahr sein.
   * Wenn Zeitstempel nicht für Ihre Report Suite aktiviert sind, `offlineEnabled` *muss* die Konfigurationseigenschaft „false“ lauten.

      Wenn dies nicht ordnungsgemäß konfiguriert ist, gehen Daten verloren. Wenn Sie sich nicht sicher sind, ob Zeitstempel für Ihre Report Suite aktiviert sind,  wenden Sie sich bitte an  Wenden Sie sich an die Kundenunterstützung oder laden Sie die Konfigurationsdatei aus Adobe Mobile Services herunter. Wenn Sie aktuell AppMeasurement-Daten in einer Report Suite erfassen, in der auch Daten aus JavaScript gesammelt werden, müssen Sie möglicherweise eine separate Report Suite für mobile Daten einrichten oder einen benutzerdefinierten Zeitstempel für JavaScript-Treffer einfügen, die die Variable `s.timestamp` nutzen.

   * Mindestens SDK-Version 4.0

* **org**

   Gibt die Experience Cloud-Organisations-ID für den Identity-Dienst für Adobe Experience Platform an.

   * Mindestens SDK-Version 4.3

* **poi**

   Jedes POI-Array beinhaltet den POI-Namen, den Längen- und Breitengrad sowie den Radius (in Metern) des POI-Bereichs. Für den POI-Namen kann eine beliebige Zeichenfolge gewählt werden. Wenn ein `trackLocation`-Aufruf gesendet wird, wird eine Kontextdatenvariable aufgefüllt und mit dem `trackLocation`-Aufruf gesendet, sofern sich die aktuellen Koordinaten an einem definierten POI befinden.

   * Mindestens SDK-Version 4.0

   ```js
   "poi" [ 
           ["sanfrancisco",37.757144,-122.44812,7000]
           ["santacruz",36.972935,-122.01725,600]
         ] 
   ```

   >[!TIP]
   >
   >Ab Version 4.2 sind POIs auf der Adobe Mobile-Oberfläche definiert und werden dynamisch mit der App-Konfigurationsdatei synchronisiert. Diese Synchronisation erfordert die Einstellung `analytics.poi`:

   ```js
   “analytics.poi”: “`https://assets.adobedtm.com/…/yourfile.json`”,
   ```

   Wenn diese Einstellung nicht konfiguriert ist, muss die Datei `ADBMobile.json` um folgende Zeile ergänzt werden. Informationen zum Herunterladen einer aktualisierten Konfigurationsdatei finden Sie unter [Vorbereitung](/help/ios/getting-started/requirements.md).

* **postback**

   Die Definition der „callback“-Nachrichtenvorlage wird im Folgenden gezeigt:

   ```js
   "payload":{
       "templateurl":"",//required- will be token-expanded prior to being sent
       "templatebody":"", //optional-if this length > 0 POST will be used as transport method. This is a base-64 encoded blob,which will be decoded and token-expanded prior to being sent.
       "contenttype":"", //optional-if this is length > 0 and POST type is selected, this will be set as the Content-Typeheader. if this is not supplied for a POST request,the default will be "application/x-www-form-urlencoded"
       "timeout": 0 //optional-number of seconds to wait before timingout.Defaultis2.}
   ```

   Das Objekt `payload` im Code stellt eine Beispiel-Payload für eine Nachrichtendefinition dar, die in der Datei `ADBMobileConfig.json` verwendet werden würde. Weitere Informationen dazu finden Sie unter [Postbacks](/help/ios/analytics-main/postback/postback.md).

   * Mindestens SDK-Version 4.6

* **privacyDefault**

   * Für `optedin` werden die Treffer sofort gesendet.
   * Bei `optedout` werden Treffer verworfen.
   * Wenn der Wert `optunknown` lautet und für ihre Report Suite Zeitstempel aktiviert sind, werden Treffer gespeichert, bis sich der Datenschutzstatus zu „optedin“ (Treffer werden gesendet) oder „optedout“ (Treffer werden verworfen) ändert.

      Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

      Dadurch wird nur der Ausgangswert festgelegt. Wenn dieser Wert im Code festgelegt oder geändert wird, wird der neue Wert verwendet, bis er wieder geändert oder die App entfernt und erneut installiert wird. Der Standardwert lautet `optedin`.

   * Mindestens SDK-Version 4.0

* **referrerTimeout**

   Anzahl der Sekunden, die das SDK beim ersten Start auf Akquise-Werber-Daten wartet, bevor das Time-out erfolgt. Wenn Sie Akquise verwenden, empfehlen wir ein 5-Sekunden-Time-out.

   >[!IMPORTANT]
   >
   >Diese Variable ist für Akquise erforderlich. Wenn die Variable auf `0` festgelegt oder nicht enthalten ist, wartet das SDK nicht auf Akquise-Daten und Akquise-Metriken werden nicht verfolgt.

   * Mindestens SDK-Version 4.1

* **remotes**

   Wird automatisch konfiguriert und definiert die von Adobe gehosteten Endpunkte für dynamische Konfigurationsdateien. Bei jedem Start wird der Zeitpunkt der letzten Aktualisierung der einzelnen Konfigurationsdateien mit der aktuellen Version verglichen. Etwaige Updates werden dann heruntergeladen und gespeichert.

   * `analytics.poi`: der Endpunkt für die gehostete POI-Konfiguration.

   * `messages`: der Endpunkt für die gehostete Konfiguration von In-App-Nachrichten.

   * Mindestens SDK-Version 4.2

* **rsids**

   Eine oder mehrere Report Suites zum Empfangen von Analytics-Daten. Mehrere Report Suite-IDs sollten durch Kommata getrennt werden, wobei kein Leerzeichen dazwischen steht.

   ```js
   "rsids": "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2" 
   ```

   >[!IMPORTANT]
   >
   >Diese Variable ist für Analytics erforderlich.

   * Mindestens SDK-Version 4.0

* **server**

   Der Analytics- oder Zielgruppen-Management-Server, basierend auf dem übergeordneten Knoten.

   Diese Variable sollte mit der Serverdomäne aufgefüllt werden, und zwar ohne das Protokollpräfix `https://` oder `https://`. Das Präfix basiert auf der Variablen `ssl` und wird automatisch von der Bibliothek verarbeitet.

   Wenn `ssl` auf `true` gesetzt ist, wird eine sichere Verbindung zu diesem Server hergestellt. Wenn `ssl` auf `false` gesetzt ist, wird eine nicht sichere Verbindung zu diesem Server hergestellt.

   >[!IMPORTANT]
   >
   >Diese Variable ist für Analytics und/oder Zielgruppen-Management erforderlich.

   * Mindestens SDK-Version 4.0

* **ssl**

   >[!IMPORTANT]
   >
   > Ab Version 4.10.0 ist SSL standardmäßig auf true gesetzt, wenn das Flag nicht gesetzt ist.

   Aktiviert (`true`) oder deaktiviert (`false`) die Möglichkeit, Messdaten mithilfe von SSL (HTTPS) zu senden.

   Die Definition der „callback“-Nachrichtenvorlage wird im Folgenden gezeigt:

   ```js
   "payload":{
       "templateurl":"",//required-will be token-expanded prior to being sent
       "templatebody":"",//optional-if this length > 0, POST will be used as transport method. This is a base64 encoded blob,which will be decoded and token-expanded prior to being sent.
       "contenttype":"",//optional-if this is length > 0 and POST type is selected this will be set as the Content-Typeheader. if this is not supplied for a POST request,the default will be "application/x-www-form-urlencoded"
       "timeout":0//optional-numberofsecondstowaitbeforetimingout.Defaultis2.} 
   ```

   Das Objekt `payload` im Code stellt eine Beispiel-Payload für eine Nachrichtendefinition dar, die in die Datei `ADBMobileConfig.json` aufgenommen wird. Weitere Informationen dazu finden Sie unter [Postbacks](/help/ios/analytics-main/postback/postback.md).

   * Mindestens SDK-Version 4.0

* **timeout**

   Bestimmt, wie lange Target auf eine Antwort wartet.

   * Mindestens SDK-Version 4.0


## Beispieldatei `ADBMobileConfig.json` {#section_52FA7C71A99147AFA9BE08D2177D8DA7}

Im Folgenden finden Sie eine beispielhafte Datei `ADBMobileConfig.json`:

```js
{ 
    "version": "2014-08-05T19:18:28.169Z", 
    "marketingCloud" : { 
        "org": "016D5C175213CCA80A490D05@AdobeOrg", 
        "coopUnsafe": false 
    }, 
    "target": { 
        "clientCode": "", 
        "timeout": 5, 
        "environmentId": 8 
    }, 
    "audienceManager": { 
        "server": "", 
        "analyticsForwardingEnabled": false 
    }, 
    "acquisition": { 
        "server": "c00.adobe.com", 
        "appid": "10a77a60192fbb628376e1b1daeeb65debf934e2c807e067ceb2963a41b165ee" 
    }, 
    "analytics": { 
        "rsids": "coolApp", 
        "server": "my.CoolApp.com", 
        "ssl": true, 
        "offlineEnabled": true, 
        "charset": "UTF-8", 
        "lifecycleTimeout": 300, 
        "privacyDefault": "optedin", 
        "batchLimit": 0, 
        "referrerTimeout": 5, 
        "poi": [ 
            ["san francisco",37.757144,-122.44812,7000],  
            ["santa cruz",36.972935,-122.01725,600] 
        ] 
    }, 
    "messages": [ 
        { 
            "messageId": "cb426565-a563-497a-a889-9dbeb451f8ae", 
            "template": "fullscreen", 
            "payload": { 
                 "html": "<!DOCTYPE html><html><head><meta charset=\"utf-8\" /><title></title><style></style></head><body><iframe src=\"https://www.adobe.com/\" frameborder=\"0\"></iframe></body></html>"
            },
            "showOffline": false,
            "showRule": "always",
            "endDate": 2524730400,
            "startDate": 0,
            "audiences": [],
            "triggers": [
                {
                    "key": "pev2",
                    "matches": "eq",
                    "values": [
                        "AMACTION:custom"
                    ] 
                } 
            ] 
        } 
    ], 
    "remotes": {
        "analytics.poi": "https://assets.adobedtm.com/staging/42a6fc9b77cd9f29082cf19b787bae75b7d1f9ca/scripts/satellite-53e0faadc2f9ed92bc00003b.json",
        "messages": "https://assets.adobedtm.com/staging/42a6fc9b77cd9f29082cf19b787bae75b7d1f9ca/scripts/satellite-53e0f9e2c2f9ed92bc000032.json"
    }
}
```

## Nachrichtenbeschreibung {#section_B97D654BA92149CE91F525268D7AD71F}

Der Nachrichtenknoten wird automatisch von Adobe Mobile Services generiert und muss in der Regel nicht manuell geändert werden. Die folgende Beschreibung dient der Fehlerbehebung:

* „messageId“

   * Generierte ID, erforderlich

* „template“

   * „alert“, „fullscreen“ oder „local“
   * erforderlich

* „payload“

   * „html“

      * Nur Vollbild-Vorlage, erforderlich
      * html, das die Nachricht definiert
   * „image“

      * nur Vollbild, optional
      * URL zu dem Bild, das als Vollbild verwendet werden soll
   * „altImage“

      * nur Vollbild, optional
      * Name des gebündelten Bildes, das verwendet werden soll, wenn die in
         `image` angegebene URL nicht erreichbar ist
   * „title“

      * Vollbild und Warnhinweis, erforderlich
      * Titeltext für einen Vollbild- oder Warnhinweis
   * „content“

      * Warnhinweis und lokale Benachrichtigung, erforderlich
      * Zusätzlicher Text für eine Warnmeldung oder Text für eine lokale Benachrichtigung
   * „confirm“

      * Warnhinweis, optional
      * Text, der in der Bestätigen-Schaltfläche verwendet wird
   * „cancel“

      * Warnung, erforderlich
      * Text, der in der Abbrechen-Schaltfläche verwendet wird
   * „url“

      * Warnhinweis, optional
      * URL-Aktion, die geladen wird, wenn auf die Bestätigen-Schaltfläche geklickt wird
   * „wait“

      * lokale Benachrichtigung, erforderlich
      * Wartezeit (in Sekunden) zum Posten der lokalen Benachrichtigung nach Abgleich der Kriterien









* „showOffline“

   * true oder false
   * Standardmäßig ist „false“ festgelegt

* „showRule“

   * „always“, „once“ oder „untilClick“
   * erforderlich

* „endDate“

   * Anzahl der Sekunden seit dem 1. Januar 1970
   * Standardwert ist „2524730400“

* „startDate“

   * Anzahl der Sekunden seit dem 1. Januar 1970
   * Standardwert ist „0“

* „audiences“

   Eine Gruppe von Objekten, die definieren, wie die Meldung angezeigt werden soll:

   * „key“

      Variablenname, der im Treffer zu finden und erforderlich ist.

   * „matches“

      Typ des Matchers, der für den Vergleich verwendet wird:

      * eq = gleich
      * ne = nicht gleich
      * co = enthält
      * nc = enthält nicht
      * sw = beginnt mit
      * ew = endet mit
      * ex = existiert
      * nx = existiert nicht
      * lt = kleiner als
      * le = kleiner als oder gleich
      * gt = größer als
      * ge = größer als oder gleich
   * „values“

      Eine Gruppe von Werten, die mit dem Wert der Variablen verglichen werden, die hier benannt sind:

      * Schlüssel
      * mit dem Matcher-Typ in
      * „matches“


* „triggers“

   Wie Zielgruppen, nur dass hier an die Stelle der Zielgruppen die Aktionen treten:

   * „key“
   * „matches“
   * „values“
