---
description: 'null'
seo-description: 'null'
seo-title: Developer quick start
solution: Marketing Cloud,Analytics
title: Schnellstart für Entwickler
topic: Entwickler und Implementierung
uuid: b368959b-d985-436e-8b3e-97e355a97951
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Developer quick start {#developer-quick-start}

Sie benötigen Visual Studio 2013 oder höher, um das SDK zu implementieren.

## SDK abrufen {#section_99FE1A17A36D4A2C943939023CF6265C}

Wenn Sie das heruntergeladene [SDK](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) extrahieren, wird ein eigener Ordner für jede Kombination aus unterstützter Architektur und Plattform angelegt. Außerdem verfügen Sie über die Datei `ADBMobileConfig.json`, die später in diesem Handbuch erläutert wird.

## Select the correct version {#section_E53C5AA7D5474824A89BB32C003865A1}

Different `.dll`/ `.winmd` files are provided for each target platform (Windows 8.1, Windows Phone 8.1), and supported architecture (x86, x64, ARM). Die Dateien werden wie folgt in eine Ordnerstruktur unterteilt:

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>The version of `ADBMobile.winmd` does not reflect the version of the library. The `.winmd` file contains metadata only, and as such will have a version number of `255.255.255.255` which is accepted behavior according to Microsoft (see [How do I add assembly information for a WinRT C++ / CX component dll?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). To check the version of the library you are using, check the version of the underlying `ADBMobile.dll` file.

## Syntax differences {#section_A02DE120B6D240F5AFFE7509755C4F14}

Die Windows 8.1 Universal App Store-Bibliothek kann in verschiedenen Programmiersprachen verwendet werden. Die Beispiele in diesem Handbuch beziehen sich auf WinJS (JavaScript) und müssen bei Verwendung einer anderen Sprache gegebenenfalls angepasst werden. Beachten Sie, dass der erste Buchstabe von winmd-Methoden aus winJS (JavaScript) automatisch kleingeschrieben wird.

Der Hauptunterschied zwischen den verschiedenen Implementierungen besteht in der für die Kontextdaten verwendeten Datenstruktur.

Additionally, when using the SDK in a WinJS project, use an empty string ( `""` or `''`) instead of `null` for empty string values.

## Add the library and config file to your project - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Starten Sie Visual Studio und öffnen Sie Ihre Lösung.
1. In the **Solution Explorer**, right-click **[!UICONTROL References]** and select **[!UIUCONTROL Add Reference]**.

1. Select the correct version of the library and browse to the associated `ADBMobile.winmd` file.

   Weitere Informationen finden Sie im Abschnitt zur *Auswahl der richtigen Version* .

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Verify that `ADBMobile.winmd` is selected in the **[!UICONTROL Reference Manager]** window and click **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Wenn Sie einer Windows Phone-App einen Verweis hinzufügen, ändern Sie zur Auswahl den Standarddateifilter von `ADBMobile.winmd`**Komponentendateienin** Alle Dateien ****.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Überspringen Sie diesen Schritt, wenn Sie auch ein C++-Projekt in Ihrer Lösung haben.

1. Wählen Sie auf der linken Registerkarte " **Windows** "die Option " **[!UICONTROL Erweiterungen]**"und wählen Sie dann **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]** aus und fügen Sie es hinzu.

1. Fügen Sie Ihrer Klasse die folgende Zeile hinzu:

   ```
   using ADBMobile;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Navigieren Sie zu Ihrer `ADBMobileConfig.json` Datei und klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. Change **[!UICONTROL Build Action]** to **[!UICONTROL Content]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Starten Sie Visual Studio und öffnen Sie Ihre Lösung.
1. In the **[!UICONTROL Solution Explorer]**, right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL References]**.

1. Select the correct version of the library and then add a reference to the associated `ADBMobile.winmd` file.

   Weitere Informationen finden Sie im Abschnitt zur *Auswahl der richtigen Version* .

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Überprüfen Sie im Fenster " **[!UICONTROL Referenz-Manager]** "die Auswahl `ADBMobile.winmd` und klicken Sie auf **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Wenn Sie einer Windows Phone-App einen Verweis hinzufügen, ändern Sie zur Auswahl den Standarddateifilter von `ADBMobile.winmd`**Komponentendateienin** Alle Dateien ****.

1. Fügen Sie Ihrer Klasse die folgende Zeile hinzu:

   ```
   using namespace ADMS::Measurement;
   ```

1. Right-click you your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json` file in your solution and select **[!UICONTROL Properties]**.

1. On the **[!UICONTROL General]** tab, change **[!UICONTROL Content]** to **[!UICONTROL Yes]**, and click **[!UICONTROL OK]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Starten Sie Visual Studio und öffnen Sie Ihre Lösung.
1. In the **Solution Explorer**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference**.

   Weitere Informationen finden Sie im Abschnitt zur *Auswahl der richtigen Version* .

1. Select the correct version of the library and then browse to the associated `ADBMobile.winmd` file.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Vergewissern Sie sich, dass `ADBMobile.winmd` im Fenster **Reference Manager (Referenz-Manager)** markiert ist, und klicken Sie auf **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Wenn Sie einer Windows Phone-App einen Verweis hinzufügen, ändern Sie zur Auswahl den Standarddateifilter von `ADBMobile.winmd`**Komponentendateienin** Alle Dateien ****.

1. In the **[!UICONTROL Solution Explorer]**, right-click **[!UICONTROL References]** and select **[!UICONTROL Add Reference]**.

   Überspringen Sie diesen Schritt, wenn Sie auch ein C++-Projekt in Ihrer Lösung haben.

1. Wählen Sie auf der linken Registerkarte " **[!UICONTROL Windows]** "die Option " **[!UICONTROL Erweiterungen]** "und wählen Sie **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]** aus und fügen Sie es hinzu.

