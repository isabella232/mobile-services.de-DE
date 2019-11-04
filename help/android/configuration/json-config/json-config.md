---
description: Diese Informationen helfen Ihnen bei der Verwendung der Konfigurationsdatei „ADBMobile.json“.
seo-description: Diese Informationen helfen Ihnen bei der Verwendung der Konfigurationsdatei „ADBMobile.json“.
seo-title: ADBMobile-JSON-Konfiguration
solution: Experience Cloud,Analytics
title: ADBMobile-JSON-Konfiguration
topic: Entwickler und Implementierung
uuid: 1decf605-7bc3-4e73-ad52-1ecd5821599e
translation-type: ht
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# ADBMobile JSON-Konfigurationsdatei {#adbmobile-json-config}

Anhand dieser Informationen können Sie die Variablen in der Konfigurationsdatei ADBMobile.json verstehen.

## Referenz zur Konfigurationsdatei `ADBMobileConfig.json` {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

Sie können die Konfigurationsdatei für Ihre App über mehrere Plattformen hinweg verwenden:

>[!TIP]
>
>Unter **Android** muss sich `ADBMobileConfig.json` im Ordner `assets` befinden.

Hier finden Sie eine Liste der Variablen in der JSON-Datei und die minimale SDK-Version, die Sie für jede Variable benötigen:

* **acquisition**
   * Mindestens SDK-Version 4.1
   * Aktiviert die Mobile App-Akquise.
      * `server`: der Akquise-Server, der beim ersten Start auf einen Akquise-Referrer überprüft wird.
      * `appid`: die generierte ID, die diese App auf dem Akquise-Server eindeutig identifiziert.
   Wenn dieser Abschnitt fehlt, aktivieren Sie die App-Akquise und laden Sie die SDK-Konfigurationsdatei erneut herunter. Weitere Informationen finden Sie unter *referrerTimeout* in dieser Variablenliste.

* **analyticsForwardingEnabled**
   * Mindestens SDK-Version 4.8.0.
   * Der Standardwert lautet `false`.

      Die Eigenschaft im Objekt `audienceManager`. Wenn Audience Manager konfiguriert ist und `analyticsForwardingEnabled` auf `true` festgelegt ist, wird sämtlicher Analytics-Datenverkehr auch an Audience Manager weitergeleitet.

* **backdateSessionInfo**
   * Mindestens SDK-Version 4.6.
   * Aktiviert/Deaktiviert die Möglichkeit, dass das Adobe-SDK Treffer mit Sitzungsinformationen zurückdatiert.

      Aktuell umfassen Sitzungsinfotreffer Abstürze und Sitzungsdauer und können aktiviert und deaktiviert werden.

      **Treffer aktivieren oder deaktivieren**

      * Wenn Sie den Wert auf `false` einstellen, werden die Treffer **deaktiviert**. Wie schon in den Versionen vor Version 4.1 fasst das SDK die Sitzungsinformation der vorherigen Sitzung jetzt wieder mit dem ersten Treffer der nachfolgenden Sitzung zusammen. Das Adobe-SDK verbindet die Sitzungsinformation außerdem mit der aktuellen Laufzeit. Somit entstehen keine überhöhten Besuchszahlen. Die Anzahl der Aufrufe sinkt sofort, da überhöhte Besuchszahlen wegfallen.

      * Wenn Sie keinen Wert einstellen, lautet der Standardwert `true` und Treffer werden **aktiviert**. Wenn die Treffer aktiviert sind, datiert das Adobe-SDK den Sitzungsinfotreffer auf eine Sekunde nach dem endgültigen Treffer der vorherigen Sitzung zurück. Das bedeutet, dass die Daten zu Abstürzen und zur Sitzung mit dem korrekten Datum korrelieren, an dem sie stattgefunden haben. Eine Nebenwirkung besteht darin, dass das SDK ggf. einen Aufruf für den zurückdatierten Treffer erstellt. Bei jedem Neustart der App wird ein Treffer zurückdatiert.

         >[!IMPORTANT]
         >
         >Zurückdatierte Sitzungstrefferinformationen werden in einem Sitzungsinformations-Server-Aufruf gesendet und zusätzliche Server-Aufrufe werden ggf. angewendet.

* **batchLimit**
   * Mindestens SDK-Version 4.1
   * Grenzwert für die Anzahl der Treffer, die in aufeinanderfolgenden Aufrufen gesendet werden sollen.

      Wenn beispielsweise `batchLimit` auf 10 festgelegt ist, wird jeder Treffer vor dem 10. Treffer in der Warteschlange gespeichert. Wenn der 10. Treffer eingeht, werden alle 10 Treffer nacheinander gesendet.

      Beachten Sie die folgenden Informationen:

      * Der Standardwert lautet `0`. Das bedeutet, dass die Stapelverarbeitung nicht aktiviert ist.
      * Erfordert `offlineEnabled = true`.

