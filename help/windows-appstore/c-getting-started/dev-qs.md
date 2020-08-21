---
description: 'null'
seo-description: 'null'
seo-title: Developer Quick Beginn
solution: Marketing Cloud,Analytics
title: Developer Quick Beginn
topic: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 2%

---


# Developer Quick Beginn {#developer-quick-start}

Sie benötigen Visual Studio 2013 oder höher, um das SDK zu implementieren.

## SDK abrufen   {#section_99FE1A17A36D4A2C943939023CF6265C}

Nachdem Sie den [SDK-Download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)entpackt haben, verfügen Sie für jede unterstützte Architektur- und Plattformkombination über einen separaten Ordner. Sie haben auch eine `ADBMobileConfig.json` Datei, die weiter unten in diesem Handbuch beschrieben wird.

## Wählen Sie die richtige Version {#section_E53C5AA7D5474824A89BB32C003865A1}

Für jede Zielgruppe (Windows 8.1, Windows Phone 8.1) und für jede unterstützte  (x86, x64, ARM) stehen verschiedene `.dll`/ `.winmd` -dateien zur Verfügung. Die Dateien werden wie folgt in eine Ordnerstruktur aufgeteilt:

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>Die Version von `ADBMobile.winmd` spiegelt nicht die Version der Bibliothek wider. Die `.winmd` Datei enthält nur Metadaten und hat als solche eine Versionsnummer, `255.255.255.255` die nach Microsoft akzeptiert wird (siehe [Wie füge ich Assemblyinformationen für eine WinRT C++/CX-Komponente dll hinzu?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). Um die Version der verwendeten Bibliothek zu überprüfen, überprüfen Sie die Version der zugrunde liegenden `ADBMobile.dll` Datei.

## Syntaxunterschiede {#section_A02DE120B6D240F5AFFE7509755C4F14}

Die Windows 8.1 Universal App Store-Bibliothek kann in verschiedenen Programmiersprachen verwendet werden. Die Beispiele in diesem Handbuch sind in WinJS (JavaScript) enthalten und müssen ggf. geändert werden, wenn Sie eine andere Sprache verwenden. Beachten Sie, dass bei Verwendung der winmd-Methoden von winJS (JavaScript) alle Methoden automatisch ihren ersten Buchstaben verkleinert haben.

Der Hauptunterschied zwischen den Implementierungen ist die für Kontextdaten verwendete Datenstruktur.

Verwenden Sie außerdem bei Verwendung des SDK in einem WinJS-Projekt eine leere Zeichenfolge ( `""` oder `''`) anstelle `null` von Werten für leere Zeichenfolgen.

## Bibliothek und Konfigurationsdatei in Ihr Projekt Hinzufügen - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Starten Sie Visual Studio und öffnen Sie Ihre Projektmappe.
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **[!UICONTROL Referenzen]** und wählen Sie **[!UIUCONTROL Hinzufügen Referenz]**.

1. Wählen Sie die richtige Version der Bibliothek aus und navigieren Sie zur entsprechenden `ADBMobile.winmd` Datei.

   Weitere Informationen finden Sie im Abschnitt zur *Auswahl der richtigen Version* .

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Vergewissern Sie sich, dass im Fenster `ADBMobile.winmd` Referenz-Manager **[!UICONTROL die Option ausgewählt ist, und klicken Sie auf]** OK ****.

   >[!NOTE]
   >
   >Wenn Sie einer Windows Phone-App eine Referenz hinzufügen, ändern Sie zur Auswahl `ADBMobile.winmd`den Standarddateifilter von **[!UICONTROL Komponentendateien]** in **Alle Dateien**.

1. Klicken Sie im **[!UICONTROL Projektmappen-Explorer]** mit der rechten Maustaste auf **[!UICONTROL Referenzen]** und wählen Sie **[!UICONTROL Hinzufügen Referenz]**.

   Überspringen Sie diesen Schritt, wenn Sie auch ein C++-Projekt in Ihrer Lösung haben.

1. Wählen Sie auf der linken Registerkarte &quot; **Windows** &quot;die Option &quot; **[!UICONTROL Erweiterungen]**&quot;und wählen Sie dann **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]** aus und fügen Sie es hinzu.

1. hinzufügen Sie die folgende Zeile zu Ihrer Klasse:

   ```
   using ADBMobile;
   ```

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Hinzufügen]** > **[!UICONTROL Vorhandenes Element]**.

1. Navigieren Sie zu Ihrer `ADBMobileConfig.json` Datei und klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Klicken Sie mit der rechten Maustaste auf die `ADBMobileConfig.json` Datei in Ihrer Lösung und wählen Sie **[!UICONTROL Eigenschaften]**.

1. Ändern Sie die Aktion **[!UICONTROL Erstellen]** in **[!UICONTROL Inhalt]**.

## Add the library and config file to your project - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Starten Sie Visual Studio und öffnen Sie Ihre Projektmappe.
1. Klicken Sie im **[!UICONTROL Projektmappen-Explorer]** mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Hinzufügen]** > **[!UICONTROL Referenzen]**.

1. Wählen Sie die richtige Version der Bibliothek aus und fügen Sie der zugehörigen `ADBMobile.winmd` Datei einen Verweis hinzu.

   Weitere Informationen finden Sie im Abschnitt zur *Auswahl der richtigen Version* .

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Überprüfen Sie im Fenster **[!UICONTROL Referenz-Manager]** , ob die Option ausgewählt `ADBMobile.winmd` ist, und klicken Sie auf **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Wenn Sie einer Windows Phone-App eine Referenz hinzufügen, ändern Sie zur Auswahl `ADBMobile.winmd`den Standarddateifilter von **[!UICONTROL Komponentendateien]** in **Alle Dateien**.

