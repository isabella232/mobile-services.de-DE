---
description: Im Folgenden finden Sie Referenzinformationen für standardmäßige mobile Metriken und Dimensionen.
keywords: mobile
seo-description: Im Folgenden finden Sie Referenzinformationen für standardmäßige mobile Metriken und Dimensionen.
seo-title: Referenz zu Mobile-Metriken und -Dimensionen
solution: Marketing Cloud, Analytics
title: Referenz zu Mobile-Metriken und -Dimensionen
topic: Metriken
uuid: 96170 ae 7-8553-4 f 3 e-ae 01-65 e 5 b 664 adf 4
translation-type: tm+mt
source-git-commit: 056bb3edb94c2ceb2961bbe8e4851c20429e1ea2

---


# Mobile metrics and dimensions reference {#mobile-metrics-and-dimensions-reference}

Anhand dieser Informationen können Sie mehr über die standardmäßigen Mobile-Metriken und -dimensionen erfahren.

>[!TIP]
>
>Die in Adobe Analytics festgelegten Berechtigungen für Dimension und Metrik gelten für Mobile Services. Wenn Sie versuchen, einen Bericht ohne die entsprechenden Berechtigungen auszuführen, tritt ein Fehler auf.

## Metriken {#section_6704C815147D44AF96151D626BEB813C}

Hier finden Sie die Liste der standardmäßigen Mobile-Metriken:

* **Erste Starts**

   wird beim ersten Start nach der (erneuten) Installation ausgelöst.

* **Upgrades**

   wird beim ersten Start nach einem Upgrade oder einer Änderung der Versionsnummer ausgelöst.

* **Täglich eingesetzte Benutzer**

   wird ausgelöst, wenn die Anwendung an einem bestimmten Tag verwendet wird.

   >[!TIP]
   >Das Ereignis "Täglich beteiligte Benutzer" wird nicht automatisch in einer Analytics-Metrik gespeichert. Sie müssen eine Verarbeitungsregel erstellen, die ein benutzerdefiniertes Ereignis zum Erfassen dieser Metrik festlegt.

* **Monatlich beteiligte Benutzer**

   wird ausgelöst, wenn die Anwendung während eines Monats verwendet wird.

   >[!TIP]
   >Das Ereignis "Monatlich beteiligte Benutzer" wird nicht automatisch in einer Analytics-Metrik gespeichert. Sie müssen eine Verarbeitungsregel erstellen, die ein benutzerdefiniertes Ereignis zum Erfassen dieser Metrik festlegt.

* **Starts**

   wird bei jedem Start ausgelöst, außer bei Installationen oder Upgrades. wird auch ausgelöst, wenn die Applikation aus dem Hintergrund gebracht wird. Standardmäßig wird ein Neustart ausgelöst, wenn die App mindestens fünf Minuten im Hintergrund ausgeführt wird. The amount of background time before triggering a new launch can be configured in **[!UICONTROL SDK Analytics Options]** on the Manage App Settings page. Weitere Informationen finden Sie in der *Sitzungszeitüberschreitung (Sekunden)* unter [SDK-Analytics-Optionen konfigurieren](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/t-config-analytics.md).

   >[!IMPORTANT]
   >Because how visits in [!UICONTROL Adobe Analytics] and mobile app launches in [!UICONTROL Adobe Mobile Services] are calculated, you might see different results in reporting. Weitere Informationen finden Sie unter [Besuche und App-Starts vergleichen](https://helpx.adobe.com/analytics/kb/compare-visits-and-mobile-app-launches.html).

* **Abstürze**

   wird ausgelöst, wenn die App nicht ordnungsgemäß vom Benutzer beendet wird. Dieses Ereignis wird gesendet, wenn die App nach einem Absturz startet.

   >[!TIP]
   >Die Anwendung wird als Absturz betrachtet, wenn sie nicht aufgerufen wird.

* **Gesamtsitzungslänge**

   Aggregierte Gesamtlänge.

## Dimensionen {#section_1784C7E859F64CCEB95C5DD1DCF5C98D}

Hier finden Sie die Liste der Standardabmessungen für Mobilgeräte:

* **Installationsdatum**

   Datum des ersten Starts nach der Installation. Das Datum liegt im Format *MM/TT/JJJJ* vor.

* **App-ID**

   Speichert den Applikationsnamen und die Version im folgenden Format: `[AppName] [BundleVersion]`. Beispiel: `myapp 1.1`.

* **Startanzahl**

   Gibt an, wie oft die Applikation gestartet bzw. aus dem Hintergrund gebracht wurde.

* **Tage seit der ersten Verwendung**

   Anzahl der Tage seit dem ersten Start

* **Tage seit der letzten Verwendung**

   Anzahl der Tage seit der letzten Verwendung.

* **Stunde des Tages**

   Uhrzeit, zu der die App gestartet wurde, im 24-Stunden-Format. Diese Dimension wird auch für die Zeitunterteilung verwendet, um Spitzennutzungszeiten zu ermitteln.

* **Wochentag**

   Nummer des Wochentags, an dem die Applikation gestartet wurde.

* **Betriebssystem**

   Betriebssystem des Geräts

* **Betriebssystemversion**

   Betriebssystemversion

* **Tage seit letztem Upgrade**

   Anzahl der Tage seit der Änderung der Versionsnummer der Applikation.

   >[!TIP]
   >
   >Tage seit der letzten Aktualisierung werden nicht automatisch in einer Analytics-Variablen gespeichert. Sie müssen eine Verarbeitungsregel erstellen, um diesen Wert in eine Analytics-Variable für die Berichterstellung zu kopieren.

* **Starts seit letztem Upgrade**

   Anzahl der Starts seit der Änderung der Versionsnummer der Applikation.

   >[!TIP]
   >
   >Starts seit der letzten Aktualisierung werden nicht automatisch in einer Analytics-Variablen gespeichert. Sie müssen eine Verarbeitungsregel erstellen, um diesen Wert in eine Analytics-Variable für die Berichterstellung zu kopieren.

* **Gerätename**

   Speichert den Gerätenamen. In ios bezeichnet eine zweistellige Zeichenfolge das ios-Gerät. Die erste Zahl stellt die Gerätegenerierung dar und die zweiten Versionen der Gerätefamilie. Eine vollständige Liste der allgemeinen Gerätenamen finden Sie unter [iOS-Geräteversionen](/help/ios/reference/device-versions.md).

* **Betreibername**

   Speichert den Namen des Mobilfunknetzbetreibers.

* **Auflösung**

   Breite und Höhe in Pixeln
