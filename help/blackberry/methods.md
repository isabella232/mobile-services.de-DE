---
description: Klassen und Methoden, die von der BlackBerry-Bibliothek bereitgestellt werden.
seo-description: Klassen und Methoden, die von der BlackBerry-Bibliothek bereitgestellt werden.
seo-title: Adobe Mobile-Klassen- und -methodenreferenz
title: Adobe Mobile-Klassen- und -methodenreferenz
uuid: 1 e 42 d 759-be 43-4 bb 3-ac 1 a-c 7 d 64133 d 61 c
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Adobe Mobile class and method reference {#adobe-mobile-class-and-method-reference}

Klassen und Methoden, die von der BlackBerry-Bibliothek bereitgestellt werden.

Das SDK unterstützt derzeit Adobe Analytics und Methoden befinden sich auf der Grundlage der Lösung in separaten Klassen.

## SDK settings {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   Gibt die Enum-Darstellung für den Datenschutzstatus des aktuellen Benutzers zurück.

   * ADBMobilePrivacyStatusOptIn: Treffer werden sofort gesendet.
   * ADBMobilePrivacyStatusOptOut: Treffer werden verworfen.
   * ADBMobilePrivacyStatusUnknown: Wenn für Ihre Report Suite Zeitstempel aktiviert sind, werden Treffer so lange gespeichert, bis der Datenschutzstatus in „opt-in“ (Treffer werden gesendet) oder „opt-out“ (Treffer werden verworfen) geändert wird. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

      Der Standardwert wird in der Datei `ADBMobileConfig.json` festgelegt.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      static ADBMobilePrivacyStatus getPrivacyStatus();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
      ADBMobilePrivacyStatus privacyStatus = ADBMobile::getPrivacyStatus();
      ```

* **setPrivacyStatus**

   Legt für den aktuellen Benutzer den Datenschutzstatus `status` fest. Die folgenden Werte sind zulässig:

   * `ADBMobilePrivacyStatusOptIn` - Treffer werden sofort gesendet.
   * `ADBMobilePrivacyStatusOptOut` - werden Treffer verworfen.
   * `ADBMobilePrivacyStatusUnknown`: Wenn für Ihre Report Suite Zeitstempel aktiviert sind, werden Treffer so lange gespeichert, bis der Datenschutzstatus in „opt-in“ (Treffer werden gesendet) oder „opt-out“ (Treffer werden verworfen) geändert wird. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      static void setPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
      ADBMobile::setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```

* **getUserIdentifier**

   Gibt die Benutzer-ID zurück, sofern eine benutzerdefinierte ID festgelegt wurde. Returns `null` if a custom identifier is not set. Der Standardwert lautet `null`.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      static QString getUserIdentifier();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
      QString userId = ADBMobile::getUserIdentifier(); 
      ```

* **setUserIdentifier**

   Legt die Benutzerkennung auf `identifier` fest.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      static void setUserIdentifier(QString identifier);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
      ADBMobile::setUserIdentifier("billybob");
      ```

* **getDebugLogging**

   Gibt die aktuelle Vorgabe für die Debug-Protokollierung zurück. Der Standardwert lautet `false`.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      static bool getDebugLogging();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
       bool debugging = ADBMobile::getDebugLogging(); 
      ```

* **setDebugLogging**

   Legt die Debug-Protokollierungseinstellung auf `debugLogging` fest. 

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      static void setDebugLogging(bool debugLogging);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
        ADBMobile::setDebugLogging(true); 
      ```

* **collectLifecycleData**

   Gibt dem SDK gegenüber an, dass Lebenszyklusdaten für die Nutzung aller Lösungen im SDK erfasst werden sollen. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/blackberry/metrics.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      static void collectLifecycleData();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
      ApplicationUI::ApplicationUI(bb::cascades::Application *app):  QObject(app)  { 
      //... 
      ADBMobile::collectLifecycleData(); 
      }
      ```

## Analytics methods {#section_91F4AD0A045D4E4E8F9A93450503E49E}

Jede dieser Methoden wird zum Senden von Daten in Ihre Adobe Analytics Report Suite verwendet.

* **trackState**

   Verfolgt einen App-Status mit optionalen Kontextdaten. Status sind die in Ihrer App verfügbaren Ansichten wie „Startseiten-Dashboard“, „App-Einstellungen“, „Warenkorb“ usw. Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `trackState`-Aufrufe inkrementieren die Seitenansichten.

   >[!TIP]
   >
   >Dies ist der einzige Verfolgungsaufruf, der Seitenansichten inkrementiert.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      static void trackState(QString state, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
         ADBMobile::trackState("loginScreen", null);
      ```

* **trackAction**

   Verfolgt eine Aktion in der App. Bei Aktionen handelt es sich um die Dinge, die in Ihrer App vor sich gehen, die Sie messen möchten, beispielsweise „Anmeldungen“, „Banner-Tippvorgänge“, „Feed-Abonnements“ und andere Metriken.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   Sendet die aktuellen XY-Koordinaten. Ersetzen Sie „event“ mit dem Ereignis, das vom BPS-Abonnenten empfangen wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json` config file reference {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

The `ADBMobileConfig.json` file must be placed in the *assets* folder.

* **rsids**

   (Erforderlich) Eine oder mehrere Report Suites zum Empfangen von Analytics-Daten. Verschiedene Report Suite-IDs müssen durch Kommas getrennt und ohne Leerzeichen zwischen den einzelnen Suites angegeben werden.

   Hier finden Sie das Codebeispiel für diese Variable:

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (Erforderlich). Analytics-Server. This variable should be populated with the server domain, without an `https://` or `https://` protocol prefix. Das Protokollpräfix wird anhand der Variable `ssl` automatisch von der Bibliothek verarbeitet. Wenn `ssl` auf `true` gesetzt ist, wird eine sichere Verbindung zu diesem Server hergestellt. Wenn `ssl` auf `false` gesetzt ist, wird eine nicht sichere Verbindung zu diesem Server hergestellt.

* **charset**

   Definiert den Zeichensatz, den Sie für die an Analytics gesendeten Daten verwenden. Der Zeichensatz wird verwendet, um eingehende Daten zum Speichern und Reporting in das UTF-8-Format umzuwandeln.

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (HTTPS). Der Standardwert lautet `false`.

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. Für Ihre Report Suite müssen Zeitstempel aktiviert sein, um die Offline-Verfolgung zu nutzen.

   >[!TIP]
   >
   >If timestamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. Wenn Zeitstempel nicht für Ihre Report Suite aktiviert sind, `offlineEnabled`muss die Konfigurationseigenschaft ** „false“ lauten. Wenn dies nicht ordnungsgemäß konfiguriert ist, gehen Daten verloren. Wenn Sie sich nicht sicher sind, ob Zeitstempel für Ihre Report Suite aktiviert sind, wenden Sie sich bitte an [Enterprise-Support](https://helpx.adobe.com/contact/enterprise-support.ec.html).

   Wenn Sie aktuell AppMeasurement-Daten in einer Report Suite erfassen, in der auch Daten aus JavaScript gesammelt werden, müssen Sie möglicherweise eine separate Report Suite für mobile Daten einrichten oder einen benutzerdefinierten Zeitstempel für JavaScript-Treffer einfügen, die die Variable `s.timestamp` nutzen.

   Der Standardwert lautet `false`.

* **lifecycleTimeout**

   Legt die Dauer in Sekunden fest, die zwischen verschiedenen Startvorgängen einer App verstreichen muss, damit ein Startvorgang als neue Sitzung gilt. Dieses Zeitlimit wird auch angewendet, wenn eine Anwendung in den Hintergrund verschoben und später reaktiviert wird. Die Dauer, für welche die App im Hintergrund ausgeführt wird, wird nicht in die Sitzungsdauer eingerechnet.

   Der Standardwert ist 300 Sekunden.

* **batchLimit**

   Maximale Anzahl der in der Warteschlange gespeicherten Treffer. Der Standardwert ist 0 (kein Limit).

* **privacyDefault**

   * `optedin` - Treffer werden sofort gesendet.
   * `optedout` - werden Treffer verworfen.
   * `optunknown`: Wenn für Ihre Report Suite Zeitstempel aktiviert sind, werden Treffer so lange gespeichert, bis der Datenschutzstatus in „opt-in“ (Treffer werden gesendet) oder „opt-out“ (Treffer werden verworfen) geändert wird. 

      Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.
   Diese Variable legt nur den Ausgangswert fest. Wenn dieser Wert im Code festgelegt oder geändert wird, wird der neue Wert verwendet, bis er wieder geändert oder die App entfernt und erneut installiert wird.

   Der Standardwert lautet `optedin`.

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
    } 
}
```
