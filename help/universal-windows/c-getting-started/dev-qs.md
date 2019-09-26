---
description: 'null'
seo-description: 'null'
seo-title: Developer quick start
solution: Marketing Cloud,Analytics
title: Schnellstart für Entwickler
topic: Entwickler und Implementierung
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start{#developer-quick-start}

Im Folgenden finden Sie einige Informationen zur Implementierung der universellen Windows-Plattformbibliothek.

>[!IMPORTANT]
>
>Zum Implementieren des SDK benötigen Sie Visual Studio 2013 oder höher.

## SDK abrufen {#section_99FE1A17A36D4A2C943939023CF6265C}

After you unzip the [SDK download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) file, you will have a separate folder for each supported architecture and platform combination. Sie haben auch eine `ADBMobileConfig.json` Datei. Weitere Informationen zu dieser Datei finden Sie in der Konfigurationsdatei [ADBMobileConfig.json](/help/universal-windows/c-configuration/c.json.md).

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll/.winmd` files are provided for each supported architecture (x86, x64, ARM).

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. Die `.winmd` Datei enthält nur Metadaten und verfügt über eine Versionsnummer `255.255.255.255`, die gemäß Microsoft akzeptiert wird. Weitere Informationen finden Sie unter [Wie kann ich Assemblyinformationen für eine WinRT C++/CX-Komponente hinzufügen?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## Unterschiede in der Syntax {#section_A02DE120B6D240F5AFFE7509755C4F14}

Die Bibliothek für die universelle Windows-Plattform kann in mehreren Programmiersprachen verwendet werden. Die Beispiele in diesem Handbuch sind in WinJS (JavaScript), wenn Sie eine andere Sprache verwenden, müssen möglicherweise geändert werden. Wenn Sie winmd-Methoden von winJS verwenden, wird bei allen Methoden automatisch der erste Buchstabe verringert.

Der Hauptunterschied zwischen den verschiedenen Implementierungen besteht in der für die Kontextdaten verwendeten Datenstruktur. Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config File to your project - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Starten Sie Visual Studio und öffnen Sie Ihre Lösung.
1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

1. Select the correct version  of the library and browse to the associated ADBMobile.winmd file.

   Weitere Informationen finden Sie unter *Auswählen der richtigen Version* auf dieser Seite.

1. Klicken Sie auf **Hinzufügen**.

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Wenn auch ein C++-Projekt in Ihrer Lösung vorhanden ist, überspringen Sie diesen Schritt.

1. Wählen Sie auf der linken Registerkarte " **[!UICONTROL Windows]** "die Option " **[!UICONTROL Erweiterungen]**", wählen Sie **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]** aus und fügen Sie sie hinzu.

1. Fügen Sie Ihrer Klasse die folgende Zeile hinzu:

   ```csharp
   using ADBMobile;
   ```

1. Right-click your project and click **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Klicken Sie mit der rechten Maustaste auf die `ADBMobileConfig.json` Datei in Ihrer Lösung und wählen Sie **[!UICONTROL Eigenschaften]**.

1. Change **[!UICONTROL Build Action]** to **[!UICONTROL Content]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Starten Sie Visual Studio und öffnen Sie Ihre Lösung.
1. In the **[!UICONTROL Solution Explorer]**, right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL References]**.

1. Wählen Sie die richtige Version der Bibliothek aus und fügen Sie der zugehörigen Datei ADBMobile.winmd einen Verweis hinzu.

   Weitere Informationen finden Sie unter *Auswählen der richtigen Version* auf dieser Seite.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Vergewissern Sie sich, dass `ADBMobile.winmd` im Fenster **Reference Manager (Referenz-Manager)** markiert ist, und klicken Sie auf **[!UICONTROL OK]**.

1. Fügen Sie Ihrer Klasse die folgende Zeile hinzu:

   ```c++
   using namespace ADBMobile;
   ```

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. On the **[!UICONTROL General]** tab, change **[!UICONTROL Content]** to **[!UICONTROL Yes]** and click **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Starten Sie Visual Studio und öffnen Sie Ihre Lösung.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

1. Select the correct version of the library and browse to the associated ADBMobile.winmd file.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   If you also have a C++ project in your solution, skip this step.

1. In the Windows tab on the left, select Extensions and select and add Visual C++ 2015 Runtime for Universal Windows Platform Apps.************

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. With **[!UICONTROL File Properties]** selected, ensure **[!UICONTROL Package Action]** is set to **[!UICONTROL Content]**.

   For JavaScript projects, the file is set to Content by default.

## Update The ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

The `ADBMobileConfig.json` file contains global SDK settings and is located at your project root after you complete the steps in the *Add the library and config file to your project* section. If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

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

## Debugging {#section_3A10376A60394A15BEE483323E0CD4AA}

To enable debugging for the SDK, call `ADBMobile.Config.setDebugLogging(true);`.

Für C Sharp- und JavaScript-Apps müssen Sie das Debugging von nativem Code aktivieren, indem Sie die folgenden Schritte ausführen (für C++-Apps ist das native Code-Debugging die Standardeinstellung):

### C Sharp

1. Klicken Sie mit der rechten Maustaste auf das Projekt und klicken Sie auf **[!UICONTROL Eigenschaften]** &gt; Registerkarte **[!UICONTROL Debuggen]**.

1. Ändern Sie das Dropdown für den Debuggertyp in **Native Only** (Nur nativ).

### JavaScript

1. Right-click the project, click **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**.

1. Change the debugger type drop down to **[!UICONTROL Native Only]**.

Das ist alles! Jetzt können Sie Analytics, Target und Zielgruppen-Management in Ihrer Anwendung für die universelle Windows-Plattform implementieren.

