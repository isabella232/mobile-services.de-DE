---
description: Liste der Metriken und Dimensionen, die automatisch von der Mobilbibliothek gemessen werden können.
keywords: android;library;mobile;sdk
seo-description: Liste der Metriken und Dimensionen, die automatisch von der Mobilbibliothek gemessen werden können.
seo-title: Lebenszyklusmetriken
solution: Experience Cloud,Analytics
title: Lebenszyklusmetriken
topic: Developer and implementation
uuid: f958c3ef-1d79-4b30-8966-ef74bd48a5d6
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 75%

---


# Lebenszyklusmetriken {#lifecycle-metrics}

Liste der Metriken und Dimensionen, die automatisch von der Mobilbibliothek gemessen werden können.

Weitere Informationen finden Sie unter [Fehlerbehebung bei Lebenszyklusdaten](https://helpx.adobe.com/de/analytics/kb/troubleshoot-lifecycle-data.html).


## Lebenszyklusmetriken und -dimensionen {#section_78F036C4296F4BA3A47C2044F79C86C1}

Bei der Konfiguration werden Lebenszyklusmetriken in Kontextdatenparametern an Analytics, in Parametern zur Zielgruppe mit jedem mbox-Aufruf und als Signal an die Audience-Verwaltung gesendet. Analytics und Zielgruppe verwenden dasselbe Format, während die Audience-Verwaltung für jede Metrik ein anderes Präfix verwendet.

Bei Analytics werden die Kontextdaten, die mit jedem Lebenszyklusverfolgungsaufruf gesendet werden, automatisch mit der Metrik oder Dimension erfasst und in Berichten verwendet. Ausnahmen werden im Inhalt vermerkt.

## Metriken

* **Erste Starts**

   Wird beim ersten Ausführen nach einer Installation oder Neuinstallation ausgelöst.

   * Analytics-Kontextdaten/Target-Parameter: `a.InstallEvent`
   * Audience Manager-Signal: `c_a_InstallEvent`

* **Upgrades**

   Wird beim ersten Start nach einem Upgrade oder bei Änderung der Versionsnummer ausgelöst.

   * Analytics-Kontextdaten/Target-Parameter: `a.UpgradeEvent`
   * Audience Manager-Signal: `c_a_UpgradeEvent`

* **Täglich eingesetzte Benutzer**

   wird ausgelöst, wenn die Anwendung an einem bestimmten Tag verwendet wird.

   >[!IMPORTANT]
   >
   >Diese Metrik wird nicht automatisch in einer Analytics-Metrik gespeichert. Sie müssen eine Verarbeitungsregel erstellen, die ein benutzerdefiniertes Ereignis zum Erfassen dieser Metrik festlegt.

   * Analytics-Kontextdaten/Target-Parameter: `a.DailyEngUserEvent`
   * Audience Manager-Signal: `c_a_DailyEngUserEvent`

* **Monatlich beteiligte Benutzer**

   Wird ausgelöst, wenn die Anwendung während eines bestimmten Monats verwendet wird.

   >[!IMPORTANT]
   >
   >Diese Metrik wird nicht automatisch in einer Analytics-Metrik gespeichert. Sie müssen eine Verarbeitungsregel erstellen, die ein benutzerdefiniertes Ereignis zum Erfassen dieser Metrik festlegt.

   * Analytics-Kontextdaten/Target-Parameter: `a.MonthlyEngUserEvent`
   * Audience Manager-Signal: `c_a_MonthlyEngUserEvent`

* **Starts**

   Wird bei jeder Ausführung ausgelöst, einschließlich Abstürzen und Installationen. Wird auch bei einer Wiederaufnahme aus dem Hintergrund ausgelöst, wenn der Timeout der Lebenszyklussitzung überschritten wurde.

   * Analytics-Kontextdaten/Target-Parameter: `a.LaunchEvent`
   * Audience Manager-Signal: `c_a_LaunchEvent`

* **Abstürze**

   Wird ausgelöst, wenn die Anwendung beim Beenden nicht im Hintergrund ausgeführt wird. Das Ereignis wird gesendet, wenn die Anwendung nach dem Absturz gestartet wird. Adobe Mobile-Absturz-Reporting implementiert keinen globalen Handler für nicht abgefangene Ausnahmen.

   * Analytics-Kontextdaten/Target-Parameter: `a.CrashEvent`
   * Audience Manager-Signal: `c_a_CrashEvent`

* **Länge der vorherigen Sitzung**

   Gibt die Dauer einer vorherigen Anwendungssitzung in Sekunden an, basierend darauf, wie lange die Anwendung geöffnet und im Vordergrund war.

   * Analytics-Kontextdaten/Target-Parameter: `a.PrevSessionLength`
   * Audience Manager-Signal: `c_a_PrevSessionLength`


## Dimensionen

* **Installationsdatum**

   Datum des ersten Starts nach der Installation. Das Datumsformat ist `MM/DD/YYYY`.

   * Analytics-Kontextdaten/Target-Parameter: `a.InstallDate`
   * Audience Manager-Signal: `c_a_InstallDate`

* **App-ID**

   Speichert den App-Namen und die Version im Format `[AppName] [BundleVersion]`. Ein Beispiel für dieses Format ist `myapp 1.1`.

   * Analytics-Kontextdaten/Target-Parameter: `a.AppID`
   * Audience Manager-Signal: `c_a_AppID`

* **Startanzahl**

   Gibt an, wie oft die Applikation gestartet bzw. aus dem Hintergrund gebracht wurde.

   * Analytics-Kontextdaten/Target-Parameter: `a.Launches`
   * Audience Manager-Signal: `c_a_Launches`

* **Tage seit der ersten Benutzung**

   Anzahl der Tage seit dem ersten Start

   * Analytics-Kontextdaten/Target-Parameter: `a.DaysSinceFirstUse`
   * Audience Manager-Signal: `c_a_DaysSinceFirstUse`

* **Tage seit der letzten Benutzung**

   Anzahl der Tage seit der letzten Verwendung.

   * Analytics-Kontextdaten/Target-Parameter: `a.DaysSinceLastUse`
   * Audience Manager-Signal: `c_a_DaysSinceLastUse`

* **Stunde des Tages**

   Erfasst die Stunde, in der die App gestartet wurde. Diese Metrik verwendet das 24-Stunden-Zahlenformat und wird zur Zeitdarstellung verwendet, um die Spitzennutzungszeiten zu bestimmen.

   * Analytics-Kontextdaten/Target-Parameter: `a.HourOfDay`
   * Audience Manager-Signal: `c_a_HourOfDay`

* **Wochentag**

   Anzahl der Wochentage, an denen die App gestartet wurde.

   * Analytics-Kontextdaten/Target-Parameter: `a.DayOfWeek`
   * Audience Manager-Signal: `c_a_DayOfWeek`

* **Betriebssystemversion**

   Die Betriebssystemversion.

   * Analytics-Kontextdaten/Target-Parameter: `a.OSVersion`
   * Audience Manager-Signal: `c_a_OSVersion`

* **Tage seit der letzten Aktualisierung**

   Anzahl der Tage seit der Änderung der Versionsnummer der Applikation.

   >[!IMPORTANT]
   >
   >Diese Metrik wird nicht automatisch in einer Analytics-Variable gespeichert. Sie müssen eine Verarbeitungsregel erstellen, um diesen Wert in eine Analytics-Variable für die Berichterstellung zu kopieren.

   * Analytics-Kontextdaten/Target-Parameter: `a.DaysSinceLastUpgrade`
   * Audience Manager-Signal: `c_a_DaysSinceLastUpgrade`

* **Starts seit der letzten Aktualisierung**

   Anzahl der Starts seit der Änderung der Versionsnummer der Applikation.

   >[!IMPORTANT]
   >
   >Diese Metrik wird nicht automatisch in einer Analytics-Variable gespeichert. Sie müssen eine Verarbeitungsregel erstellen, um diesen Wert in eine Analytics-Variable für die Berichterstellung zu kopieren.

   * Analytics-Kontextdaten/Target-Parameter: `a.LaunchesSinceUpgrade`
   * Audience Manager-Signal: `c_a_LaunchesSinceUpgrade`

* **Gerätename**

   Speichert den Gerätenamen.

   * Analytics-Kontextdaten/Target-Parameter: `a.DeviceName`
   * Audience Manager-Signal: `c_a_DeviceName`

* **Betreibername**

   Speichert den vom Gerät angegebenen Namen des Mobilfunkanbieters.

   >[!IMPORTANT]
   >
   >Diese Metrik wird nicht automatisch in einer Analytics-Variable gespeichert. Sie müssen eine Verarbeitungsregel erstellen, um diesen Wert in eine Analytics-Variable für die Berichterstellung zu kopieren.

   * Analytics-Kontextdaten/Target-Parameter: `a.CarrierName`
   * Audience Manager-Signal: `c_a_CarrierName`

* **Auflösung**

   Breite x Höhe in Pixel.

   * Analytics-Kontextdaten/Target-Parameter: `a.Resolution`
   * Audience Manager-Signal: `c_a_Resolution`


## Zusätzliche Mobile-Metriken und -Dimensionen {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Die folgenden Metriken und Dimensionen werden mit der folgenden Methode in Variablen mobiler Lösungen erfasst:

### Metriken

* **Aktionsdauer insgesamt**

   Erfasst durch `trackTimedAction`-Methoden.

   * Analytics-Kontextdaten/Target-Parameter: `a.action.time.total`
   * Audience Manager-Signal: `c_a_action_time_total`

* **Aktionsdauer in Anwendung**

   Erfasst durch `trackTimedAction`-Methoden.
   * Analytics-Kontextdaten/Target-Parameter: `a.action.time.inapp`
   * Audience Manager-Signal: `c_a_action_time_inapp`

* **Lebenszeitwert (event)**

   Erfasst durch `trackLifetimeValue`-Methoden.

   * Analytics-Kontextdaten/Target-Parameter: `a.ltv.amount`
   * Audience Manager-Signal: `c_a_ltv_amount`

### Dimensionen

* **Standort (bis 10 km)**

   Erfasst durch `trackLocation`-Methoden.

   * Analytics-Kontextdaten/Zielgruppe-Parameter:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Manager-Eigenschaft(n):

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Standort (bis 100 m)**

   Erfasst durch `trackLocation`-Methoden.

   * Analytics-Kontextdaten/Zielgruppe-Parameter:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Manager-Eigenschaft(n):

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Standort (bis 1 m)**

   Erfasst durch `trackLocation`-Methoden.

   * Analytics-Kontextdaten/Zielgruppe-Parameter:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Manager-Eigenschaft(n):

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Zielpunkt-Bezeichnung**

   Populated by `trackLocation` methods when device is in a defined POI.

   * Analytics-Kontextdaten/Target-Parameter: `a.loc.poi`
   * Audience Manager trait: `c_a_loc_poi`

* **Entfernung zum Zentrum des Zielpunkts**

   Populated by `trackLocation` methods when device is within a defined POI.

   * Analytics-Kontextdaten/Target-Parameter: `a.loc.dist`
   * Audience Manager trait: `c_a_loc_dist`

* **Lebenszeitwert (Konversionsvariable)**

   Erfasst durch `trackLifetimeValue`-Methoden.

   * Analytics-Kontextdaten/Target-Parameter: `a.ltv.amount`
   * Audience Manager trait: `c_a_ltv_amount`
