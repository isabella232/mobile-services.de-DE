---
description: Im Folgenden sehen Sie die Metriken und Dimensionen, die von der Mobile-Bibliothek automatisch gemessen werden können, nachdem der Lebenszyklus implementiert wurde, sowie eine Verknüpfung zur Problembehandlung von Lebenszyklusdaten.
keywords: android;library;mobile;sdk
seo-description: Im Folgenden sehen Sie die Metriken und Dimensionen, die von der Mobile-Bibliothek automatisch gemessen werden können, nachdem der Lebenszyklus implementiert wurde, sowie eine Verknüpfung zur Problembehandlung von Lebenszyklusdaten.
seo-title: Lebenszyklusmetriken
solution: Marketing Cloud, Analytics
title: Lebenszyklusmetriken
topic: Entwickler und Implementierung
uuid: 5a371f11-6521-410f-a01f-fc3b285b050f
translation-type: tm+mt
source-git-commit: 6c440c2130781943796cdfb581a39a8167f5ba13

---


# Lifecycle metrics {#lifecycle-metrics}

Im Folgenden sehen Sie die Metriken und Dimensionen, die von der Mobile-Bibliothek automatisch gemessen werden können, nachdem der Lebenszyklus implementiert wurde, sowie eine Verknüpfung zur Problembehandlung von Lebenszyklusdaten.