* **charset**
   * Mindestens SDK-Version 4.0
   * Definiert den Zeichensatz, den Sie für die an Analytics gesendeten Daten verwenden.

      Der Zeichensatz wird verwendet, um eingehende Daten zum Speichern und Reporting in das UTF-8-Format umzuwandeln.

* **clientCode**
   * Mindestens SDK-Version 4.0
   * Ihr zugewiesener Client-Code.

      >[!IMPORTANT]
      >
      >Diese Variable ist für Target erforderlich.

* **coopUnsafe**
   * Mindestens SDK-Version 4.16.1
   * Die boolesche Eigenschaft des Objekts `marketingCloud`, das, wenn auf `true` festgelegt, dazu führt, dass das Gerät aus der Experience Cloud-Gerätekooperation ausgeschlossen wird.
   * Der Standardwert ist `false`.
   * Diese Einstellung wird **nur** für Kunden verwendet, die an der Gerätekooperation teilnehmen.
   Bei Mitgliedern mit Gerätekooperation, für die dieser Wert `true` sein muss, müssen Sie sich an das Kooperationsteam wenden, um eine Blacklist-Markierung auf Ihrem Gerätekooperationskonto zu verlangen. Es gibt keinen Self-Service-Pfad zum Aktivieren dieser Kennzeichnungen.

   Beachten Sie die folgenden Informationen:

   * Wenn `coopUnsafe` auf `true` festgelegt ist, wird `coop_unsafe=1` immer an Audience Manager und Besucher-ID-Treffer angehängt.
   * Wenn Sie die serverseitige Weiterleitung von Analytics an Audience Manager aktivieren, sehen Sie auch `coop_unsafe=1` Analytics-Treffer.


* **environmentId**
   * Mindestens SDK-Version 4.14
   * Die ID der Umgebung, die Sie verwenden möchten.

      Sie können eine gültige ID angeben (`environmentId=8`). Wenn `environmentId` nicht enthalten ist, wird die standardmäßige Produktionsumgebung verwendet.

* **lifecycleTimeout**
   * Mindestens SDK-Version 4.0
   * Der Standardwert beträgt 300 Sekunden.

      Legt die Dauer in Sekunden fest, die zwischen verschiedenen Startvorgängen einer App verstreichen muss, damit ein Startvorgang als neue Sitzung gilt. Dieses Zeitlimit wird auch angewendet, wenn eine Anwendung in den Hintergrund verschoben und später reaktiviert wird.

      Die Dauer, für die die App im Hintergrund ausgeführt wird, wird nicht in die Sitzungsdauer eingerechnet.

* **messages**

   * Mindestens SDK-Version 4.2
   * Wird automatisch von Adobe Mobile Services generiert, definiert die Einstellungen für In-App-Nachrichten. Weitere Informationen finden Sie im Abschnitt *Nachrichtenbeschreibung*.

* **offlineEnabled**

   * Mindestens SDK-Version 4.0
   * Ist diese Option aktiviert, werden Treffer in die Warteschlange aufgenommen, während das Gerät offline ist, und erst gesendet, wenn es wieder online ist.

      Für Ihre Report Suite müssen Zeitstempel aktiviert sein, um die Offline-Verfolgung zu nutzen.

      Der Standardwert lautet `false`.

      >[!IMPORTANT]
      >
      >Wenn Zeitstempel für Ihre Report Suite aktiviert sind, `offlineEnabled`muss Ihre Konfigurationseigenschaft **** wahr sein. Wenn Zeitstempel nicht für Ihre Report Suite aktiviert sind, `offlineEnabled`muss die Konfigurationseigenschaft **** „false“ lauten.
      >
      >Wenn dies nicht ordnungsgemäß konfiguriert ist, gehen Daten verloren. Wenn Sie sich nicht sicher sind, ob Zeitstempel für Ihre Report Suite aktiviert sind, wenden Sie sich an den Kundenservice oder laden Sie die Konfigurationsdatei aus Adobe Mobile Services herunter.

      Wenn Sie aktuell AppMeasurement-Daten in einer Report Suite erfassen, in der auch Daten aus JavaScript gesammelt werden, müssen Sie möglicherweise eine separate Report Suite für mobile Daten einrichten oder einen benutzerdefinierten Zeitstempel für JavaScript-Treffer einfügen, die die Variable `s.timestamp` nutzen.

* **org**

   * Mindestens SDK-Version 4.3
   * Gibt die Experience Cloud-Organisations-ID für den ID-Dienst an.

