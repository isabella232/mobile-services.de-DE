---
description: Sie können die SDK-Analytics-Optionen beim Erstellen einer neuen App oder Bearbeiten einer bestehenden App auf der Seite „App-Einstellungen verwalten“ konfigurieren.
keywords: mobile
seo-description: Sie können die SDK-Analytics-Optionen beim Erstellen einer neuen App oder Bearbeiten einer bestehenden App auf der Seite „App-Einstellungen verwalten“ konfigurieren.
seo-title: SDK-Analytics-Optionen konfigurieren
solution: Experience Cloud,Analytics
title: SDK-Analytics-Optionen konfigurieren
topic: Metrics
uuid: fd3a21d2-6560-4e96-92fe-b99caac5e834
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 65%

---


# SDK-Analytics-Optionen konfigurieren {#configure-sdk-analytics-options}

Sie können die SDK-Analytics-Optionen beim Erstellen einer neuen App oder Bearbeiten einer bestehenden App auf der Seite „App-Einstellungen verwalten“ konfigurieren.

Geben Sie Informationen in die folgenden Felder unter **[!UICONTROL SDK-Analytics-Optionen]** ein:

* **[!UICONTROL HTTPS verwenden]**

   Aktivieren Sie HTTPS, um die Sicherheit zu erhöhen.

* **[!UICONTROL Sitzungstreffer zurückdatieren]**

   Aktivieren oder deaktivieren Sie die Möglichkeit, dass das Adobe-SDK Treffer mit Sitzungsinformationen zurückdatiert. Treffer mit Sitzungsinformationen enthalten derzeit Informationen zu Abstürzen und zur Sitzungsdauer. Wenn diese Option aktiviert ist, datiert das Adobe-SDK den Treffer für Sitzungsinformationen auf 1 Sekunde nach dem letzten Treffer der vorherigen Sitzung zurück. Das bedeutet, dass Abstürze und Sitzungsdaten mit dem richtigen Datum, an dem sie stattgefunden haben, korrelieren. Bei jedem Neustart der App wird ein Treffer zurückdatiert. Wenn diese Einstellung deaktiviert wird, hängt das Adobe-SDK die Sitzungsinformationen dem aktuellen Lebenszyklus an.

* **[!UICONTROL Datenschutz]**

   Wählen Sie eine Datenschutzoption aus:

   * **[!UICONTROL Daten bis Ausschluss senden]**
   * **[!UICONTROL Daten bis zur Teilnahme zurückhalten]**

* **[!UICONTROL Sitzungs-Timeout (Sekunden)]**

   Geben Sie einen Wert für das Sitzungs-Timeout an.

   Der Standardwert liegt bei 300 Sekunden. Gibt die Zeitdauer in Sekunden an, die vergehen muss, bevor der Start als neue Sitzung gezählt wird. Dieses Time-out gilt auch, wenn Ihre Anwendung in den Hintergrund gestellt und reaktiviert wird. Die Zeit, die Ihre App im Hintergrund ist, ist nicht in der Sitzungslänge enthalten.

* **[!UICONTROL Batch-Limit]**

   Geben Sie an, wie viele Treffer in die Warteschlange eingereiht werden sollen, bevor Daten gesendet werden.

   Wenn Treffer sofort gesendet werden sollen, legen Sie diesen Wert auf „0“ fest. Die Batch-Beschränkung stellt den Schwellenwert für die Anzahl der Treffer dar, die in aufeinander folgenden Aufrufen gesendet werden sollen. Wenn diese Option beispielsweise auf 10 gesetzt ist, wird jeder Treffer vor dem 10. Treffer in der Warteschlange gespeichert. Wenn der 10. Treffer eingeht, werden alle 10 Treffer nacheinander gesendet.

* **[!UICONTROL Mehr Infos]**

   Klicken Sie auf **[!UICONTROL Mehr Infos]**, um die Report Suite-ID und den Tracking-Server anzuzeigen, Offline-Tracking zu aktivieren bzw. zu deaktivieren und das verwendete Modell für die Zeichencodierung anzuzeigen (z. B. UTF-8).

   Wenn die Offline-Verfolgung aktiviert ist, werden vom Gerät erstellte Daten mit einem Zeitstempel versehen und später gesendet. Wenn diese Option deaktiviert ist, werden Offlinedaten verworfen.