Weitere Informationen finden Sie in unserer Wissensdatenbank unter [Problembehebung von Lebenszyklusdaten](https://helpx.adobe.com/analytics/kb/troubleshoot-lifecycle-data.html).

## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

Wenn Lebenszyklusmetriken konfiguriert sind, werden sie in Kontextdatenparametern an Analytics, bei jedem mbox-Aufruf in Parametern an Target sowie als Signale an das Zielgruppen-Management gesendet. Analytics und Target verwenden dasselbe Format, während das Zielgruppen-Management ein anderes Präfix für jede Metrik verwendet.

Bei Analytics werden die Kontextdaten, die mit jedem Lebenszyklusverfolgungsaufruf gesendet werden, automatisch mit der Metrik oder Dimension erfasst und in Berichten verwendet.

### Metriken

* **a.media.name**

   Wird beim ersten Ausführen nach einer Installation oder Neuinstallation ausgelöst.

   * Analytics context data/Target parameter: `a.InstallEvent`
   * Audience Manager signal: `c_a_InstallEvent`

* **Upgrades**

   Wird beim ersten Start nach einem Upgrade oder bei Änderung der Versionsnummer ausgelöst.

   * Analytics context data/Target parameter: `a.UpgradeEvent`
   * Audience Manager signal: `c_a_UpgradeEvent`

* **Täglich eingesetzte Benutzer**

   wird ausgelöst, wenn die Anwendung an einem bestimmten Tag verwendet wird.

   >[!IMPORTANT]
   >
   >This metric is not automatically stored in an Analytics metric. Sie müssen eine Verarbeitungsregel erstellen, die ein benutzerdefiniertes Ereignis zum Erfassen dieser Metrik festlegt.

   * Analytics context data/Target parameter: `a.DailyEngUserEvent`
   * Audience Manager signal: `c_a_DailyEngUserEvent`

* **Monatlich beteiligte Benutzer**

   Wird ausgelöst, wenn die Anwendung während eines bestimmten Monats verwendet wird.  &gt;&gt;&gt;&gt;

   >[!IMPORTANT]
   >
   >Diese Metrik wird nicht automatisch in einer Analytics-Metrik gespeichert. Sie müssen eine Verarbeitungsregel erstellen, die ein benutzerdefiniertes Ereignis zum Erfassen dieser Metrik festlegt.

   * Analytics context data/Target parameter: `a.MonthlyEngUserEvent`
   * Audience Manager signal: `c_a_MonthlyEngUserEvent`

* **Starts**

   Wird bei jeder Ausführung ausgelöst, auch nach Abstürzen und Installationen. Wird auch bei einer Wiederaufnahme aus dem Hintergrund ausgelöst, wenn das Timeout der Lebenszyklussitzung überschritten wurde.

   * Analytics context data/Target parameter: `a.LaunchEvent`
   * Audience Manager signal: `c_a_LaunchEvent`

* **Abstürze**

   Wird ausgelöst, wenn die Anwendung beim Beenden nicht im Hintergrund ausgeführt wird. Das Ereignis wird gesendet, wenn die Anwendung nach dem Absturz gestartet wird. Adobe Mobile-Absturz-Reporting implementiert keinen globalen Handler für nicht abgefangene Ausnahmen.

   * Analytics context data/Target parameter: `a.CrashEvent`
   * Audience Manager signal: `c_a_CrashEvent`

* **Länge der vorherigen Sitzung**

   Gibt die Dauer einer vorherigen Anwendungssitzung in Sekunden an, basierend darauf, wie lange die Anwendung geöffnet und im Vordergrund war.

   * Analytics context data/Target parameter: `a.PrevSessionLength`
   * Audience Manager signal: `c_a_PrevSessionLength`

### Dimensionen

* **Installationsdatum**

   Datum des ersten Starts nach der Installation. Das Datumsformat ist `MM/DD/YYYY`festgelegt.

   * Analytics context data/Target parameter: `a.InstallDate`
   * Audience Manager signal: `c_a_InstallDate`

* **App-ID**

   Speichert den Applikationsnamen und die Version im folgenden Format:
   `[AppName] [BundleVersion]`.

   Ein Beispiel für dieses Format ist `myapp 1.1`.

   * Analytics context data/Target parameter: `a.AppID`
   * Audience Manager signal: `c_a_AppID`

* **Startanzahl**

   Gibt an, wie oft die Applikation gestartet bzw. aus dem Hintergrund gebracht wurde.

   * Analytics context data/Target parameter: `a.Launches`
   * Audience Manager signal: `c_a_Launches`

* **Tage seit der ersten Benutzung**

   Anzahl der Tage seit dem ersten Start

   * Analytics context data/Target parameter: `a.DaysSinceFirstUse`
   * Audience Manager signal: `c_a_DaysSinceFirstUse`

* **Tage seit der letzten Benutzung**

   Anzahl der Tage seit der letzten Verwendung.

   * Analytics context data/Target parameter: `a.DaysSinceLastUse`
   * Audience Manager signal: `c_a_DaysSinceLastUse`

* **Stunde des Tages**

   Erfasst die Stunde, in der die App gestartet wurde. Diese Metrik verwendet das 24-Stunden-Zahlenformat und wird zur Zeitdarstellung verwendet, um die Spitzennutzungszeiten zu bestimmen.

   * Analytics context data/Target parameter: `a.HourOfDay`
   * Audience Manager signal: `c_a_HourOfDay`

* **Wochentag**

   Anzahl der Wochentage, an denen die App gestartet wurde.

   * Analytics context data/Target parameter: `a.DayOfWeek`
   * Audience Manager signal: `c_a_DayOfWeek`

* **Betriebssystemversion**

   Die Version des Betriebssystems.

   * Analytics context data/Target parameter: `a.OSVersion`
   * Audience Manager signal: `c_a_OSVersion`

* **Tage seit der letzten Aktualisierung**

   Anzahl der Tage seit der Änderung der Versionsnummer der Applikation.

   >[!IMPORTANT]
   >
   >Diese Metrik wird nicht automatisch in einer Analytics-Variablen gespeichert. Sie müssen eine Verarbeitungsregel erstellen, um diesen Wert in eine Analytics-Variable für die Berichterstellung zu kopieren.

   * Analytics context data/Target parameter: `a.DaysSinceLastUpgrade`
   * Audience Manager signal: `c_a_DaysSinceLastUpgrade`

* **Starts seit der letzten Aktualisierung**

   Anzahl der Starts seit der Änderung der Versionsnummer der Applikation.

   >[!IMPORTANT]
   >
   >Diese Metrik wird nicht automatisch in einer Analytics-Variablen gespeichert. Sie müssen eine Verarbeitungsregel erstellen, um diesen Wert in eine Analytics-Variable für die Berichterstellung zu kopieren.

   * Analytics context data/Target parameter: `a.LaunchesSinceUpgrade`
   * Audience Manager signal: `c_a_LaunchesSinceUpgrade`

* **Gerätename**

   Speichert den Gerätenamen.

   * Analytics context data/Target parameter: `a.DeviceName`
   * Audience Manager signal: `c_a_DeviceName`

* **Betreibername**

   Speichert den vom Gerät angegebenen Namen des Mobilfunkanbieters.

   >[!IMPORTANT]
   >
   >Diese Metrik wird nicht automatisch in einer Analytics-Variablen gespeichert. Sie müssen eine Verarbeitungsregel erstellen, um diesen Wert in eine Analytics-Variable für die Berichterstellung zu kopieren.

   * Analytics context data/Target parameter: `a.CarrierName`
   * Audience Manager signal: `c_a_CarrierName`

* **Auflösung**

   Breite x Höhe in Pixel.

   * Analytics context data/Target parameter: `a.Resolution`
   * Audience Manager signal: `c_a_Resolution`

## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Die folgenden Metriken und Dimensionen werden in Variablen mobiler Lösungen mit der aufgeführten Methode erfasst.

* **Standort (bis 10 km)**

   Populated by `trackLocation` methods.

   * Analytics context data/Target parameter:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Management trait:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Standort (bis 100 m)**

   Populated by `trackLocation` methods.

   * Analytics-Kontextdaten/Target-Parameter:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Management trait:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Standort (bis 1 m)**

   Populated by `trackLocation` methods.

   * Analytics-Kontextdaten/Target-Parameter:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Eigenschaft Zielgruppen-Management:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Zielpunkt-Bezeichnung**

   Erfasst durch `trackLocation`-Methoden, wenn sich das Gerät an einem POI befindet.

   * Analytics-Kontextdaten/Target-Parameter:

      * `a.loc.poi`
   * Eigenschaft Zielgruppen-Management:

      * `c_a_loc_poi`


* **Entfernung zum Zentrum des Zielpunkts**

   Erfasst durch `trackLocation`-Methoden, wenn sich das Gerät an einem POI befindet.

   * Analytics-Kontextdaten/Target-Parameter:

      * `a.loc.dist`
   * Eigenschaft Zielgruppen-Management:

      * `c_a_loc_dist`
