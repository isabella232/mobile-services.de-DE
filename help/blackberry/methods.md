---
description: Klassen und Methoden, die von der BlackBerry-Bibliothek bereitgestellt werden.
title: Adobe Mobile-Klasse und Methodenreferenz
uuid: 1e42d759-be43-4bb3-ac1a-c7d64133d61c
exl-id: ad73ec1d-d082-4237-b7cb-b8ec2f7595a3
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 61%

---

# Adobe Mobile-Klasse und Methodenreferenz {#adobe-mobile-class-and-method-reference}

Klassen und Methoden, die von der BlackBerry-Bibliothek bereitgestellt werden.

Das SDK unterstützt derzeit Adobe Analytics und Methoden befinden sich je nach Lösung in separaten Klassen.

## SDK-Einstellungen {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   Gibt die Enum-Darstellung für den Datenschutzstatus des aktuellen Benutzers zurück.

   * ADBMobilePrivacyStatusOptIn - Treffer werden sofort gesendet.
   * ADBMobilePrivacyStatusOptOut - Treffer werden verworfen.
   * ADBMobilePrivacyStatusUnknown : Wenn für Ihre Report Suite Zeitstempel aktiviert sind, werden Treffer gespeichert, bis der Datenschutzstatus zu &quot;opt-in&quot;(anschließend werden Treffer gesendet) oder &quot;opt-out&quot;(anschließend werden die Treffer verworfen) geändert wird. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

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
   * `ADBMobilePrivacyStatusUnknown` - Wenn für Ihre Report Suite Zeitstempel aktiviert sind, werden die Treffer gespeichert, bis der Datenschutzstatus zu &quot;opt-in&quot;(anschließend werden die Treffer gesendet) oder &quot;opt-out&quot;(anschließend werden die Treffer verworfen) geändert wird. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      static void setPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
      ADBMobile::setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```

* **getUserIdentifier**

   Gibt die Benutzer-ID zurück, sofern eine benutzerdefinierte ID festgelegt wurde. Gibt `null` zurück, wenn keine benutzerdefinierte ID festgelegt ist. Der Standardwert lautet `null`.

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

   Verfolgt einen App-Status mit optionalen Kontextdaten. Status sind die Ansichten, die in Ihrer App verfügbar sind, z. B. &quot;Startseiten-Dashboard&quot;, &quot;App-Einstellungen&quot;, &quot;Warenkorb&quot;usw. Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `trackState`-Aufrufe inkrementieren die Seitenansichten.

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

   Verfolgt eine Aktion in der App. Bei Aktionen handelt es sich um die Dinge, die in Ihrer App vor sich gehen, die Sie messen möchten, z. B. &quot;Anmeldungen&quot;, &quot;Banner-Tippvorgänge&quot;, &quot;Feed-Abonnements&quot;und andere Metriken.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   Sendet die aktuellen XY-Koordinaten. Ersetzen Sie das Ereignis durch das Ereignis, das vom Abonnenten von BPS empfangen wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json` Referenz zur Konfigurationsdatei {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

Die Datei `ADBMobileConfig.json` muss sich im Ordner *assets* befinden.

* **rsids**

   (Erforderlich) Eine oder mehrere Report Suites für den Empfang von Analytics-Daten. Mehrere Report Suite-IDs sollten durch Kommata getrennt werden, wobei kein Leerzeichen dazwischen steht.

   Hier finden Sie ein Code-Beispiel für diese Variable:

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (Erforderlich). Analytics-Server. Diese Variable sollte mit der Serverdomäne aufgefüllt werden, und zwar ohne das Protokollpräfix `https://` oder `https://`. Das Protokollpräfix wird automatisch von der Bibliothek basierend auf der Variablen `ssl` verarbeitet. Wenn `ssl` auf `true` gesetzt ist, wird eine sichere Verbindung zu diesem Server hergestellt. Wenn `ssl` auf `false` gesetzt ist, wird eine nicht sichere Verbindung zu diesem Server hergestellt.

* **charset**

   Definiert den Zeichensatz, den Sie für die an Analytics gesendeten Daten verwenden. Der Zeichensatz wird verwendet, um eingehende Daten zum Speichern und Reporting in das UTF-8-Format umzuwandeln.

* **ssl**

   Aktiviert (`true`) oder deaktiviert (`false`) das Senden von Messungsdaten über SSL (HTTPS). Der Standardwert lautet `false`.

* **offlineEnabled**

   Wenn aktiviert (`true`), werden Treffer in die Warteschlange gestellt, während das Gerät offline ist, und später gesendet, wenn das Gerät online ist. Für Ihre Report Suite müssen Zeitstempel aktiviert sein, um die Offline-Verfolgung zu nutzen.

   >[!TIP]
   >
   >Wenn Zeitstempel für Ihre Report Suite aktiviert sind, muss die `offlineEnabled` Konfigurationseigenschaft *muss* `true` sein. Wenn Zeitstempel nicht für Ihre Report Suite aktiviert sind, `offlineEnabled` *muss* die Konfigurationseigenschaft „false“ lauten. Wenn dies nicht ordnungsgemäß konfiguriert ist, gehen Daten verloren. Wenn Sie sich nicht sicher sind, ob Zeitstempel für Ihre Report Suite aktiviert sind,   wenden Sie sich bitte an   [Enterprise Support](https://helpx.adobe.com/de/contact/enterprise-support.ec.html).

   Wenn Sie aktuell AppMeasurement-Daten in einer Report Suite erfassen, in der auch Daten aus JavaScript gesammelt werden, müssen Sie möglicherweise eine separate Report Suite für mobile Daten einrichten oder einen benutzerdefinierten Zeitstempel für alle JavaScript-Treffer einfügen, die die Variable `s.timestamp` verwenden.

   Der Standardwert lautet `false`.

* **lifecycleTimeout**

   Gibt die Dauer in Sekunden an, die zwischen dem App-Starts verstreichen muss, damit der Start als neue Sitzung erachtet wird. Dieses Time-out gilt auch, wenn Ihre Anwendung in den Hintergrund gestellt und reaktiviert wird. Die Zeit, die Ihre App im Hintergrund ist, ist nicht in der Sitzungslänge enthalten.

   Der Standardwert ist 300 Sekunden.

* **batchLimit**

   Maximale Anzahl der in der Warteschlange gespeicherten Treffer. Der Standardwert ist 0 (Keine Begrenzung).

* **privacyDefault**

   * `optedin`: Treffer werden umgehend gesendet.
   * `optedout`: werden Treffer verworfen.
   * `optunknown` - Wenn für Ihre Report Suite Zeitstempel aktiviert sind, werden die Treffer gespeichert, bis der Datenschutzstatus zu &quot;opt-in&quot;(anschließend werden die Treffer gesendet) oder &quot;opt-out&quot;(anschließend werden die Treffer verworfen) geändert wird.

      Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.
   Diese Variable legt nur den Anfangswert fest. Wenn dieser Wert im Code festgelegt oder geändert wird, wird der neue Wert verwendet, bis er geändert wird, oder die App wird deinstalliert und dann erneut installiert.

   Der Standardwert lautet `optedin`.

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
    } 
}
```
