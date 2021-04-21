---
description: Informationen zum Implementieren der universellen Windows-Plattformbibliothek.
solution: Experience Cloud,Analytics
title: Schnellstart für Entwickler
topic-fix: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
exl-id: 28fc2a96-907e-41fc-a798-3e8d43fc7616
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 4%

---

# Schnellstart für Entwickler{#developer-quick-start}

Im Folgenden finden Sie einige Informationen zur Implementierung der universellen Windows-Plattformbibliothek.

>[!IMPORTANT]
>
>Zum Implementieren des SDK benötigen Sie Visual Studio 2013 oder höher.

## SDK abrufen   {#section_99FE1A17A36D4A2C943939023CF6265C}

Nachdem Sie die Datei [SDK-Download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) entpackt haben, verfügen Sie über einen separaten Ordner für jede unterstützte Architektur- und Plattformkombination. Sie haben auch eine `ADBMobileConfig.json`-Datei. Weitere Informationen zu dieser Datei finden Sie unter [ADBMobileConfig.json config file](/help/universal-windows/c-configuration/c.json.md).

## Wählen Sie die richtige Version {#section_E53C5AA7D5474824A89BB32C003865A1}

Für jede unterstützte Architektur (x86, x64, ARM) werden verschiedene `.dll/.winmd`-Dateien bereitgestellt.

>[!IMPORTANT]
>
>Die Version von `ADBMobile.winmd` spiegelt nicht die Version der Bibliothek wider. Die `.winmd`-Datei enthält nur Metadaten und hat eine Versionsnummer von `255.255.255.255`, was nach Microsoft akzeptiert wird. Weitere Informationen finden Sie unter [Wie füge ich Assemblyinformationen für eine WinRT C++/CX-Komponente hinzu?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). Um die Version der verwendeten Bibliothek zu überprüfen, überprüfen Sie die Version der zugrunde liegenden Datei `ADBMobile.dll`.

## Syntaxunterschiede {#section_A02DE120B6D240F5AFFE7509755C4F14}

Die universelle Windows-Plattform-Bibliothek kann in verschiedenen Programmiersprachen verwendet werden. Die Beispiele in diesem Handbuch sind in WinJS (JavaScript), wenn Sie eine andere Sprache verwenden, müssen möglicherweise geändert werden. Wenn Sie winmd-Methoden von winJS verwenden, wird bei allen Methoden automatisch der erste Buchstabe gekürzt.

Der Hauptunterschied zwischen den Implementierungen ist die für Kontextdaten verwendete Datenstruktur. Verwenden Sie außerdem bei Verwendung des SDK in einem WinJS-Projekt eine leere Zeichenfolge ( `""` oder `''`) anstelle von `null` für leere Zeichenfolgenwerte.

## Bibliothek und Konfigurationsdatei in Ihr Projekt Hinzufügen - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Starten Sie Visual Studio und öffnen Sie Ihre Projektmappe.
1. Klicken Sie im **[!UICONTROL Projektmappen-Explorer]** mit der rechten Maustaste auf **[!UICONTROL References]** und wählen Sie **[!UICONTROL Hinzufügen Reference]**.

1. Wählen Sie die richtige Version der Bibliothek und navigieren Sie zur zugehörigen Datei ADBMobile.winmd.

   Weitere Informationen finden Sie im Abschnitt *Wählen Sie die richtige Version* auf dieser Seite.

1. Klicken Sie auf **Hinzufügen**.

1. Vergewissern Sie sich, dass die Datei ADBMobile.winmd im Fenster **[!UICONTROL Referenz-Manager]** markiert ist, und klicken Sie auf **[!UICONTROL OK]**.

1. Klicken Sie im **[!UICONTROL Projektmappen-Explorer]** mit der rechten Maustaste auf **[!UICONTROL References]** und wählen Sie **[!UICONTROL Hinzufügen Reference]**.

   Wenn auch ein C++-Projekt in Ihrer Lösung vorhanden ist, überspringen Sie diesen Schritt.

1. Wählen Sie auf der linken Registerkarte **[!UICONTROL Windows]** die Option **[!UICONTROL Erweiterungen]** aus und fügen Sie **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]** hinzu.

1. hinzufügen Sie die folgende Zeile zu Ihrer Klasse:

   ```csharp
   using ADBMobile;
   ```

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt und klicken Sie auf **[!UICONTROL Hinzufügen]** > **[!UICONTROL Vorhandenes Element]**.

1. Navigieren Sie zur Datei `ADBMobileConfig.json` und klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Klicken Sie mit der rechten Maustaste auf die Datei `ADBMobileConfig.json` in Ihrer Lösung und wählen Sie **[!UICONTROL Eigenschaften]**.

1. Ändern Sie **[!UICONTROL Aktion erstellen]** in **[!UICONTROL Inhalt]**.

## hinzufügen Sie die Bibliotheks- und Konfigurationsdatei in Ihr Projekt - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Starten Sie Visual Studio und öffnen Sie Ihre Projektmappe.
1. Klicken Sie im **[!UICONTROL Projektmappen-Explorer]** mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Hinzufügen]** > **[!UICONTROL Referenzen]**.

1. Wählen Sie die richtige Version der Bibliothek aus und fügen Sie der zugehörigen Datei ADBMobile.winmd einen Verweis hinzu.

   Weitere Informationen finden Sie im Abschnitt *Wählen Sie die richtige Version* auf dieser Seite.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Vergewissern Sie sich, dass `ADBMobile.winmd` im Fenster **[!UICONTROL Referenz-Manager]** markiert ist, und klicken Sie auf **[!UICONTROL OK]**.