1. Right-click your project and select **[!UICONTROL Add]** &gt; **[!UICONTROL Existing Item]**.

1. Browse to the `ADBMobileConfig.json` file and click **[!UICONTROL Add]**.

1. Right-click the `ADBMobileConfig.json]` file in your solution and select **[!UICONTROL Properties]**.

1. Stellen Sie bei aktivierten **[!UICONTROL Dateieigenschaften]** sicher, dass **[!UICONTROL für die Paketaktion]** der **[!UICONTROL Inhalt]** festgelegt ist.

   Bei JavaScript-Projekten ist die Datei standardmäßig auf **[!UICONTROL Inhalt]** eingestellt.

## Update the ADBMobileConfig.json config file {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

The `ADBMobileConfig.json` file contains global SDK settings, and is located at your project root after you complete the steps in the *Add the Library and Config File to your Project* section. If your `ADBMobileConfig.json` file was not pre-configured by Adobe Mobile Services, you need to update a few values to get started.

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

* **Analytics**: `rsids` und `server`
* **Target**: `clientCode`
* **Zielgruppen-Management**: `server`

For more details, see [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md).

## Debugging {#section_3A10376A60394A15BEE483323E0CD4AA}

Wenn Sie Debugging für das SDK aktivieren möchten, müssen Sie `ADBMobile.Config.setDebugLogging(true);` ); aufrufen.

Für C Sharp- und JS-Apps müssen Sie das Debugging von nativem Code aktivieren, indem Sie die folgenden Schritte ausführen (das native Code-Debugging ist die Standardeinstellung für C++-Apps):

### C Scharf

Right-click the project, select **[!UICONTROL Properties]** &gt; **[!UICONTROL Debug tab]**. Wählen Sie in der Dropdownliste Debugger die Option **[!UICONTROL Nur]** nativ.

### JS

Right-click the project, select  **[!UICONTROL Properties]** &gt; **[!UICONTROL Configuration Properties]** &gt; **[!UICONTROL Debug tab]**. Ändern Sie das Dropdown für den Debuggertyp in **Native Only** (Nur nativ).

Das ist alles! Sie können jetzt Analytics, Target und Zielgruppen-Management in Ihrer Windows 8.1 Universal App Store-App implementieren.
