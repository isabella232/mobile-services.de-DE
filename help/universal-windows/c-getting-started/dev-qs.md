---
description: 'null'
seo-description: 'null'
seo-title: Schnellstart für Entwickler
solution: Experience Cloud,Analytics
title: Schnellstart für Entwickler
topic: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 4%

---


# Schnellstart für Entwickler{#developer-quick-start}

Im Folgenden finden Sie einige Informationen zur Implementierung der universellen Windows-Plattformbibliothek.

>[!IMPORTANT]
>
>Zum Implementieren des SDK benötigen Sie Visual Studio 2013 oder höher.

## SDK abrufen   {#section_99FE1A17A36D4A2C943939023CF6265C}

Nachdem Sie die [SDK-Download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) -Datei entpackt haben, verfügen Sie für jede unterstützte Architektur- und Plattformkombination über einen separaten Ordner. Sie haben auch eine `ADBMobileConfig.json` Datei. Weitere Informationen zu dieser Datei finden Sie in der Konfigurationsdatei [ADBMobileConfig.json](/help/universal-windows/c-configuration/c.json.md).

## Wählen Sie die richtige Version {#section_E53C5AA7D5474824A89BB32C003865A1}

Für jede unterstützte Architektur (x86, x64, ARM) werden verschiedene `.dll/.winmd` Dateien bereitgestellt.

>[!IMPORTANT]
>
>Die Version von `ADBMobile.winmd` spiegelt nicht die Version der Bibliothek wider. Die `.winmd` Datei enthält nur Metadaten und verfügt über eine Versionsnummer `255.255.255.255`, die gemäß Microsoft akzeptiert wird. Weitere Informationen finden Sie unter [Wie füge ich Assemblyinformationen für eine WinRT C++/CX-Komponente hinzu?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). Um die Version der verwendeten Bibliothek zu überprüfen, überprüfen Sie die Version der zugrunde liegenden `ADBMobile.dll` Datei.

## Syntaxunterschiede {#section_A02DE120B6D240F5AFFE7509755C4F14}

Die universelle Windows-Plattform-Bibliothek kann in verschiedenen Programmiersprachen verwendet werden. Die Beispiele in diesem Handbuch sind in WinJS (JavaScript), wenn Sie eine andere Sprache verwenden, müssen möglicherweise geändert werden. Wenn Sie winmd-Methoden von winJS verwenden, wird bei allen Methoden automatisch der erste Buchstabe gekürzt.

Der Hauptunterschied zwischen den Implementierungen ist die für Kontextdaten verwendete Datenstruktur. Verwenden Sie außerdem bei Verwendung des SDK in einem WinJS-Projekt eine leere Zeichenfolge ( `""` oder `''`) anstelle `null` von Werten für leere Zeichenfolgen.

## Add the library and config File to your project - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Starten Sie Visual Studio und öffnen Sie Ihre Projektmappe.
1. Klicken Sie im **[!UICONTROL Projektmappen-Explorer]** mit der rechten Maustaste auf **[!UICONTROL Referenzen]** und wählen Sie **[!UICONTROL Hinzufügen Referenz]**.

1. Wählen Sie die richtige Version der Bibliothek und navigieren Sie zur zugehörigen Datei ADBMobile.winmd.

   Weitere Informationen finden Sie unter *Auswählen der richtigen Version* auf dieser Seite.

1. Klicken Sie auf **Hinzufügen**.

1. Vergewissern Sie sich, dass die Datei ADBMobile.winmd im Fenster **[!UICONTROL Reference Manager]** markiert ist, und klicken Sie auf **[!UICONTROL OK]**.

1. Klicken Sie im **[!UICONTROL Projektmappen-Explorer]** mit der rechten Maustaste auf **[!UICONTROL Referenzen]** und wählen Sie **[!UICONTROL Hinzufügen Referenz]**.

   Wenn auch ein C++-Projekt in Ihrer Lösung vorhanden ist, überspringen Sie diesen Schritt.

1. Wählen Sie auf der linken Registerkarte &quot; **[!UICONTROL Windows]** &quot;die Option &quot; **[!UICONTROL Erweiterungen]**&quot;, wählen Sie **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]** aus und fügen Sie sie hinzu.

1. hinzufügen Sie die folgende Zeile zu Ihrer Klasse:

   ```csharp
   using ADBMobile;
   ```

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt und klicken Sie auf **[!UICONTROL Hinzufügen]** > **[!UICONTROL Vorhandenes Element]**.

1. Navigieren Sie zur `ADBMobileConfig.json` Datei und klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Klicken Sie mit der rechten Maustaste auf die `ADBMobileConfig.json` Datei in Ihrer Lösung und wählen Sie **[!UICONTROL Eigenschaften]**.

1. Ändern Sie die Aktion **[!UICONTROL Erstellen]** in **[!UICONTROL Inhalt]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Starten Sie Visual Studio und öffnen Sie Ihre Projektmappe.
1. Klicken Sie im **[!UICONTROL Projektmappen-Explorer]** mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Hinzufügen]** > **[!UICONTROL Referenzen]**.