1. hinzufügen Sie die folgende Zeile zu Ihrer Klasse:

   ```
   using namespace ADMS::Measurement;
   ```

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Hinzufügen]** > **[!UICONTROL Vorhandenes Element]**.

1. Navigieren Sie zur `ADBMobileConfig.json` Datei und klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Klicken Sie mit der rechten Maustaste auf die `ADBMobileConfig.json` Datei in Ihrer Lösung und wählen Sie **[!UICONTROL Eigenschaften]**.

1. Ändern Sie auf der Registerkarte &quot; **[!UICONTROL Allgemein]** &quot;den Eintrag &quot; **[!UICONTROL Inhalt]** &quot;in &quot; **[!UICONTROL Ja]**&quot;und klicken Sie auf **[!UICONTROL &quot;OK&quot;]**.

## Add the library and config file to your project - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Starten Sie Visual Studio und öffnen Sie Ihre Projektmappe.
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **[!UICONTROL Referenzen]** und wählen Sie **[!UICONTROL Hinzufügen Referenz]**.

   Weitere Informationen finden Sie im Abschnitt zur *Auswahl der richtigen Version* .

1. Wählen Sie die richtige Version der Bibliothek aus und navigieren Sie dann zur entsprechenden `ADBMobile.winmd` Datei.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Überprüfen Sie, ob diese Option im Fenster `ADBMobile.winmd` Referenz-Manager **[!UICONTROL aktiviert ist, und klicken Sie auf]** OK ****.

   >[!TIP]
   >
   >Wenn Sie einer Windows Phone-App eine Referenz hinzufügen, ändern Sie zur Auswahl `ADBMobile.winmd`den Standarddateifilter von **[!UICONTROL Komponentendateien]** in **Alle Dateien**.

1. Klicken Sie im **[!UICONTROL Projektmappen-Explorer]** mit der rechten Maustaste auf **[!UICONTROL Referenzen]** und wählen Sie **[!UICONTROL Hinzufügen Referenz]**.

   Überspringen Sie diesen Schritt, wenn Sie auch ein C++-Projekt in Ihrer Lösung haben.

1. Wählen Sie auf der linken Registerkarte &quot; **[!UICONTROL Windows]** &quot;die Option &quot; **[!UICONTROL Erweiterungen]** &quot;und wählen Sie **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]** aus und fügen Sie es hinzu.

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Hinzufügen]** > **[!UICONTROL Vorhandenes Element]**.

1. Navigieren Sie zur `ADBMobileConfig.json` Datei und klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Klicken Sie mit der rechten Maustaste auf die `ADBMobileConfig.json]` Datei in Ihrer Lösung und wählen Sie **[!UICONTROL Eigenschaften]**.

1. Stellen Sie bei aktivierten **[!UICONTROL Dateieigenschaften]** sicher, dass **[!UICONTROL für die Paketaktion]** der **[!UICONTROL Inhalt]** festgelegt ist.

   Bei JavaScript-Projekten ist die Datei standardmäßig auf **[!UICONTROL Inhalt]** eingestellt.

## ADBMobileConfig.json-Konfigurationsdatei aktualisieren {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

Die `ADBMobileConfig.json` Datei enthält globale SDK-Einstellungen und befindet sich im Projektstamm, nachdem Sie die Schritte im Abschnitt *Hinzufügen Bibliotheks- und Konfigurationsdatei zu Ihrem Projekt* ausgeführt haben. Wenn Ihre `ADBMobileConfig.json` Datei nicht von Adobe Mobile Services vorkonfiguriert wurde, müssen Sie zunächst einige Werte aktualisieren.

The following is an example of an `ADBMobileConfig.json` file:

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

Aktualisieren Sie mindestens die folgenden Werte für die von Ihnen verwendeten Lösungen:

* **Analytics**: `rsids` und `server`
* **Target**: `clientCode`
* **Zielgruppen-Management**: `server`

Weitere Informationen finden Sie unter [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md).

## Debugging {#section_3A10376A60394A15BEE483323E0CD4AA}

Wenn Sie das Debugging für das SDK aktivieren möchten, müssen Sie aufrufen `ADBMobile.Config.setDebugLogging(true);`.

Für C Sharp- und JS-Apps müssen Sie das Debugging von nativem Code aktivieren, indem Sie die folgenden Schritte ausführen (das native Code-Debugging ist die Standardeinstellung für C++-Apps):

### C Scharf

Klicken Sie mit der rechten Maustaste auf das Projekt und wählen Sie **[!UICONTROL Eigenschaften]** > Registerkarte **[!UICONTROL Debuggen]**. Wählen Sie in der Dropdownliste Debugger die Option **[!UICONTROL Nur]** nativ.

### JS

Klicken Sie mit der rechten Maustaste auf das Projekt und wählen Sie **[!UICONTROL Eigenschaften]** > **[!UICONTROL Konfigurationseigenschaften]** > Registerkarte **[!UICONTROL Debuggen]**. Ändern Sie die Dropdown-Liste &quot;Debugger-Typ&quot;in &quot; **Nur** nativ&quot;.

Das ist alles! Sie können jetzt Analytics, Zielgruppe und Audience-Management in Ihrer Windows 8.1 Universal App Store-App implementieren.
