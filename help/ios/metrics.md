---
description: Die folgende Tabelle enthält die Metriken und Dimensionen, die nach der Implementierung des Lebenszyklus automatisch von der mobilen Bibliothek gemessen werden können.
seo-description: Die folgende Tabelle enthält die Metriken und Dimensionen, die nach der Implementierung des Lebenszyklus automatisch von der mobilen Bibliothek gemessen werden können.
seo-title: Lebenszyklusmetriken
solution: Marketing Cloud,Analytics
title: Lebenszyklusmetriken
topic: Entwickler und Implementierung
uuid: b795e383-d59b-4a3c-9e14-ffe8fb58412c
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Lifecycle metrics {#lifecycle-metrics}

Hier sind die Metriken und Dimensionen, die nach der Implementierung des Lebenszyklus automatisch von der mobilen Bibliothek gemessen werden können.

## Neue Adobe Experience Cloud SDK-Version

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDKs für die Adobe Experience Platform? Klicken Sie für die neueste Dokumentation [hier](https://aep-sdks.gitbook.io/docs/).

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDKs können über die [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) konfiguriert werden.

* Gehen Sie zu Launch, um zu beginnen.
* Gehen Sie zu [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK Repositorys enthalten ist.

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Weitere Informationen finden Sie unter [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).


## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

Nachdem die Lebenszyklusmetriken konfiguriert sind, werden die Metriken in Kontextdatenparametern an Analytics, in Parametern mit jedem Mbox-Aufruf an Target und als Signal an den Audience Manager gesendet. Analytics und Target verwenden dasselbe Format, während Audience Manager für jede Metrik ein anderes Präfix verwendet.

Für Analytics werden die mit jedem Lebenszyklus-Verfolgungsaufruf gesendeten Kontextdaten automatisch mithilfe der in der ersten Spalte aufgeführten Metrik oder Dimension erfasst und gemeldet.

>[!TIP]
>
>Ausnahmen sind in der Beschreibung enthalten.

### Metriken

* **Erste Starts**

   Wird beim ersten Ausführen nach einer Installation oder Neuinstallation ausgelöst.

   * Analytics Context Data/Target parameter: `a.InstallEvent`
   * Audience Manager signal: `c_a_InstallEvent`

* **Upgrades**

   Wird beim ersten Ausführen nach einer Aktualisierung oder immer dann, wenn sich die Versionsnummer ändert, ausgelöst.

   * Analytics Context Data/Target parameter: `a.UpgradeEvent`
   * Audience Manager signal: `c_a_UpgradeEvent`

* **Täglich eingesetzte Benutzer**

   wird ausgelöst, wenn die Anwendung an einem bestimmten Tag verwendet wird.

   * Analytics Context Data/Target parameter: `a.DailyEngUserEvent`
   * Audience Manager signal: `c_a_DailyEngUserEvent`

* **Monatlich beteiligte Benutzer**

   Wird ausgelöst, wenn die Anwendung während eines bestimmten Monats verwendet wird.

   * Analytics Context Data/Target parameter: `a.MonthlyEngUserEvent`
   * Audience Manager signal: `c_a_MonthlyEngUserEvent`

* **Starts**

   Wird bei jeder Ausführung ausgelöst, einschließlich Abstürzen und Installationen. Wird auch ausgelöst, wenn die Anwendung nach Überschreitung der Lebenszyklus-Zeitüberschreitung aus dem Hintergrund geholt wird.

   * Analytics Context Data/Target parameter: `a.LaunchEvent`
   * Audience Manager signal: `c_a_LaunchEvent`

* **Abstürze**

   Wird ausgelöst, wenn die Anwendung beim Beenden nicht im Hintergrund ausgeführt wird. Das Ereignis wird gesendet, wenn die Anwendung nach einem Absturz neu gestartet wird.  Adobe Mobile-Absturz-Reporting implementiert keinen globalen Handler für nicht abgefangene Ausnahmen.

   * Analytics Context Data/Target parameter: `a.CrashEvent`
   * Audience Manager signal: `c_a_CrashEvent`

* **Länge der vorherigen Sitzung**

   Gibt die Dauer einer vorherigen Anwendungssitzung an, basierend darauf, wie lange die Anwendung geöffnet und im Vordergrund war.

   * Analytics Context Data/Target parameter: `a.PrevSessionLength`
   * Audience Manager signal: `c_a_PrevSessionLength`

>[!IMPORTANT]
>
> Die Metriken " *Täglich eingebundene Benutzer* "und " *Monatlich beteiligte Benutzer* "werden nicht automatisch in einer Analytics-Metrik gespeichert. Sie müssen eine Verarbeitungsregel erstellen, die ein benutzerspezifisches Ereignis zur Erfassung dieser Metriken einstellt.

### Dimensionen

* **Installationsdatum**

   Datum des ersten Starts nach der Installation.  The date format is .`MM/DD/YYYY`

   * Analytics-Kontextdaten/Target: `a.InstallDate`
   * Zielgruppen-Management: `c_a_InstallDate`

* **App-ID**

   Stores the Application name and version in the `[AppName] [BundleVersion]` format. Beispiel: `myapp 1.1`.

   * Analytics-Kontextdaten/Target: `a.AppID`
   * Zielgruppen-Management: `c_a_AppID`

* **Startanzahl**

   Gibt an, wie oft die Applikation gestartet bzw. aus dem Hintergrund gebracht wurde.

   * Analytics-Kontextdaten/Target: `a.Launches`
   * Zielgruppen-Management: `c_a_Launches`

* **Tage seit der ersten Benutzung**

   Anzahl der Tage seit dem ersten Ausführen.

   * Analytics-Kontextdaten/Target: `a.DaysSinceFirstUse`
   * Zielgruppen-Management: `c_a_DaysSinceFirstUse`

* **Tage seit der letzten Benutzung**

   Anzahl der Tage seit der letzten Verwendung.

   * Analytics-Kontextdaten/Target: `a.DaysSinceLastUse`
   * Zielgruppen-Management: `c_a_DaysSinceLastUse`

* **Stunde des Tages**

   Misst, zu welcher Stunde die Anwendung gestartet wurde; es wird ein 24-Stunden-Format genutzt. Wird für die Zeitaufteilung verwendet, um Spitzennutzungszeiten zu ermitteln.

   * Analytics-Kontextdaten/Target: `a.HourOfDay`
   * Zielgruppen-Management: `c_a_HourOfDay`

* **Wochentag**

   Nummer des Wochentags, an dem die Applikation gestartet wurde.

   * Analytics-Kontextdaten/Target: `a.DayOfWeek`
   * Zielgruppen-Management: `c_a_DayOfWeek`

* **Betriebssystemversion**

   Anzahl der Tage seit der Änderung der Versionsnummer der Applikation.

   * Analytics-Kontextdaten/Target: `a.OSVersion`
   * Zielgruppen-Management: `c_a_OSVersion|OS version`

* **Tage seit der letzten Aktualisierung**

   Tage seit der letzten Aktualisierung.

   * Analytics-Kontextdaten/Target: `a.DaysSinceLastUpgrade`
   * Zielgruppen-Management: `c_a_DaysSinceLastUpgrade`

* **Starts seit der letzten Aktualisierung**

   Anzahl der Starts seit der Änderung der Versionsnummer der Applikation.

   * Analytics-Kontextdaten/Target: `a.LaunchesSinceUpgrade`
   * Zielgruppen-Management: `c_a_LaunchesSinceUpgrade`

* **Gerätename**

   Speichert den Gerätenamen.  Zweistellige, kommagetrennte Zeichenfolge, die das iOS-Gerät angibt. Die erste Ziffer steht üblicherweise für die Gerätegeneration, die zweite weist die Version der verschiedenen Mitglieder der Gerätefamilie aus. Eine Liste gängiger Gerätenamen finden Sie unter  iOS-Geräteversionen.

   * Analytics-Kontextdaten/Target: `a.DeviceName`
   * Zielgruppen-Management: `c_a_DeviceName`

* **Betreibername**

   Speichert den vom Gerät angegebenen Namen des Mobilfunkanbieters.

   * Analytics-Kontextdaten/Target: `a.CarrierName`
   * Zielgruppen-Management: `c_a_CarrierName`

* **Auflösung**

   Breite x Höhe in Pixel.

   * Analytics-Kontextdaten/Target: `a.Resolution`
   * Zielgruppen-Management: `c_a_Resolution`
   >[!IMPORTANT]
   >
   >The Days since last upgrade, Launches since last upgrade, and the Carrier Name dimensions are not automatically stored in an Analytics variable. ****** Sie müssen eine Verarbeitungsregel erstellen, um die Werte zur Berichterstellung in eine Analytics-Variable zu kopieren.


## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Die folgenden Metriken und Dimensionen werden in Variablen mobiler Lösungen mit der aufgeführten Methode erfasst.

### Metriken

* **Aktionsdauer insgesamt**

   Erfasst durch trackTimedAction-Methoden.

   * Analytics Context Data/Target parameter: `a.action.time.total`
   * Audience Management trait: `c_a_action_time_total`

* **Aktionsdauer in Anwendung**

   Erfasst durch trackTimedAction-Methoden.

   * Analytics Context Data/Target parameter: `a.action.time.inapp`
   * Audience Management trait: `c_a_action_time_inapp`

* **Lebenszeitwert (event)**

   Erfasst durch trackLifetimeValue-Methoden.

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Audience Management trait: `c_a_ltv_amount`


### Dimensionen

* **Standort (bis 10 km)**

   Populated by `trackLocation` methods.

   * Analytics-Kontextdaten/Target-Parameter:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Eigenschaft Zielgruppen-Management:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Standort (bis 100 m)**

   Erfasst durch trackLocation-Methoden.

   * Analytics-Kontextdaten/Target-Parameter:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Eigenschaft Zielgruppen-Management:

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

   Wird durch trackLocation-Methoden aufgefüllt, wenn sich das Gerät in einem definierten POI befindet.

   * Analytics Context Data/Target parameter: `a.loc.poi`
   * Audience Management trait: `c_a_loc_poi`

* **Entfernung zum Zentrum des Zielpunkts**

   Wird durch trackLocation-Methoden aufgefüllt, wenn sich das Gerät in einem definierten POI befindet.

   * Analytics Context Data/Target parameter: `a.loc.dist`
   * Audience Management trait: `c_a_loc_dist`

* **Lebenszeitwert (Konversionsvariable)**

   Erfasst durch trackLifetimeValue-Methoden.

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Audience Management trait: `c_a_ltv_amount`

* **Rückverfolgungscode**

   Erfasst durch App-Akquise. Automatisch von Adobe Mobile Services generiert.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.trackingcode`
   * Audience Management trait: `c_a_referrer_campaign_trackingcode`

* **Kampagne**

   Name der Kampagne, ebenfalls gespeichert in der Kampagnenvariable. Erfasst durch App-Akquise.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.name`
   * Audience Management trait: `c_a_referrer_campaign_name`

* **Kampagneninhalt**

   Der Name der ID des Inhalts, in dem der Link angezeigt wurde. Erfasst durch App-Akquise.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.content`
   * Audience Management trait: `c_a_referrer_campaign_content`

* **Kampagnenmedium**

   Marketingmedium, z. B. Banner oder E-Mail. Erfasst durch App-Akquise.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.medium`
   * Audience Management trait: `c_a_referrer_campaign_medium`

* **Kampagnenquelle**

   Ursprünglicher Referrer, wie z. B. Newsletter oder soziales Netzwerk. Erfasst durch App-Akquise.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.source`
   * Audience Management trait: `c_a_referrer_campaign_source`

* **Kampagnenbegriff**

   Bezahlte Keywords oder andere Begriffe, die Sie mit dieser Akquise verfolgen wollen. Erfasst durch App-Akquise.

   * Analytics Context Data/Target parameter: `a.referrer.campaign.term`
   * Audience Management trait: `c_a_referrer_campaign_term`
