---
description: Im Folgenden sehen Sie die Metriken und Dimensionen, die von der Mobile-Bibliothek automatisch gemessen werden können, nachdem der Lebenszyklus implementiert wurde, sowie eine Verknüpfung zur Problembehandlung von Lebenszyklusdaten.
keywords: android;library;mobile;sdk
seo-description: Im Folgenden sehen Sie die Metriken und Dimensionen, die von der Mobile-Bibliothek automatisch gemessen werden können, nachdem der Lebenszyklus implementiert wurde, sowie eine Verknüpfung zur Problembehandlung von Lebenszyklusdaten.
seo-title: Lebenszyklusmetriken
solution: Marketing Cloud, Analytics
title: Lebenszyklusmetriken
topic: Entwickler und Implementierung
uuid: a8f3ebac-be3b-4948-82bb-105d46cfff6d
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Lifecycle metrics{#lifecycle-metrics}

This section provides information about the metrics and dimensions that can be measured automatically by the mobile library, after lifecycle is implemented, and a link to troubleshoot Lifecycle data. Weitere Informationen zur Fehlerbehebung finden Sie unter [Fehlerbehebung bei Lebenszyklusdaten](https://helpx.adobe.com/analytics/kb/troubleshoot-lifecycle-data.html).

## Neue Adobe Experience Cloud SDK-Version

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDKs für die Adobe Experience Platform? Klicken Sie für die neueste Dokumentation [hier](https://aep-sdks.gitbook.io/docs/).

>[!IMPORTANT]
>
>Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDKs können über die [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) konfiguriert werden.

* Gehen Sie zu [Launch](https://launch.adobe.com/), um zu beginnen.
* Gehen Sie zu [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK Repositorys enthalten ist.

## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

Wenn Lebenszyklusmetriken konfiguriert sind, werden sie in Kontextdatenparametern an Analytics, bei jedem mbox-Aufruf in Parametern an Target sowie als Signale an das Zielgruppen-Management gesendet. Analytics und Target verwenden dasselbe Format, während das Zielgruppen-Management ein anderes Präfix für jede Metrik verwendet.

For Analytics, the context data that is sent with each lifecycle tracking call is automatically captured in and reported on by using the metric or dimension, and the exceptions are noted.

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

   >[!IMPORTANT]
   >
   >This metric is not automatically stored in an Analytics metric. Sie müssen eine Verarbeitungsregel erstellen, die ein benutzerdefiniertes Ereignis zum Erfassen dieser Metrik festlegt.

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

   Wird bei jeder Ausführung ausgelöst, auch nach Abstürzen und Installationen. Wird auch bei einer Wiederaufnahme aus dem Hintergrund ausgelöst, wenn das Timeout der Lebenszyklussitzung überschritten wurde.

   >[!IMPORTANT]
   >
   >Diese Metrik wird nicht automatisch in einer Analytics-Metrik gespeichert. Sie müssen eine Verarbeitungsregel erstellen, die ein benutzerdefiniertes Ereignis zum Erfassen dieser Metrik festlegt.

   * Analytics-Kontextdaten/Target-Parameter: `a.LaunchEvent`
   * Audience Manager-Signal: `c_a_LaunchEvent`

* **Abstürze**

   Wird ausgelöst, wenn die Anwendung beim Beenden nicht im Hintergrund ausgeführt wird. Das Ereignis wird gesendet, wenn die Anwendung nach dem Absturz gestartet wird.  Adobe Mobile-Absturz-Reporting implementiert keinen globalen Handler für nicht abgefangene Ausnahmen.

   * Analytics-Kontextdaten/Target-Parameter: `a.CrashEvent`
   * Audience Manager-Signal: `c_a_CrashEvent`

* **Länge der vorherigen Sitzung**

   Gibt die Dauer einer vorherigen Anwendungssitzung in Sekunden an, basierend darauf, wie lange die Anwendung geöffnet und im Vordergrund war.

   * Analytics-Kontextdaten/Target-Parameter: `a.PrevSessionLength`
   * Audience Manager-Signal: `c_a_PrevSessionLength`


### Dimensionen

* **Installationsdatum**

   Datum des ersten Starts nach der Installation. Das Datumsformat lautet MM/TT/JJJJ.

   * Analytics-Kontextdaten/Target-Parameter: `a.InstallDate`
   * Audience Manager: `c_a_InstallDate`

* **App-ID**

   Stores the application name and version in the `[AppName] [BundleVersion]` format. Ein Beispiel für dieses Format ist `myapp 1.1`.

   * Analytics-Kontextdaten/Target-Parameter: `a.AppID`
   * Audience Manager: `c_a_AppID`

* **Startanzahl**

   Gibt an, wie oft die Applikation gestartet bzw. aus dem Hintergrund gebracht wurde.

   * Analytics-Kontextdaten/Target-Parameter: `a.Launches`
   * Audience Manager: `c_a_Launches`

* **Tage seit der ersten Benutzung**

   Anzahl der Tage seit dem ersten Start

   * Analytics-Kontextdaten/Target-Parameter: `a.DaysSinceFirstUse`
   * Audience Manager: `c_a_DaysSinceFirstUse`

* **Tage seit der letzten Benutzung**

   Anzahl der Tage seit der letzten Verwendung.

   * Analytics-Kontextdaten/Target-Parameter: `a.DaysSinceLastUse`
   * Audience Manager: `c_a_DaysSinceLastUse`

* **Stunde des Tages**

   Erfasst die Stunde, in der die App gestartet wurde.  Diese Metrik verwendet das 24-Stunden-Zahlenformat und wird zur Zeitdarstellung verwendet, um die Spitzennutzungszeiten zu bestimmen.

   * Analytics-Kontextdaten/Target-Parameter: `a.HourOfDay`
   * Audience Manager: `c_a_HourOfDay`

* **Wochentag**

   Anzahl der Wochentage, an denen die App gestartet wurde.

   * Analytics-Kontextdaten/Target-Parameter: `a.DayOfWeek`
   * Audience Manager: `c_a_DayOfWeek`

* **Betriebssystemversion**

   Die Betriebssystemversion.

   * Analytics-Kontextdaten/Target-Parameter: `a.OSVersion`
   * Audience Manager: `c_a_OSVersion`

* **Tage seit der letzten Aktualisierung**

   Anzahl der Tage seit der Änderung der Versionsnummer der Applikation.

   >[!IMPORTANT]
   >
   >Diese Metrik wird nicht automatisch in einer Analytics-Variablen gespeichert. Sie müssen eine Verarbeitungsregel erstellen, um diesen Wert in eine Analytics-Variable für die Berichterstellung zu kopieren.

   * Analytics-Kontextdaten/Target-Parameter: `a.DaysSinceLastUpgrade`
   * Audience Manager: `c_a_DaysSinceLastUpgrade`

* **Starts seit der letzten Aktualisierung**

   Anzahl der Starts seit der Änderung der Versionsnummer der Applikation.

   >[!IMPORTANT]
   >
   >Diese Metrik wird nicht automatisch in einer Analytics-Variablen gespeichert. Sie müssen eine Verarbeitungsregel erstellen, um diesen Wert in eine Analytics-Variable für die Berichterstellung zu kopieren.

   * Analytics-Kontextdaten/Target-Parameter: `a.LaunchesSinceUpgrade`
   * Audience Manager: `c_a_LaunchesSinceUpgrade`

* **Gerätename**

   Speichert den Gerätenamen.

   * Analytics-Kontextdaten/Target-Parameter: `a.DeviceName`
   * Audience Manager: `c_a_DeviceName`

* **Betreibername**

   Speichert den vom Gerät angegebenen Namen des Mobilfunkanbieters.  Wichtig: Dieser Messwert wird nicht automatisch in einer Analytics-Variablen gespeichert. Sie müssen eine Verarbeitungsregel erstellen, um diesen Wert in eine Analytics-Variable für die Berichterstellung zu kopieren.

   >[!IMPORTANT]
   >
   >Diese Metrik wird nicht automatisch in einer Analytics-Variablen gespeichert. Sie müssen eine Verarbeitungsregel erstellen, um diesen Wert in eine Analytics-Variable für die Berichterstellung zu kopieren.

   * Analytics-Kontextdaten/Target-Parameter: `a.CarrierName`
   * Audience Manager: `c_a_CarrierName`

* **Auflösung**

   Breite x Höhe in Pixel.

   * Analytics-Kontextdaten/Target-Parameter: `a.Resolution`
   * Audience Manager: `c_a_Resolution`

## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Die folgenden Metriken und Dimensionen werden von der Methode in der Spalte **Beschreibung** in den Variablen der mobilen Lösung erfasst.

### Metriken

* **Aktionsdauer insgesamt**

   Populated by `trackTimedAction` methods.

   * Analytics-Kontextdaten/Target-Parameter: `a.action.time.total`
   * Eigenschaften von Audience Manager: `c_a_action_time_total`

* **Aktionsdauer in Anwendung**

   Populated by `trackTimedAction` methods.

   * Analytics-Kontextdaten/Target-Parameter: `a.action.time.inapp`
   * Eigenschaften von Audience Manager: `c_a_action_time_inapp`

* **Lebenszeitwert (event)**

   Populated by `trackLifetimeValue` methods.

   * Analytics-Kontextdaten/Target-Parameter: `a.ltv.amount`
   * Eigenschaften von Audience Manager: `c_a_ltv_amount`

### Dimensionen

* **Standort (bis 10 km)**

   Populated by `trackLocation` methods.

   * Analytics-Kontextdaten/Target-Parameter:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Eigenschaften von Audience Manager:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Standort (bis 100 m)**

   Erfasst durch trackLocation-Methoden.

   * Analytics-Kontextdaten/Target-Parameter:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Eigenschaften von Audience Manager:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Standort (bis 1 m)**

   Erfasst durch trackLocation-Methoden.

   * Analytics Context Data/Target Parameters:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Eigenschaften von Audience Manager:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Zielpunkt-Bezeichnung**

   Erfasst durch trackLocation-Methoden, wenn sich das Gerät an einem POI befindet.

   * Analytics Context Data/Target Parameters: `a.loc.poi`
   * Eigenschaften von Audience Manager: `c_a_loc_poi`

* **Entfernung zum Zentrum des Zielpunkts**

   Erfasst durch trackLocation-Methoden, wenn sich das Gerät an einem POI befindet.

   * Analytics Context Data/Target Parameters: `a.loc.dist`
   * Eigenschaften von Audience Manager: `c_a_loc_dist`

* **Lebenszeitwert (Konversionsvariable)**

   Erfasst durch trackLifetimeValue-Methoden.

   * Analytics Context Data/Target Parameters: `a.ltv.amount`
   * Audience Manager Trait: `c_a_ltv_amount`

* **Rückverfolgungscode**

   Wird von Mobile App – Akquise erfasst und automatisch von Adobe Mobile Services generiert.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.trackingcode`
   * Audience Manager Trait: `c_a_referrer_campaign_trackingcode`

* ** Kampagne

   Name der Kampagne, ebenfalls gespeichert in der Kampagnenvariable. Erfasst durch App-Akquise.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.name`
   * Eigenschaften von Audience Manager: `c_a_referrer_campaign_name`

* **Kampagneninhalt**

   Der Name der ID des Inhalts, in dem der Link angezeigt wurde. Erfasst durch App-Akquise.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.content`
   * Eigenschaften von Audience Manager: `c_a_referrer_campaign_content`

* **Kampagnenmedium**

   Marketingmedium, beispielsweise ein Banner oder eine E-Mail. Erfasst durch App-Akquise.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.medium`
   * Eigenschaften von Audience Manager: `c_a_referrer_campaign_medium`

* **Kampagnenquelle**

   Ursprünglicher Referrer, wie z. B. Newsletter oder soziales Netzwerk. Erfasst durch App-Akquise.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.source`
   * Audience Manager Trait: `c_a_referrer_campaign_source`

* **Kampagnenbegriff**

   Bezahlte Keywords oder andere Begriffe, die Sie mit dieser Akquise verfolgen wollen. Erfasst durch App-Akquise.

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.term`
   * Audience Manager Trait: `c_a_referrer_campaign_term`
