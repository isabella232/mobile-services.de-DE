---
description: 'null'
seo-description: 'null'
seo-title: Schnellstart für Entwickler
solution: Marketing Cloud, Analytics
title: Schnellstart für Entwickler
topic: Entwickler und Implementierung
uuid: 11 c 06 fcf-d 5 e 4-4858-9 a 4 e -3 bf 66 cdd 2 a 48
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start{#developer-quick-start}

Im Folgenden finden Sie einige Informationen zur Implementierung der Universal Windows Platform Library.

>[!IMPORTANT]
>
>Um das SDK zu implementieren, benötigen Sie Visual Studio 2013 oder höher.

## SDK abrufen {#section_99FE1A17A36D4A2C943939023CF6265C}

After you unzip the [SDK download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) file, you will have a separate folder for each supported architecture and platform combination. Sie haben auch eine `ADBMobileConfig.json` Datei. Weitere Informationen zu dieser Datei finden Sie unter [adbmobileconfig. json-Konfigurationsdatei](/help/universal-windows/c-configuration/c.json.md).

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll/.winmd` files are provided for each supported architecture (x86, x64, ARM).

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. Die `.winmd` Datei enthält nur Metadaten und enthält eine Versionsnummer, `255.255.255.255`die gemäß Microsoft akzeptiert wird. Weitere Informationen finden Sie unter [Wie füge ich Assemblierungsinformationen für eine winrt C + +/CX-Komponente hinzu?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## Unterschiede in der Syntax {#section_A02DE120B6D240F5AFFE7509755C4F14}

Die Bibliothek für die universelle Windows-Plattform kann in mehreren Programmiersprachen verwendet werden. Die Beispiele in diesem Handbuch sind in winjs (javascript) enthalten, wenn Sie eine andere Sprache verwenden, müssen sie möglicherweise geändert werden. Wenn Sie Winmd-Methoden aus winjs verbrauchen, haben alle Methoden automatisch ihren ersten Buchstaben.

Der Hauptunterschied zwischen den verschiedenen Implementierungen besteht in der für die Kontextdaten verwendeten Datenstruktur. Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config File to your project - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Starten Sie Visual Studio und öffnen Sie Ihre Lösung.
1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

1. Wählen Sie die richtige Version der Bibliothek aus und navigieren Sie zur zugehörigen adbmobile. winmd-Datei.

   Weitere Informationen finden Sie unter *Auswählen des richtigen* Versionsabschnitts auf dieser Seite.

1. Klicken Sie auf **Hinzufügen**.

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Wenn Sie in Ihrer Lösung auch über ein C + +-Projekt verfügen, überspringen Sie diesen Schritt.

1. Wählen Sie auf der **[!UICONTROL linken Seite der Registerkarte "Windows]** «die Option **[!UICONTROL " Erweiterungen]**" , wählen Sie " **[!UICONTROL Visual C + + 2015 Runtime for Universal Windows Platform Apps]**«.

1. Fügen Sie Ihrer Klasse die folgende Zeile hinzu:

   ```csharp
   using ADBMobile;
   ```

1. Right-click your project and click **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Klicken Sie mit der rechten Maustaste auf die `ADBMobileConfig.json` Datei in Ihrer Lösung und wählen **[!UICONTROL Sie Eigenschaften]**.

1. **[!UICONTROL Build-Aktion]** in **[!UICONTROL Inhalt ändern]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Starten Sie Visual Studio und öffnen Sie Ihre Lösung.
1. In the **[!UICONTROL Solution Explorer]**, right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL References]**.

1. Wählen Sie die richtige Version der Bibliothek aus und fügen Sie der zugeordneten adbmobile. winmd-Datei einen Verweis hinzu.

   Weitere Informationen finden Sie unter *Auswählen des richtigen* Versionsabschnitts auf dieser Seite.

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

1. Wählen Sie die richtige Version der Bibliothek aus und navigieren Sie zur zugehörigen adbmobile. winmd-Datei.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Verify that the ADBMobile.winmd file is checked in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Wenn Sie in Ihrer Lösung auch über ein C + +-Projekt verfügen, überspringen Sie diesen Schritt.

1. Wählen Sie auf der **[!UICONTROL linken Registerkarte auf]** der linken Seite **[!UICONTROL Erweiterungen]** aus und wählen Sie **[!UICONTROL Visual C + + 2015 Runtime for Universal Windows Platform Apps]**.

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. Stellen Sie **[!UICONTROL sicher, dass die]** **[!UICONTROL Option "Paketaktion"]** auf **[!UICONTROL " Inhalt"]** festgelegt ist.

   Bei javascript-Projekten ist die Datei standardmäßig auf "Inhalt" festgelegt.

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

Aktualisieren Sie mindestens die folgenden Werte für die Lösungen, die Sie verwenden:

* **Adobe Analytics**: `rsids` und `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

Weitere Informationen finden Sie unter [SDK-Methoden](/help/universal-windows/c-configuration/methods.md).

## Debugging {#section_3A10376A60394A15BEE483323E0CD4AA}

Um das Debugging für das SDK zu aktivieren, rufen `ADBMobile.Config.setDebugLogging(true);`Sie die Seite auf.

Für C Sharp- und javascript-Apps müssen Sie das Debugging nativer Code aktivieren, indem Sie die folgenden Schritte ausführen (das native Debugging von Code ist die Standardeinstellung für C + +-Apps):

### C Sharp

1. Klicken Sie mit der rechten Maustaste auf das Projekt und klicken Sie auf **[!UICONTROL Eigenschaften]** &gt; **[!UICONTROL Debug-Registerkarte]**.

1. Ändern Sie das Dropdown für den Debuggertyp in **Native Only** (Nur nativ).

### JavaScript

1. Right-click the project, click **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**.

1. Change the debugger type drop down to **[!UICONTROL Native Only]**.

Das ist alles! Jetzt können Sie Analytics, Target und Zielgruppen-Management in Ihrer Anwendung für die universelle Windows-Plattform implementieren.