* **poi**
   * Mindestens SDK-Version 4.0
   * Jedes POI-Array beinhaltet den POI-Namen, den Längen- und den Breitengrad sowie den Radius in Metern des POI-Bereichs.

      Für den POI-Namen kann eine beliebige Zeichenfolge gewählt werden. Wenn beim Senden eines `trackLocation`-Aufrufs die aktuellen Koordinaten zu einem definierten POI passen, wird eine Kontextdatenvariable gefüllt und zusammen mit dem `trackLocation`-Aufruf gesendet.

      ```javascript
      "poi": [
                 ["san francisco",37.757144,-122.44812,7000]
                 ["santa cruz",36.972935,-122.01725,600]
             ]
      ```

      Ab Version 4.2 sind POIs auf der Adobe Mobile-Oberfläche definiert und werden dynamisch mit der App-Konfigurationsdatei synchronisiert. Diese Synchronisation erfordert die Einstellung `analytics.poi`:

      ```javascript
      “analytics.poi“: `https://assets.adobedtm.com/`
      …/yourfile.json”`,
      ```

      Wenn diese Einstellung nicht konfiguriert ist, muss die Datei `ADBMobile.json` um folgende Zeile ergänzt werden. Informationen zum Herunterladen einer aktualisierten Konfigurationsdatei finden Sie unter [Vorbereitung](/help/android/getting-started/requirements.md).

* **postback**
   * Mindestens SDK-Version 4.6
   * Im Folgenden finden Sie eine Definition der Nachrichtenvorlage „Rückruf“:

      ```javascript
      "payload":{
        "templateurl":"", //required will be token-expanded prior to being sent
        "templatebody":"", //optional - if this length > 0 POST will be used as transport method. This is a base64 encoded blob, which will be decoded and token-expanded prior to being sent.
        "contenttype": "", // optional - if this is length > 0 and POST type is selected this will be set as the Content-Type header.  if this is not supplied for a POST request, the default will be "application/x-www-form-urlencoded"
        "timeout": 0 // optional - number of seconds to wait before timing out.  Default is 2.}
      ```

      Das Objekt `payload` im Code stellt eine Beispiel-Payload für eine Nachrichtendefinition dar, die in die Datei `ADBMobileConfig.json` aufgenommen wird. Weitere Informationen dazu finden Sie unter [Postbacks](/help/android/analytics-main/postbacks/postbacks.md).

* **privacyDefault**
   * Mindestens SDK-Version 4.0
   * Der Standardwert lautet `optedin`.
      * Für `optedin` werden die Treffer sofort gesendet.
      * Bei `optedout` werden Treffer verworfen.
      * Wenn der Wert `optunknown` lautet und für ihre Report Suite Zeitstempel aktiviert sind, werden Treffer gespeichert, bis sich der Datenschutzstatus zu „optedin“ (Treffer werden gesendet) oder „optedout“ (Treffer werden verworfen) ändert.
      Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu `optedin`geändert wird.  Hierdurch wird nur der anfängliche Wert festgelegt. Wenn dieser Wert im Code festgelegt oder geändert wird, wird der neue Wert verwendet, bis er wieder geändert oder die App entfernt und erneut installiert wird.


* **referrerTimeout**
   * Mindestens SDK-Version 4.1
   * Anzahl der Sekunden, die das SDK beim ersten Start auf Akquise-Referrer-Daten wartet, bevor ein Timeout verursacht wird. Wenn Sie Akquise nutzen, empfehlen wir ein Timeout von 5 Sekunden.

      >[!IMPORTANT]
      >
      >Diese Variable ist für Akquise erforderlich. Wenn die Variable auf `0` festgelegt oder nicht enthalten ist, wartet das SDK nicht auf Akquise-Daten und Akquise-Metriken werden nicht verfolgt.

* **remotes**
   * Mindestens SDK-Version 4.2
   * Wird automatisch konfiguriert und definiert die von Adobe gehosteten Endpunkte für dynamische Konfigurationsdateien.

      Bei jedem Start wird der Zeitpunkt der letzten Aktualisierung der einzelnen Konfigurationsdateien mit der aktuellen Version verglichen. Etwaige Updates werden dann heruntergeladen und gespeichert.
      * `analytics.poi`: der Endpunkt für die gehostete POI-Konfiguration.
      * `messages`: der Endpunkt für die gehostete Konfiguration von In-App-Nachrichten.

* **rsids**
   * Mindestens SDK-Version 4.0
   * Mindestens eine Report Suite zum Empfang der Analytics-Daten. Verschiedene Report Suite-IDs müssen durch Kommas getrennt und ohne Leerzeichen zwischen den einzelnen Suites angegeben werden.

      ```javascript
        "rsids" "rsid"
      ```

      ```javascript
        "rsids" "rsid1,rsid2"
      ```

      >[!IMPORTANT]
      >
      >Diese Variable ist für Analytics erforderlich.

