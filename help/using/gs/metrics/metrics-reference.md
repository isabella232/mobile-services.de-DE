---
description: Im Folgenden finden Sie Referenzinformationen für standardmäßige mobile Metriken und Dimensionen.
keywords: mobile
seo-description: Im Folgenden finden Sie Referenzinformationen für standardmäßige mobile Metriken und Dimensionen.
seo-title: Referenz zu Mobile-Metriken und -Dimensionen
solution: Experience Cloud,Analytics
title: Referenz zu Mobile-Metriken und -Dimensionen
topic: Metrics
uuid: 96170ae7-8553-4f3e-ae01-65e5b664adf4
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 100%

---


# Hinweise zu Mobile-Metriken und -Dimensionen {#mobile-metrics-and-dimensions-reference}

Diese Informationen helfen Ihnen, mehr über die standardmäßigen Mobile-Metriken und- Dimensionen zu erfahren.

>[!TIP]
>
>Die in Adobe Analytics festgelegten Dimensions- und Metrikberechtigungen gelten auch für Mobile Services. Wenn Sie versuchen, einen Bericht ohne die entsprechenden Berechtigungen auszuführen, tritt ein Fehler auf.

## Metriken {#section_6704C815147D44AF96151D626BEB813C}

Hier finden Sie die Liste der standardmäßigen Mobile-Metriken:

* **Erste Starts**

   wird beim ersten Start nach der (erneuten) Installation ausgelöst.

* **Upgrades**

   wird beim ersten Start nach einem Upgrade oder einer Änderung der Versionsnummer ausgelöst.

* **Täglich eingesetzte Benutzer**

   wird ausgelöst, wenn die Anwendung an einem bestimmten Tag verwendet wird.

   >[!TIP]
   >
   >Das Ereignis „Täglich beteiligte Benutzer“ wird nicht automatisch in einer Analytics-Metrik gespeichert. Sie müssen eine Verarbeitungsregel erstellen, die ein benutzerdefiniertes Ereignis zum Erfassen dieser Metrik festlegt.

* **Monatlich beteiligte Benutzer**

   wird ausgelöst, wenn die Anwendung während eines Monats verwendet wird.

   >[!TIP]
   >Das Ereignis „Monatlich beteiligte Benutzer“ wird nicht automatisch in einer Analytics-Metrik gespeichert. Sie müssen eine Verarbeitungsregel erstellen, die ein benutzerdefiniertes Ereignis zum Erfassen dieser Metrik festlegt.

* **Starts**

   wird bei jedem Start ausgelöst, außer bei Installationen oder Upgrades. wird auch ausgelöst, wenn die Applikation aus dem Hintergrund gebracht wird. Standardmäßig wird ein Neustart ausgelöst, wenn die App mindestens fünf Minuten im Hintergrund ausgeführt wird. Die Dauer, über die die App im Hintergrund läuft, bevor ein Neustart ausgelöst wird, können Sie in den **[!UICONTROL SDK-Analytics-Optionen]** auf der Seite „App-Einstellungen verwalten“ konfigurieren. Weitere Informationen finden Sie in der Zeile *Sitzungs-Timeout (Sekunden)* unter [SDK-Analytics-Optionen konfigurieren](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/t-config-analytics.md).

   >[!IMPORTANT]
   >Aufgrund der Art der Berechnung von Besuchen in [!UICONTROL Adobe Analytics] und von App-Starts in [!UICONTROL Adobe Mobile Services] werden möglicherweise unterschiedliche Ergebnisse in den Berichten angezeigt. Weitere Informationen finden Sie unter [Besuche und App-Starts vergleichen](https://helpx.adobe.com/de/analytics/kb/compare-visits-and-mobile-app-launches.html).

* **Abstürze**

   Wird ausgelöst, wenn die Anwendung nicht ordnungsgemäß beendet wird. Dieses Ereignis wird gesendet, wenn die Anwendung nach einem Absturz gestartet wird.

   >[!TIP]
   >Die App gilt als abgestürzt, wenn kein Befehl zum Beenden aufgerufen wird.

* **Gesamtsitzungslänge**

   Aggregierte Gesamtlänge.

## Dimensionen {#section_1784C7E859F64CCEB95C5DD1DCF5C98D}

Hier finden Sie die Liste der standardmäßigen Mobile-Dimensionen:

* **Installationsdatum**

   Datum des ersten Starts nach der Installation. Das Datum wird im Format *MM/TT/JJJJ* angegeben.

* **App-ID**

   Speichert den Applikationsnamen und die Version im folgenden Format: `[AppName] [BundleVersion]`. Beispiel: `myapp 1.1`.

* **Startanzahl**

   Gibt an, wie oft die Applikation gestartet bzw. aus dem Hintergrund gebracht wurde.

* **Tage seit der ersten Verwendung**

   Anzahl der Tage seit dem ersten Start.

* **Tage seit der letzten Verwendung**

   Anzahl der Tage seit der letzten Verwendung.

* **Stunde des Tages**

   Uhrzeit, zu der die App gestartet wurde, im 24-Stunden-Format. Diese Dimension wird auch für die Zeitunterteilung verwendet, um Spitzennutzungszeiten zu ermitteln.

* **Wochentag**

   Nummer des Wochentags, an dem die Applikation gestartet wurde.

* **Betriebssystem**

   Betriebssystem des Geräts.

* **Betriebssystemversion**

   Betriebssystemversion.

* **Tage seit letztem Upgrade**

   Anzahl der Tage seit der Änderung der Versionsnummer der Applikation.

   >[!TIP]
   >
   >Die Tage seit letztem Upgrade werden nicht automatisch in einer Analytics-Variablen gespeichert. Sie müssen eine Verarbeitungsregel erstellen, um diesen Wert in eine Analytics-Variable für die Berichterstellung zu kopieren.

* **Starts seit letztem Upgrade**

   Anzahl der Starts seit der Änderung der Versionsnummer der Applikation.

   >[!TIP]
   >
   >Die Starts seit letztem Upgrade werden nicht automatisch in einer Analytics-Variablen gespeichert. Sie müssen eine Verarbeitungsregel erstellen, um diesen Wert in eine Analytics-Variable für die Berichterstellung zu kopieren.

* **Gerätename**

   Speichert den Gerätenamen. Unter iOS gibt eine kommagetrennte zweistellige Zeichenfolge das iOS-Gerät an. Die erste Ziffer steht für die Gerätegeneration, die zweite weist die Version der verschiedenen Mitglieder der Gerätefamilie aus. Eine vollständige Liste der allgemeinen Gerätenamen finden Sie unter [iOS-Geräteversionen](/help/ios/reference/device-versions.md).

* **Betreibername**

   Speichert den Namen des Mobilfunknetzbetreibers.

* **Auflösung**

   Breite und Höhe in Pixeln.
