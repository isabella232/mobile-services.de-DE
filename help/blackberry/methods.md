---
description: Klassen und Methoden, die von der BlackBerry-Bibliothek bereitgestellt werden.
seo-description: Klassen und Methoden, die von der BlackBerry-Bibliothek bereitgestellt werden.
seo-title: Adobe Mobile-Klasse und Methodenreferenz
title: Adobe Mobile-Klasse und Methodenreferenz
uuid: 1e42d759-be43-4bb3-ac1a-c7d64133d61c
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 60%

---


# Adobe Mobile-Klasse und Methodenreferenz {#adobe-mobile-class-and-method-reference}

Klassen und Methoden, die von der BlackBerry-Bibliothek bereitgestellt werden.

Das SDK unterstützt derzeit Adobe Analytics, und die Methoden sind je nach Lösung in separaten Klassen unterteilt.

## SDK-Einstellungen {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   Gibt die Enum-Darstellung für den Datenschutzstatus des aktuellen Benutzers zurück.

   * ADBMobilePrivacyStatusOptIn - Treffer werden sofort gesendet.
   * ADBMobilePrivacyStatusOptOut - Treffer werden verworfen.
   * ADBMobilePrivacyStatusUnknown - Wenn Ihre Report Suite zeitstempelfähig ist, werden Treffer gespeichert, bis der Datenschutzstatus in &quot;opt-in&quot;(Zugriffe werden dann gesendet) oder &quot;opt-out&quot;(Zugriffe werden dann verworfen) geändert wird. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

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

   * `ADBMobilePrivacyStatusOptIn`: Treffer werden umgehend gesendet.
   * `ADBMobilePrivacyStatusOptOut`: werden Treffer verworfen.
   * `ADBMobilePrivacyStatusUnknown` - Wenn Ihre Report Suite zeitstempelfähig ist, werden die Treffer gespeichert, bis der Datenschutzstatus in &quot;opt-in&quot;(Zugriffe werden gesendet) oder &quot;opt-out&quot;(Zugriffe werden dann verworfen) geändert wird. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

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

## Analytics-Methoden {#section_91F4AD0A045D4E4E8F9A93450503E49E}

Jede dieser Methoden wird zum Senden von Daten in Ihre Adobe Analytics Report Suite verwendet.

* **trackState**

   Verfolgt einen App-Status mit optionalen Kontextdaten. Statusangaben sind die Ansichten, die in Ihrer App verfügbar sind, z. B. &quot;Home Dashboard&quot;, &quot;App-Einstellungen&quot;, &quot;Warenkorb&quot;usw. Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `trackState`-Aufrufe inkrementieren die Seitenansichten.

   >[!TIP]
   >
   >Dies ist der einzige Verfolgungsaufruf, bei dem die Seitenansichten inkrementiert werden.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      static void trackState(QString state, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
         ADBMobile::trackState("loginScreen", null);
      ```

* **trackAction**

   Verfolgt eine Aktion in der App. Aktionen sind die Vorgänge, die in Ihrer App stattfinden und die Sie messen möchten, z. B. &quot;Anmeldungen&quot;, &quot;Bannerklappen&quot;, &quot;Feed-Abonnement&quot;und andere Metriken.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   Sendet die aktuellen XY-Koordinaten. Ersetzen Sie Ereignis durch das Ereignis, das vom Abonnenten von BPS empfangen wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json` Referenz zur Konfigurationsdatei {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

The `ADBMobileConfig.json` file must be placed in the *assets* folder.

* **rsids**

   (Erforderlich) Eine oder mehrere Report Suites zum Empfang von Analytics-Daten. Mehrere Report Suite-IDs sollten durch Kommata getrennt werden, wobei kein Leerzeichen dazwischen steht.

   Im Folgenden finden Sie das Codebeispiel für diese Variable:

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (Erforderlich). Analytics-Server. Diese Variable sollte mit der Serverdomäne aufgefüllt werden, und zwar ohne das Protokollpräfix `https://` oder `https://`. Das Protokollpräfix wird automatisch von der Bibliothek auf Basis der `ssl` Variablen verarbeitet. Wenn `ssl` auf `true` gesetzt ist, wird eine sichere Verbindung zu diesem Server hergestellt. Wenn `ssl` auf `false` gesetzt ist, wird eine nicht sichere Verbindung zu diesem Server hergestellt.

* **charset**

   Definiert den Zeichensatz, den Sie für die an Analytics gesendeten Daten verwenden. Der Zeichensatz wird verwendet, um eingehende Daten zum Speichern und Reporting in das UTF-8-Format umzuwandeln.

* **ssl**

   Aktiviert (`true`) oder deaktiviert (`false`) das Senden von Messungsdaten über SSL (HTTPS). Der Standardwert lautet `false`.

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. Für Ihre Report Suite müssen Zeitstempel aktiviert sein, um die Offline-Verfolgung zu nutzen.

   >[!TIP]
   >
   >If timestamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. Wenn Zeitstempel nicht für Ihre Report Suite aktiviert sind, `offlineEnabled` *muss* die Konfigurationseigenschaft „false“ lauten. Wenn dies nicht ordnungsgemäß konfiguriert ist, gehen Daten verloren. Wenn Sie sich nicht sicher sind, ob Zeitstempel für Ihre Report Suite aktiviert sind,   wenden Sie sich bitte an   [Enterprise Support](https://helpx.adobe.com/de/contact/enterprise-support.ec.html).

   If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data, or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

   Der Standardwert lautet `false`.

* **lifecycleTimeout**

   Gibt die Dauer in Sekunden an, die zwischen dem App-Starts verstreichen muss, damit der Start als neue Sitzung erachtet wird. Dieses Time-out gilt auch, wenn Ihre Anwendung in den Hintergrund gestellt und reaktiviert wird. Die Zeit, die Ihre App im Hintergrund ist, ist nicht in der Sitzungslänge enthalten.

   Der Standardwert ist 300 Sekunden.

* **batchLimit**

   Maximale Anzahl der in der Warteschlange gespeicherten Treffer. Der Standardwert ist 0 (Keine Begrenzung).

* **privacyDefault**

   * `optedin`: Treffer werden umgehend gesendet.
   * `optedout`: werden Treffer verworfen.
   * `optunknown` - Wenn Ihre Report Suite zeitstempelfähig ist, werden die Treffer gespeichert, bis der Datenschutzstatus in &quot;opt-in&quot;(Zugriffe werden gesendet) oder &quot;opt-out&quot;(Zugriffe werden dann verworfen) geändert wird.

      Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.
   Diese Variable legt nur den Ausgangswert fest. Wenn dieser Wert jemals im Code festgelegt oder geändert wurde, wird der neue Wert verwendet, bis er geändert wird, oder die App wird deinstalliert und dann neu installiert.

   Der Standardwert lautet `optedin`.

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
    } 
}
```