* **server**
   * Mindestens SDK-Version 4.0
   * Der Analytics- oder Zielgruppen-Management-Server, basierend auf dem übergeordneten Knoten. Diese Variable sollte mit der Serverdomäne aufgefüllt werden, und zwar ohne das Protokollpräfix `https://` oder `https://`. Das Präfix basiert auf der Variablen `ssl` und wird automatisch von der Bibliothek verarbeitet. Wenn `ssl` auf `true` gesetzt ist, wird eine sichere Verbindung zu diesem Server hergestellt. Wenn `ssl` auf `false` gesetzt ist, wird eine nicht sichere Verbindung zu diesem Server hergestellt.

* **ssl**
   * Mindestens SDK-Version 4.0
   * Der Standardwert lautet `false`.

      Aktiviert (`true`) oder deaktiviert (`false`) die Möglichkeit, Messdaten mithilfe von SSL (HTTPS) zu senden.

      Die Definition der „callback“-Nachrichtenvorlage wird im Folgenden gezeigt:

      ```javascript
      "payload": {
          "templateurl":"",//required-will be token-expanded prior to being sent 
          "templatebody": "", //optional - if this length >  0 POST will be used& as transport method. This is a base64 encoded blob, which will be  decoded and token-expanded prior to being sent.
          "contenttype": "" // optional - if this is length > 0 POST type is selected this will be set as the Content-Type header. if this is not supplied for a POST request, the default will be "application/x-www-form-urlencoded"
          "timeout": 0 // optional - number of seconds to wait before timing& out. Default is 2.}
      ```

* **timeout**
   * Mindestens SDK-Version 4.0
   * Bestimmt, wie lange Target auf eine Antwort wartet.


## Beispieldatei `ADBMobileConfig.json` {#section_4655EF79744649E5A5AE19E3224C472C}

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

Der Nachrichtenknoten wird automatisch von Adobe Mobile Services erstellt und muss für gewöhnlich nicht manuell geändert werden. Im Folgenden finden Sie Beschreibungen zur Problembehandlung:

* „messageId“
* generierte ID, erforderlich
* „template“
   * „alert“, „fullscreen“ oder „local“
   * erforderlich

* „showOffline“
   * „true“ oder „false“
   * Standard ist „false“

* „showRule“
   * „always“, „once“ oder „untilClick“
   * erforderlich

* „endDate“
   * Anzahl der Sekunden seit 1. Januar 1970
   * Standardwert ist „2524730400“

* „startDate“
   * Anzahl der Sekunden seit 1. Januar 1970
   * Standardwert ist „0“

* „payload“
   * „html“
      * nur Vollbildvorlage, erforderlich
      * Nachrichtendefinition durch HTML
   * „image“
      * nur Vollbild, optional
      * URL des Bildes, das als Vollbild verwendet werden soll
   * „altImage“
      * nur Vollbild, optional
      * Name des Bundle-Bildes, das verwendet werden soll, wenn die in
         * „image“
         * angegebene URL nicht erreichbar ist
   * „title“
      * Vollbild und Warnhinweis, erforderlich
      * Titeltext für eine Vollbildnachricht oder einen Warnhinweis
   * „content“
      * Warnhinweis und lokale Benachrichtigung, erforderlich
      * Text für eine Alarmnachricht oder eine lokale Benachrichtigung
   * „confirm“
      * Warnhinweis, optional
      * Für Schaltfläche „Bestätigen“ verwendeter Text
   * „cancel“
      * Warnhinweis, erforderlich
      * Für Schaltfläche „Abbrechen“ verwendeter Text
   * „url“
      * Warnhinweis, optional
      * URL, die beim Klicken der Schaltfläche „Bestätigen“ aufgerufen wird
   * „wait“
      * lokale Benachrichtigung, erforderlich
      * Zeit (in Sekunden), die zwischen Auslösungskriterium und Anzeige der lokalen Benachrichtigung gewartet wird



* „audiences“
   * Array von Objekten, das definiert, wie die Nachricht angezeigt werden soll
   * „key“
      * im Treffer zu suchender Variablenname, erforderlich
* „matches“
   * beim Vergleichen verwendeter Zuordnungstyp
   * eq = ist gleich
   * ne = ist nicht gleich
   * co = enthält
   * nc = enthält nicht
   * sw = beginnt mit
   * ew = endet mit
   * ex = vorhanden
   * nx = nicht vorhanden
   * lt = kleiner als
   * le = kleiner/gleich
   * gt = größer als
   * ge = größer/gleich
* „values“
   * ein Array von Werten, das verwendet wird, um eine Übereinstimmung mit den Werten der in
      * „key“
      * definierten Variablen durchzuführen; mithilfe des Zuordnungstyps aus
      * „matches“
* „triggers“
   * Ähnlich wie „audiences“, jedoch handelt es sich hierbei um die Aktion statt um die Zielgruppe
   * „key“
   * „matches“
   * „values“
