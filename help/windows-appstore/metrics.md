---
description: Listet die Metriken und Dimensionen auf, die automatisch von der Mobile-Bibliothek gemessen werden können.
keywords: Android;Bibliothek;Mobile;SDK
solution: Experience Cloud Services,Analytics
title: Lebenszyklusmetriken
topic-fix: Developer and implementation
uuid: c483271f-f620-46f4-aad8-d5f02d763f7d
exl-id: a1e4eeca-8b8f-47ca-a489-acc338238c42
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 64%

---

# Lebenszyklusmetriken{#lifecycle-metrics}

Listet die Metriken und Dimensionen auf, die automatisch von der Mobile-Bibliothek gemessen werden können.

Weitere Informationen finden Sie unter [Fehlerbehebung bei Lebenszyklusdaten](https://helpx.adobe.com/de/analytics/kb/troubleshoot-lifecycle-data.html).

## Lebenszyklusmetriken und -dimensionen {#section_78F036C4296F4BA3A47C2044F79C86C1}

Wenn Lebenszyklusmetriken konfiguriert sind, werden sie in Kontextdatenparametern an Analytics, in Parametern mit jedem Mbox-Aufruf an Target und als Signal an den Audience Manager gesendet. Analytics und Target verwenden dasselbe Format und Audience Manager verwendet für jede Metrik ein anderes Präfix.

Für Analytics werden die Kontextdaten, die mit jedem Lebenszyklus-Verfolgungsaufruf gesendet werden, automatisch mithilfe der unten aufgeführten Metrik oder Dimension erfasst und gemeldet. Ausnahmen werden vermerkt.

### Metriken

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

   >[!TIP]
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

   Wird bei jeder Ausführung ausgelöst, einschließlich Abstürzen und Installationen. Wird auch bei einer Wiederaufnahme aus dem Hintergrund ausgelöst, wenn das Sitzungs-Timeout des Lebenszyklus überschritten wurde.

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

### Dimensionen

* **Installationsdatum**

   Datum des ersten Starts nach der Installation. Das Datumsformat ist `MM/DD/YYYY`.

   * Analytics-Kontextdaten/Target: `a.InstallDate`
   * Audience Manager: `c_a_InstallDate`

* **App-ID**

   Speichert den App-Namen und die Version im Format `[AppName] [BundleVersion]`. Ein Beispiel für dieses Format ist `myapp 1.1`.

   * Analytics-Kontextdaten/Target: `a.AppID`
   * Audience Manager: `c_a_AppID`

* **Startanzahl**

   Gibt an, wie oft die Applikation gestartet bzw. aus dem Hintergrund gebracht wurde.

   * Analytics-Kontextdaten/Target: `a.Launches`
   * Audience Manager: `c_a_Launches`

* **Tage seit der ersten Benutzung**

   Anzahl der Tage seit dem ersten Start

   * Analytics-Kontextdaten/Target: `a.DaysSinceFirstUse`
   * Audience Manager: `c_a_DaysSinceFirstUse`

* **Tage seit der letzten Benutzung**

   Anzahl der Tage seit der letzten Verwendung.

   * Analytics-Kontextdaten/Target: `a.DaysSinceLastUse`
   * Audience Manager: `c_a_DaysSinceLastUse`

* **Stunde des Tages**

   Erfasst die Stunde, in der die App gestartet wurde. Diese Metrik verwendet das 24-Stunden-Zahlenformat und wird zur Zeitdarstellung verwendet, um die Spitzennutzungszeiten zu bestimmen.

   * Analytics-Kontextdaten/Target: `a.HourOfDay`
   * Audience Manager: `c_a_HourOfDay`

* **Wochentag**

   Anzahl der Wochentage, an denen die App gestartet wurde.

   * Analytics-Kontextdaten/Target: `a.DayOfWeek`
   * Audience Manager: `c_a_DayOfWeek`

* **Betriebssystemversion**

   Die Betriebssystemversion.

   * Analytics-Kontextdaten/Target: `a.OSVersion`
   * Audience Manager: `c_a_OSVersion`

* **Tage seit der letzten Aktualisierung**

   Anzahl der Tage seit der Änderung der Versionsnummer der Applikation.

   >[!IMPORTANT]
   >
   >Diese Metrik wird nicht automatisch in einer Analytics-Variable gespeichert. Sie müssen eine Verarbeitungsregel erstellen, um diesen Wert in eine Analytics-Variable für die Berichterstellung zu kopieren.

   * Analytics-Kontextdaten/Target: `a.DaysSinceLastUpgrade`
   * Audience Manager: `c_a_DaysSinceLastUpgrade`

* **Starts seit der letzten Aktualisierung**

   Anzahl der Starts seit der Änderung der Versionsnummer der Applikation.

   >[!IMPORTANT]
   >
   >Diese Metrik wird nicht automatisch in einer Analytics-Variable gespeichert. Sie müssen eine Verarbeitungsregel erstellen, um diesen Wert in eine Analytics-Variable für die Berichterstellung zu kopieren.

   * Analytics-Kontextdaten/Target: `a.LaunchesSinceUpgrade`
   * Audience Manager: `c_a_LaunchesSinceUpgrade`

* **Gerätename**

   Speichert den Gerätenamen.

   * Analytics-Kontextdaten/Target: `a.DeviceName`
   * Audience Manager: `c_a_DeviceName`

* **Betreibername**

   Speichert den vom Gerät angegebenen Namen des Mobilfunkanbieters.

   >[!IMPORTANT]
   >
   >Diese Metrik wird nicht automatisch in einer Analytics-Variable gespeichert. Sie müssen eine Verarbeitungsregel erstellen, um diesen Wert in eine Analytics-Variable für die Berichterstellung zu kopieren.

   * Analytics-Kontextdaten/Target: `a.CarrierName`
   * Audience Manager: `c_a_CarrierName`

* **Auflösung**

   Breite x Höhe in Pixel.

   * Analytics-Kontextdaten/Target: `a.Resolution`
   * Audience Manager: `c_a_Resolution`


## Zusätzliche Mobile-Metriken und -Dimensionen {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Die folgenden Metriken und Dimensionen werden mithilfe der in der Beschreibung aufgeführten Methoden in Variablen mobiler Lösungen erfasst.

### Metriken

* **Aktionsdauer insgesamt**

   Erfasst durch `trackTimedAction`-Methoden.

   * Analytics-Kontextdaten/Target-Parameter: `a.action.time.total`
   * Audience Manager-Eigenschaft: `c_a_action_time_total`

* **Aktionsdauer in Anwendung**

   Erfasst durch `trackTimedAction`-Methoden.

   * Analytics-Kontextdaten/Target-Parameter: `a.action.time.inapp`
   * Audience Manager-Eigenschaft: `c_a_action_time_inapp`

* **Lebenszeitwert (event)**

   Erfasst durch `trackLifetimeValue`-Methoden.

   * Analytics-Kontextdaten/Target-Parameter: `a.ltv.amount`
   * Audience Manager-Eigenschaft: `c_a_ltv_amount`

## Dimensionen

* **Standort (bis 10 km)**

   Erfasst durch `trackLocation`-Methoden.

   * Analytics-Kontextdaten/Target-Parameter:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Manager-Eigenschaft:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Standort (bis 100 m)**

   Erfasst durch `trackLocation`-Methoden.

   * Analytics-Kontextdaten/Target-Parameter:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Manager-Eigenschaft:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Standort (bis 1 m)**

   Erfasst durch `trackLocation`-Methoden.

   * Analytics-Kontextdaten/Target-Parameter:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Manager-Eigenschaft:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Zielpunkt-Bezeichnung**

   Erfasst durch `trackLocation` Methoden, wenn sich das Gerät innerhalb eines definierten Zielpunkts befindet.

   * Analytics-Kontextdaten/Target-Parameter: `a.loc.poi`
   * Audience Manager-Eigenschaft: `c_a_loc_poi`

* **Entfernung zum Zentrum des Zielpunkts**

   Erfasst durch `trackLocation` Methoden, wenn sich das Gerät innerhalb eines definierten Zielpunkts befindet.

   * Analytics-Kontextdaten/Target-Parameter: `a.loc.dist`
   * Audience Manager-Eigenschaft: `c_a_loc_dist`

* **Lebenszeitwert (Konversionsvariable)**

   Erfasst durch `trackLifetimeValue`-Methoden.

   * Analytics-Kontextdaten/Target-Parameter: `a.ltv.amount`
   * Audience Manager-Eigenschaft: `c_a_ltv_amount`
