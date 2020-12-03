---
description: Die folgenden Tabellen beinhalten die Metriken und Dimensionen, die nach der Implementierung des Lebenszyklus automatisch von der mobilen Bibliothek gemessen werden können.
seo-description: Die folgenden Tabellen beinhalten die Metriken und Dimensionen, die nach der Implementierung des Lebenszyklus automatisch von der mobilen Bibliothek gemessen werden können.
seo-title: Lebenszyklusmetriken
solution: Experience Cloud,Analytics
title: Lebenszyklusmetriken
topic: Developer and implementation
uuid: b795e383-d59b-4a3c-9e14-ffe8fb58412c
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1108'
ht-degree: 100%

---


# Lebenszyklusmetriken {#lifecycle-metrics}

Im Folgenden die Metriken und Dimensionen, die nach der Implementierung des Lebenszyklus automatisch von der mobilen Bibliothek gemessen werden können.

## Neue Version des Adobe Experience Platform Mobile SDK

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDK für die Adobe Experience Platform? Klicken Sie [hier](https://aep-sdks.gitbook.io/docs/), um unsere aktuelle Dokumentation abzurufen.

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDK können über [Experience Platform Launch](https://www.adobe.com/de/experience-platform/launch.html) konfiguriert werden.

* Gehen Sie zu [Experience Platform Launch](https://launch.adobe.com/), um zu beginnen.
* Gehen Sie zu [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK-Repositorys enthalten ist.


## Lebenszyklusmetriken und -dimensionen {#section_78F036C4296F4BA3A47C2044F79C86C1}

Nachdem die Lebenszyklusmetriken konfiguriert sind, werden die Metriken in Kontextdatenparametern an Analytics, in Parametern mit jedem Mbox-Aufruf an Target und als Signal an den Audience Manager gesendet. Analytics und Target verwenden dasselbe Format, während Audience Manager für jede Metrik ein anderes Präfix verwendet.

Für Analytics werden die mit jedem Lebenszyklus-Verfolgungsaufruf gesendeten Kontextdaten automatisch mithilfe der in der ersten Spalte aufgeführten Metrik oder Dimension erfasst und gemeldet.

>[!TIP]
>
>Ausnahmen sind in der Beschreibung angegeben.

### Metriken

* **Erste Starts**

   Wird beim ersten Ausführen nach einer Installation oder Neuinstallation ausgelöst.

   * Analytics-Kontextdaten/Target-Parameter: `a.InstallEvent`
   * Audience Manager-Signal: `c_a_InstallEvent`

* **Upgrades**

   Wird beim ersten Ausführen nach einer Aktualisierung oder immer dann, wenn sich die Versionsnummer ändert, ausgelöst.

   * Analytics-Kontextdaten/Target-Parameter: `a.UpgradeEvent`
   * Audience Manager-Signal: `c_a_UpgradeEvent`

* **Täglich eingesetzte Benutzer**

   wird ausgelöst, wenn die Anwendung an einem bestimmten Tag verwendet wird.

   * Analytics-Kontextdaten/Target-Parameter: `a.DailyEngUserEvent`
   * Audience Manager-Signal: `c_a_DailyEngUserEvent`

* **Monatlich beteiligte Benutzer**

   Wird ausgelöst, wenn die Anwendung während eines bestimmten Monats verwendet wird.

   * Analytics-Kontextdaten/Target-Parameter: `a.MonthlyEngUserEvent`
   * Audience Manager-Signal: `c_a_MonthlyEngUserEvent`

* **Starts**

   Wird bei jeder Ausführung ausgelöst, einschließlich Abstürzen und Installationen. Wird auch ausgelöst, wenn die App nach Überschreitung des Lebenszyklussitzungs-Timeouts aus dem Hintergrund fortgesetzt wird.

   * Analytics-Kontextdaten/Target-Parameter: `a.LaunchEvent`
   * Audience Manager-Signal: `c_a_LaunchEvent`

* **Abstürze**

   Wird ausgelöst, wenn die Anwendung beim Beenden nicht im Hintergrund ausgeführt wird. Das Ereignis wird gesendet, wenn die Anwendung nach einem Absturz neu gestartet wird.  Adobe Mobile-Absturz-Reporting implementiert keinen globalen Handler für nicht abgefangene Ausnahmen.

   * Analytics-Kontextdaten/Target-Parameter: `a.CrashEvent`
   * Audience Manager-Signal: `c_a_CrashEvent`

* **Länge der vorherigen Sitzung**

   Gibt die Dauer einer vorherigen Anwendungssitzung an, basierend darauf, wie lange die Anwendung geöffnet und im Vordergrund war.

   * Analytics-Kontextdaten/Target-Parameter: `a.PrevSessionLength`
   * Audience Manager-Signal: `c_a_PrevSessionLength`

>[!IMPORTANT]
>
> Die Metriken *Täglich beteiligte Benutzer* und *Monatlich beteiligte Benutzer* werden nicht automatisch in einer Analytics-Metrik gespeichert. Sie müssen eine Verarbeitungsregel erstellen, die ein benutzerdefiniertes Ereignis zum Erfassen dieser Metriken festlegt.

#### Dimensionen

* **Installationsdatum**

   Datum des ersten Starts nach der Installation.  Das Datumsformat ist `MM/DD/YYYY`.

   * Analytics-Kontextdaten/Target: `a.InstallDate`
   * Zielgruppen-Management: `c_a_InstallDate`

* **App-ID**

   Speichert den App-Namen und die Version im Format `[AppName] [BundleVersion]`. Beispiel: `myapp 1.1`.

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

   Uhrzeit, zu der die App gestartet wurde, im 24-Stunden-Format. Wird für die Zeitunterteilung verwendet, um Spitzennutzungszeiten zu ermitteln.

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

   Speichert den Gerätenamen.  Kommagetrennte zweistellige Zeichenfolge, die das iOS-Gerät angibt. Die erste Ziffer steht üblicherweise für die Gerätegeneration, die zweite weist die Version der verschiedenen Mitglieder der Gerätefamilie aus. Eine Liste gängiger Gerätenamen finden Sie unter    iOS-Geräteversionen.

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
   >Die Dimensionen *Tage seit der letzten Aktualisierung*, *Starts seit der letzten Aktualisierung* und *Betreibername* werden nicht automatisch in einer Analytics-Variablen gespeichert. Sie müssen eine Verarbeitungsregel erstellen, um die Werte in eine Analytics-Variable für die Berichterstellung zu kopieren.


## Zusätzliche Mobile-Metriken und -Dimensionen {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

Die folgenden Metriken und Dimensionen werden in Variablen mobiler Lösungen mit der aufgeführten Methode erfasst.

### Metriken

* **Aktionsdauer insgesamt**

   Erfasst durch trackTimedAction-Methoden.

   * Analytics-Kontextdaten/Target-Parameter: `a.action.time.total`
   * Zielgruppen-Management-Eigenschaft: `c_a_action_time_total`

* **Aktionsdauer in Anwendung**

   Erfasst durch trackTimedAction-Methoden.

   * Analytics-Kontextdaten/Target-Parameter: `a.action.time.inapp`
   * Zielgruppen-Management-Eigenschaft: `c_a_action_time_inapp`

* **Lebenszeitwert (event)**

   Erfasst durch trackLifetimeValue-Methoden.

   * Analytics-Kontextdaten/Target-Parameter: `a.ltv.amount`
   * Zielgruppen-Management-Eigenschaft: `c_a_ltv_amount`


### Dimensionen

* **Standort (bis 10 km)**

   Erfasst durch `trackLocation`-Methoden.

   * Analytics-Kontextdaten/Target-Parameter:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Zielgruppen-Management-Eigenschaft:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Standort (bis 100 m)**

   Erfasst durch trackLocation-Methoden.

   * Analytics-Kontextdaten/Target-Parameter:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Zielgruppen-Management-Eigenschaft:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Standort (bis 1 m)**

   Erfasst durch `trackLocation`-Methoden.

   * Analytics-Kontextdaten/Target-Parameter:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Zielgruppen-Management-Eigenschaft:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Zielpunkt-Bezeichnung**

   Wird durch trackLocation-Methoden aufgefüllt, wenn sich das Gerät in einem definierten POI befindet.

   * Analytics-Kontextdaten/Target-Parameter: `a.loc.poi`
   * Zielgruppen-Management-Eigenschaft: `c_a_loc_poi`

* **Entfernung zum Zentrum des Zielpunkts**

   Wird durch trackLocation-Methoden aufgefüllt, wenn sich das Gerät in einem definierten POI befindet.

   * Analytics-Kontextdaten/Target-Parameter: `a.loc.dist`
   * Zielgruppen-Management-Eigenschaft: `c_a_loc_dist`

* **Lebenszeitwert (Konversionsvariable)**

   Erfasst durch trackLifetimeValue-Methoden.

   * Analytics-Kontextdaten/Target-Parameter: `a.ltv.amount`
   * Zielgruppen-Management-Eigenschaft: `c_a_ltv_amount`

* **Rückverfolgungscode**

   Erfasst durch App-Akquise. Wird automatisch von Adobe Mobile Services generiert.

   * Analytics-Kontextdaten/Target-Parameter: `a.referrer.campaign.trackingcode`
   * Zielgruppen-Management-Eigenschaft: `c_a_referrer_campaign_trackingcode`

* **Kampagne**

   Name der Kampagne, ebenfalls gespeichert in der Kampagnenvariable. Erfasst durch App-Akquise.

   * Analytics-Kontextdaten/Target-Parameter: `a.referrer.campaign.name`
   * Zielgruppen-Management-Eigenschaft: `c_a_referrer_campaign_name`

* **Kampagneninhalt**

   Der Name oder die ID des Inhalts, der den Link angezeigt hat. Erfasst durch App-Akquise.

   * Analytics-Kontextdaten/Target-Parameter: `a.referrer.campaign.content`
   * Zielgruppen-Management-Eigenschaft: `c_a_referrer_campaign_content`

* **Kampagnenmedium**

   Marketing-Medium, z. B. ein Banner oder eine E-Mail. Erfasst durch App-Akquise.

   * Analytics-Kontextdaten/Target-Parameter: `a.referrer.campaign.medium`
   * Zielgruppen-Management-Eigenschaft: `c_a_referrer_campaign_medium`

* **Kampagnenquelle**

   Ursprünglicher Referrer, z. B. ein Newsletter oder ein Social Media-Netzwerk. Erfasst durch App-Akquise.

   * Analytics-Kontextdaten/Target-Parameter: `a.referrer.campaign.source`
   * Zielgruppen-Management-Eigenschaft: `c_a_referrer_campaign_source`

* **Kampagnenbegriff**

   Bezahlte Suchbegriffe oder andere Begriffe, die Sie mit dieser Akquise verfolgen möchten. Erfasst durch App-Akquise.

   * Analytics-Kontextdaten/Target-Parameter: `a.referrer.campaign.term`
   * Zielgruppen-Management-Eigenschaft: `c_a_referrer_campaign_term`