1. Wählen Sie die richtige Version der Bibliothek aus und fügen Sie der zugehörigen Datei ADBMobile.winmd einen Verweis hinzu.

   Weitere Informationen finden Sie unter *Auswählen der richtigen Version* auf dieser Seite.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Überprüfen Sie, ob diese Option im Fenster `ADBMobile.winmd` Referenz-Manager **[!UICONTROL aktiviert ist, und klicken Sie auf]** OK ****.

1. hinzufügen Sie die folgende Zeile zu Ihrer Klasse:

   ```c++
   using namespace ADBMobile;
   ```

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Hinzufügen]** > **[!UICONTROL Vorhandenes Element]**.

1. Navigieren Sie zur `ADBMobileConfig.json` Datei und klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Klicken Sie mit der rechten Maustaste auf die `ADBMobileConfig.json` Datei in Ihrer Lösung und wählen Sie **[!UICONTROL Eigenschaften]**.

1. Ändern Sie auf der Registerkarte &quot; **[!UICONTROL Allgemein]** &quot; **[!UICONTROL Inhalt]** in **[!UICONTROL Ja]** und klicken Sie auf **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Starten Sie Visual Studio und öffnen Sie Ihre Projektmappe.

1. Klicken Sie im **[!UICONTROL Projektmappen-Explorer]** mit der rechten Maustaste auf **[!UICONTROL Referenzen]** und wählen Sie **[!UICONTROL Hinzufügen Referenz]**.

1. Wählen Sie die richtige Version der Bibliothek und navigieren Sie zur zugehörigen Datei ADBMobile.winmd.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Vergewissern Sie sich, dass die Datei ADBMobile.winmd im Fenster **[!UICONTROL Reference Manager]** markiert ist, und klicken Sie auf **[!UICONTROL OK]**.

1. Klicken Sie im **[!UICONTROL Projektmappen-Explorer]** mit der rechten Maustaste auf **[!UICONTROL Referenzen]** und wählen Sie **[!UICONTROL Hinzufügen Referenz]**.

   Wenn auch ein C++-Projekt in Ihrer Lösung vorhanden ist, überspringen Sie diesen Schritt.

1. Wählen Sie auf der linken Registerkarte &quot; **[!UICONTROL Windows]** &quot;die Option &quot; **[!UICONTROL Erweiterungen]** &quot;und wählen Sie **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]** und fügen Sie sie hinzu.

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Hinzufügen]** > **[!UICONTROL Vorhandenes Element]**.

1. Navigieren Sie zur `ADBMobileConfig.json` Datei und klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Klicken Sie mit der rechten Maustaste auf die `ADBMobileConfig.json` Datei in Ihrer Lösung und wählen Sie **[!UICONTROL Eigenschaften]**.

1. Stellen Sie bei aktivierten **[!UICONTROL Dateieigenschaften]** sicher, dass **[!UICONTROL für die Paketaktion]** der **[!UICONTROL Inhalt]** festgelegt ist.

   Bei JavaScript-Projekten ist die Datei standardmäßig auf &quot;Inhalt&quot;eingestellt.

## ADBMobileConfig.json-Konfigurationsdatei aktualisieren {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

Die `ADBMobileConfig.json` Datei enthält globale SDK-Einstellungen und befindet sich im Projektstamm, nachdem Sie die Schritte im Abschnitt *Hinzufügen Bibliothek und Konfigurationsdatei für Ihr Projekt* ausgeführt haben. Wenn Ihre `ADBMobileConfig.json` Datei nicht von Adobe Mobile Services vorkonfiguriert wurde, müssen Sie zunächst einige Werte aktualisieren.

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

* **Adobe Analytics**: `rsids` und `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

For more information, see [SDK methods](/help/universal-windows/c-configuration/methods.md).

## Debugging von {#section_3A10376A60394A15BEE483323E0CD4AA}

Rufen Sie zum Aktivieren des Debuggens für das SDK auf `ADBMobile.Config.setDebugLogging(true);`.

Für C Sharp- und JavaScript-Apps müssen Sie das Debugging von nativem Code aktivieren, indem Sie die folgenden Schritte ausführen (für C++-Apps ist das native Code-Debugging die Standardeinstellung):

### C Scharf

1. Klicken Sie mit der rechten Maustaste auf das Projekt und klicken Sie auf **[!UICONTROL Eigenschaften]** > Registerkarte **[!UICONTROL Debuggen]**.

1. Ändern Sie die Dropdown-Liste &quot;Debugger-Typ&quot;in &quot; **Nur** nativ&quot;.

### JavaScript

1. Klicken Sie mit der rechten Maustaste auf das Projekt und dann auf die Registerkarte **[!UICONTROL Eigenschaften]** > **[!UICONTROL Konfigurationseigenschaften]** > **[!UICONTROL Debug]**.

1. Ändern Sie die Dropdown-Liste &quot;Debugger-Typ&quot;in &quot; **[!UICONTROL Nur]** nativ&quot;.

Das ist alles! Sie können jetzt Analytics, Zielgruppe und Audience-Management in Ihre Universal Windows Platform-App implementieren.

