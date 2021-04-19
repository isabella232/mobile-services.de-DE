---
description: Sie können die SDK-Analytics-Optionen beim Erstellen einer neuen App oder Bearbeiten einer bestehenden App auf der Seite „App-Einstellungen verwalten“ konfigurieren.
keywords: mobile
seo-description: Sie können die SDK-Analytics-Optionen beim Erstellen einer neuen App oder Bearbeiten einer bestehenden App auf der Seite „App-Einstellungen verwalten“ konfigurieren.
seo-title: SDK-Analytics-Optionen konfigurieren
solution: Experience Cloud,Analytics
title: SDK-Analytics-Optionen konfigurieren
topic-fix: Metrics
uuid: fd3a21d2-6560-4e96-92fe-b99caac5e834
exl-id: f2c35b65-1052-4bfc-af9d-8778e4ff0522
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 100%

---

# SDK-Analytics-Optionen konfigurieren {#configure-sdk-analytics-options}

Sie können die SDK-Analytics-Optionen beim Erstellen einer neuen App oder Bearbeiten einer bestehenden App auf der Seite „App-Einstellungen verwalten“ konfigurieren.

Geben Sie Informationen in die folgenden Felder unter **[!UICONTROL SDK-Analytics-Optionen]** ein:

* **[!UICONTROL HTTPS verwenden]**

   Aktivieren Sie HTTPS, um die Sicherheit zu erhöhen.

* **[!UICONTROL Sitzungstreffer zurückdatieren]**

   Aktivieren oder deaktivieren Sie die Möglichkeit, dass das Adobe-SDK Treffer mit Sitzungsinformationen zurückdatiert. Treffer mit Sitzungsinformationen enthalten derzeit Informationen zu Abstürzen und zur Sitzungsdauer. Wenn aktiviert, datiert das Adobe SDK den Treffer mit Sitzungsinformation auf 1 Sekunde nach dem letzten Treffer in der vorherigen Sitzung zurück. Das bedeutet, dass Abstürze und Sitzungsdaten dem korrekten Datum, an dem sie aufgetreten sind, entsprechen. Bei jedem Neustart der App wird ein Treffer zurückdatiert. Wenn diese Einstellung deaktiviert wird, hängt das Adobe-SDK die Sitzungsinformationen dem aktuellen Lebenszyklus an.

* **[!UICONTROL Datenschutz]**

   Wählen Sie eine Datenschutzoption aus:

   * **[!UICONTROL Daten bis Opt-out senden]**
   * **[!UICONTROL Daten bis Opt-in zurückhalten]**

* **[!UICONTROL Sitzungs-Timeout (Sekunden)]**

   Geben Sie einen Wert für das Sitzungs-Timeout an.

   Der Standardwert liegt bei 300 Sekunden. Gibt die Dauer in Sekunden an, die zwischen dem App-Starts verstreichen muss, damit der Start als neue Sitzung erachtet wird. Dieses Time-out gilt auch, wenn Ihre Anwendung in den Hintergrund gestellt und reaktiviert wird. Die Zeit, die Ihre App im Hintergrund ist, ist nicht in der Sitzungslänge enthalten.

* **[!UICONTROL Batch-Limit]**

   Geben Sie an, wie viele Treffer in die Warteschlange eingereiht werden sollen, bevor Daten gesendet werden.

   Wenn Treffer sofort gesendet werden sollen, legen Sie diesen Wert auf „0“ fest. Das Batch-Limit stellt den Grenzwert für die Anzahl der Treffer dar, die in aufeinanderfolgenden Aufrufen gesendet werden sollen. Wenn diese Option beispielsweise auf 10 festgelegt ist, wird jeder Treffer vor dem 10. Treffer in der Warteschlange gespeichert. Beim 10. Treffer werden alle 10 Treffer nacheinander gesendet.

* **[!UICONTROL Mehr Infos]**

   Klicken Sie auf **[!UICONTROL Mehr Infos]**, um die Report Suite-ID und den Trackingserver anzuzeigen, Offline-Tracking zu aktivieren bzw. zu deaktivieren und das verwendete Modell für die Zeichencodierung anzuzeigen (z. B. UTF-8).

   Wenn Offline-Tracking aktiviert ist, werden vom Gerät offline erstellte Daten mit einem Zeitstempel versehen und später gesendet. Wenn diese Option deaktiviert ist, werden die Offline-Daten verworfen.
