---
description: Sie können die SDK-Analytics-Optionen beim Erstellen einer neuen App oder Bearbeiten einer bestehenden App auf der Seite „App-Einstellungen verwalten“ konfigurieren.
keywords: mobile
seo-description: Sie können die SDK-Analytics-Optionen beim Erstellen einer neuen App oder Bearbeiten einer bestehenden App auf der Seite „App-Einstellungen verwalten“ konfigurieren.
seo-title: SDK-Analytics-Optionen konfigurieren
solution: Marketing Cloud, Analytics
title: SDK-Analytics-Optionen konfigurieren
topic: Metriken
uuid: fd 3 a 21 d 2-6560-4 e 96-92 fe-b 99 caac 5 e 834
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Configure SDK Analytics options {#configure-sdk-analytics-options}

Sie können die SDK-Analytics-Optionen beim Erstellen einer neuen App oder Bearbeiten einer bestehenden App auf der Seite „App-Einstellungen verwalten“ konfigurieren.

Type information in the following fields under **[!UICONTROL SDK Analytics Options]**:

* **[!UICONTROL HTTPS verwenden]**

   Aktivieren Sie HTTPS, um die Sicherheit zu erhöhen.

* **[!UICONTROL Sitzungstreffer zurückdatieren]**

   Aktivieren oder deaktivieren Sie die Möglichkeit, dass das Adobe SDK Treffer mit Sitzungsinformationen zurückdatiert. Treffer mit Sitzungsinformationen enthalten derzeit Informationen zu Abstürzen und zur Sitzungsdauer. Wenn diese Einstellung aktiviert wird, datiert das Adobe-SDK Treffer mit Sitzungsinformationen auf 1 Sekunde nach dem letzten Treffer der vorherigen Sitzung zurück. Das bedeutet, dass die Daten zu Abstürzen und zur Sitzung mit dem korrekten Datum, an dem sie stattgefunden haben, korrelieren. Bei jedem Neustart der App wird ein Treffer zurückdatiert. Wenn diese Einstellung deaktiviert wird, hängt das Adobe-SDK die Sitzungsinformationen dem aktuellen Lebenszyklus an.

* **[!UICONTROL Datenschutz]**

   Wählen Sie eine Datenschutzoption aus:

   * **[!UICONTROL Daten bis Ausschluss senden]**
   * **[!UICONTROL Daten bis zur Teilnahme zurückhalten]**

* **[!UICONTROL Sitzungs-Timeout (Sekunden)]**

   Geben Sie einen Wert für das Sitzungs-Timeout an.

   Der Standardwert liegt bei 300 Sekunden. Legt die Dauer in Sekunden fest, die zwischen verschiedenen Startvorgängen einer App verstreichen muss, damit ein Startvorgang als neue Sitzung gilt. Dieses Zeitlimit wird auch angewendet, wenn eine Anwendung in den Hintergrund verschoben und später reaktiviert wird. Die Dauer, für welche die App im Hintergrund ausgeführt wird, wird nicht in die Sitzungsdauer eingerechnet.

* **[!UICONTROL Batch-Limit]**

   Geben Sie an, wie viele Treffer in die Warteschlange eingereiht werden sollen, bevor Daten gesendet werden.

   Wenn Treffer sofort gesendet werden sollen, legen Sie diesen Wert auf „0“ fest. Das Batch-Limit stellt den Schwellenwert für die Anzahl der Treffer dar, die in aufeinanderfolgenden Aufrufen gesendet werden sollen. Wenn diese Option beispielsweise auf „10“ festgelegt wird, wird jeder Treffer vor dem 10. Treffer in der Warteschlange abgelegt. Wenn der 10. Treffer eingeht, werden alle 10 Treffer nacheinander gesendet.

* **[!UICONTROL Mehr Infos]**

   Klicken Sie auf **[!UICONTROL Mehr Infos], um die Report Suite-ID und den Tracking-Server anzuzeigen, Offline-Tracking zu aktivieren bzw. zu deaktivieren und das verwendete Modell für die Zeichencodierung anzuzeigen (z. B. UTF-8).**

   Wenn Offline-Tracking aktiviert ist, werden Daten, die vom Gerät im Offline-Zustand generiert werden, mit einem Zeitstempel versehen und später gesendet. Wenn diese Option deaktiviert ist, werden Offline-Daten verworfen.