1. hinzufügen Sie die folgende Zeile zu Ihrer Klasse:

   ```c++
   using namespace ADBMobile;
   ```

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Hinzufügen]** > **[!UICONTROL Vorhandenes Element]**.

1. Navigieren Sie zur Datei `ADBMobileConfig.json` und klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Klicken Sie mit der rechten Maustaste auf die Datei `ADBMobileConfig.json` in Ihrer Lösung und wählen Sie **[!UICONTROL Eigenschaften]**.

1. Ändern Sie auf der Registerkarte **[!UICONTROL Allgemein]** **[!UICONTROL Inhalt]** in **[!UICONTROL Ja]** und klicken Sie auf **[!UICONTROL OK]**.

## hinzufügen Sie die Bibliotheks- und Konfigurationsdatei in Ihr Projekt - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Starten Sie Visual Studio und öffnen Sie Ihre Projektmappe.

1. Klicken Sie im **[!UICONTROL Projektmappen-Explorer]** mit der rechten Maustaste auf **[!UICONTROL References]** und wählen Sie **[!UICONTROL Hinzufügen Reference]**.

1. Wählen Sie die richtige Version der Bibliothek und navigieren Sie zur zugehörigen Datei ADBMobile.winmd.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Vergewissern Sie sich, dass die Datei ADBMobile.winmd im Fenster **[!UICONTROL Referenz-Manager]** markiert ist, und klicken Sie auf **[!UICONTROL OK]**.

1. Klicken Sie im **[!UICONTROL Projektmappen-Explorer]** mit der rechten Maustaste auf **[!UICONTROL References]** und wählen Sie **[!UICONTROL Hinzufügen Reference]**.

   Wenn auch ein C++-Projekt in Ihrer Lösung vorhanden ist, überspringen Sie diesen Schritt.

1. Wählen Sie auf der linken Registerkarte **[!UICONTROL Windows]** die Option **[!UICONTROL Erweiterungen]** und wählen Sie **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]** und fügen Sie diese hinzu.

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Hinzufügen]** > **[!UICONTROL Vorhandenes Element]**.

1. Navigieren Sie zur Datei `ADBMobileConfig.json` und klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Klicken Sie mit der rechten Maustaste auf die Datei `ADBMobileConfig.json` in Ihrer Lösung und wählen Sie **[!UICONTROL Eigenschaften]**.

1. Wenn **[!UICONTROL Dateieigenschaften]** ausgewählt ist, stellen Sie sicher, dass **[!UICONTROL Paketaktion]** auf **[!UICONTROL Inhalt]** eingestellt ist.

   Bei JavaScript-Projekten ist die Datei standardmäßig auf &quot;Inhalt&quot;eingestellt.

## ADBMobileConfig.json-Konfigurationsdatei {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE} aktualisieren

Die Datei `ADBMobileConfig.json` enthält globale SDK-Einstellungen und befindet sich im Projektstamm, nachdem Sie die Schritte im Abschnitt *Hinzufügen der Bibliotheks- und Konfigurationsdatei zu Ihrem Projekt* ausgeführt haben. Wenn Ihre `ADBMobileConfig.json`-Datei nicht von Adobe Mobile Services vorkonfiguriert wurde, müssen Sie zunächst einige Werte aktualisieren.

Im Folgenden finden Sie ein Beispiel für eine `ADBMobileConfig.json`-Datei:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 300, 
        "privacyDefault" : "optedin", 
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000], 
                    ["santa cruz",36.972935,-122.01725,600] 
                ] 
    }, 
 "target" : { 
  "clientCode" : "myTargetClientCode", 
  "timeout" : 1 
 }, 
 "audienceManager" : { 
  "server" : "myServer.demdex.com" 
 } 
}
```

Aktualisieren Sie mindestens die folgenden Werte für die verwendeten Lösungen:

* **Adobe Analytics**:  `rsids` und  `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

Weitere Informationen finden Sie unter [SDK-Methoden](/help/universal-windows/c-configuration/methods.md).

## Debugging von {#section_3A10376A60394A15BEE483323E0CD4AA}

Rufen Sie zum Aktivieren des Debuggens für das SDK `ADBMobile.Config.setDebugLogging(true);` auf.

Für C Sharp- und JavaScript-Apps müssen Sie das Debugging von nativem Code aktivieren, indem Sie die folgenden Schritte ausführen (für C++-Apps ist das native Code-Debugging die Standardeinstellung):

### C Scharf

1. Klicken Sie mit der rechten Maustaste auf das Projekt und dann auf **[!UICONTROL Eigenschaften]** > **[!UICONTROL Registerkarte Debuggen]**.

1. Ändern Sie die Dropdown-Liste für den Debugger-Typ in **Nur nativ**.

### JavaScript

1. Klicken Sie mit der rechten Maustaste auf das Projekt und dann auf **[!UICONTROL Eigenschaften]** > **[!UICONTROL Konfigurationseigenschaften]** > **[!UICONTROL Registerkarte Debuggen]**.

1. Ändern Sie die Dropdown-Liste für den Debugger-Typ in **[!UICONTROL Nur nativ]**.

Das ist alles! Sie können jetzt Analytics, Zielgruppe und Audience-Management in Ihre Universal Windows Platform-App implementieren.
