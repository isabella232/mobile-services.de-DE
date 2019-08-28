---
description: Die Akquise-Verfolgung muss in der SDK-Konfiguration aktiviert sein, bevor Sie Marketing-Links verfolgen und Berichte erstellen können.
keywords: mobile
seo-description: Die Akquise-Verfolgung muss in der SDK-Konfiguration aktiviert sein, bevor Sie Marketing-Links verfolgen und Berichte erstellen können.
seo-title: Akquise konfigurieren
solution: Marketing Cloud, Analytics
title: Akquise konfigurieren
topic: Metriken
uuid: e 996 e 43 e -8 a 77-47 a 3-a 6 fb -53 f 676 f 92 bef
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Akquise konfigurieren {#configure-acquisition}

Die Akquise-Verfolgung muss in der SDK-Konfiguration aktiviert sein, bevor Sie Marketing-Links verfolgen und Berichte erstellen können.

1. Rufen Sie die Seite App-Einstellungen verwalten für die gewünschte App auf und scrollen Sie zum Abschnitt **[!UICONTROL SDK-Akquise-Optionen]** herunter.
1. Führen Sie die folgenden Aufgaben durch:

   * To enable Acquisition, select the **[!UICONTROL Enable]** check box.

      When you select this check box, the **[!UICONTROL Referrer Timeout]** field becomes active, and the value changes from 0 to 5.

   * Geben Sie einen Wert in das Feld **[!UICONTROL Referrer-Timeout (Sekunden)]** ein.

      (**Optional**) Wenn Sie das Kontrollkästchen **[!UICONTROL Aktivieren]** aktiviert haben, ist dieses Feld optional. Sie können den Timeout-Wert ändern, indem Sie einen Sekundenwert eingeben. Diese Einstellung gibt den Zeitraum an, der auf Akquise-Informationen gewartet werden soll, bevor der erste Start-Treffer gesendet wird.
   >[!IMPORTANT]
   >Sie müssen einen Wert ungleich null eingeben. Wenn Sie Akquise aktivieren, den Wert aber als null belassen, funktionieren Akquise-Links nicht. Es wird empfohlen, den Standardwert von 5 Sekunden zu verwenden.

1. Laden Sie die neue SDK-Konfigurationsdatei herunter und verwenden Sie sie in Ihrer App.

   Sie haben die Akquise für **iOS** erfolgreich konfiguriert.
To enable Acquisition on **Android**, complete the steps in [Tracking Mobile Acquisition](/help/android/acquisition-main/acquisition.md).
