---
description: 'null'
seo-description: 'null'
seo-title: Schnellstart für Entwickler
solution: Experience Cloud,Analytics
title: Schnellstart für Entwickler
topic-fix: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
exl-id: dd3262b1-e211-4758-9b4a-9dc7c4920c10
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 3%

---

# Schnellstart für Entwickler {#developer-quick-start}

Sie benötigen Visual Studio 2013 oder höher, um das SDK zu implementieren.

## SDK abrufen   {#section_99FE1A17A36D4A2C943939023CF6265C}

Nachdem Sie den [SDK-Download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) entpackt haben, verfügen Sie über einen separaten Ordner für jede unterstützte Architektur- und Plattformkombination. Sie haben auch eine `ADBMobileConfig.json`-Datei, die weiter unten in diesem Handbuch beschrieben wird.

## Wählen Sie die richtige Version {#section_E53C5AA7D5474824A89BB32C003865A1}

Für jede Zielgruppe (Windows 8.1, Windows Phone 8.1) und für jede unterstützte  (x86, x64, ARM) werden verschiedene `.dll`/ `.winmd`-Dateien bereitgestellt. Die Dateien werden wie folgt in eine Ordnerstruktur aufgeteilt:

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>Die Version von `ADBMobile.winmd` spiegelt nicht die Version der Bibliothek wider. Die `.winmd`-Datei enthält nur Metadaten und hat als solche eine Versionsnummer von `255.255.255.255`, die nach Microsoft akzeptiert wird (siehe [Wie füge ich Assemblyinformationen für eine WinRT C++-/CX-Komponentendll hinzu?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). Um die Version der verwendeten Bibliothek zu überprüfen, überprüfen Sie die Version der zugrunde liegenden Datei `ADBMobile.dll`.

## Syntaxunterschiede {#section_A02DE120B6D240F5AFFE7509755C4F14}

Die Windows 8.1 Universal App Store-Bibliothek kann in verschiedenen Programmiersprachen verwendet werden. Die Beispiele in diesem Handbuch sind in WinJS (JavaScript) enthalten und müssen ggf. geändert werden, wenn Sie eine andere Sprache verwenden. Beachten Sie, dass bei Verwendung der winmd-Methoden von winJS (JavaScript) alle Methoden automatisch ihren ersten Buchstaben verkleinert haben.

Der Hauptunterschied zwischen den Implementierungen ist die für Kontextdaten verwendete Datenstruktur.

Verwenden Sie außerdem bei Verwendung des SDK in einem WinJS-Projekt eine leere Zeichenfolge ( `""` oder `''`) anstelle von `null` für leere Zeichenfolgenwerte.

## hinzufügen Sie die Bibliotheks- und Konfigurationsdatei in Ihr Projekt - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Starten Sie Visual Studio und öffnen Sie Ihre Projektmappe.
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **[!UICONTROL References]** und wählen Sie **[!UICONTROL Hinzufügen Reference]**.

1. Wählen Sie die richtige Version der Bibliothek aus und navigieren Sie zur zugehörigen `ADBMobile.winmd`-Datei.

   Weitere Informationen finden Sie im Abschnitt *Wählen Sie die richtige Version* aus.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Vergewissern Sie sich, dass `ADBMobile.winmd` im Fenster **[!UICONTROL Referenz-Manager]** ausgewählt ist, und klicken Sie auf **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Wenn Sie einer Windows Phone-App einen Verweis hinzufügen und `ADBMobile.winmd` auswählen, ändern Sie den Standarddateifilter von **[!UICONTROL Komponentendateien]** in **Alle Dateien**.

1. Klicken Sie im **[!UICONTROL Projektmappen-Explorer]** mit der rechten Maustaste auf **[!UICONTROL References]** und wählen Sie **[!UICONTROL Hinzufügen Reference]**.

   Überspringen Sie diesen Schritt, wenn Sie auch ein C++-Projekt in Ihrer Lösung haben.

1. Wählen Sie auf der linken Registerkarte **Windows** die Option **[!UICONTROL Erweiterungen]** und wählen Sie dann **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]** und fügen Sie es hinzu.

1. hinzufügen Sie die folgende Zeile zu Ihrer Klasse:

   ```
   using ADBMobile;
   ```

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Hinzufügen]** > **[!UICONTROL Vorhandenes Element]**.

1. Navigieren Sie zu Ihrer `ADBMobileConfig.json`-Datei und klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Klicken Sie mit der rechten Maustaste auf die Datei `ADBMobileConfig.json` in Ihrer Lösung und wählen Sie **[!UICONTROL Eigenschaften]**.

1. Ändern Sie **[!UICONTROL Aktion erstellen]** in **[!UICONTROL Inhalt]**.

## hinzufügen Sie die Bibliotheks- und Konfigurationsdatei in Ihr Projekt - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Starten Sie Visual Studio und öffnen Sie Ihre Projektmappe.
1. Klicken Sie im **[!UICONTROL Projektmappen-Explorer]** mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Hinzufügen]** > **[!UICONTROL Referenzen]**.

1. Wählen Sie die richtige Version der Bibliothek aus und fügen Sie der zugehörigen Datei `ADBMobile.winmd` einen Verweis hinzu.

   Weitere Informationen finden Sie im Abschnitt *Wählen Sie die korrekte Version* aus.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Überprüfen Sie im Fenster **[!UICONTROL Referenz-Manager]**, ob `ADBMobile.winmd` ausgewählt ist, und klicken Sie auf **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Wenn Sie einer Windows Phone-App einen Verweis hinzufügen und `ADBMobile.winmd` auswählen, ändern Sie den Standarddateifilter von **[!UICONTROL Komponentendateien]** in **Alle Dateien**.

1. hinzufügen Sie die folgende Zeile zu Ihrer Klasse:

   ```
   using namespace ADMS::Measurement;
   ```

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Hinzufügen]** > **[!UICONTROL Vorhandenes Element]**.

1. Navigieren Sie zur Datei `ADBMobileConfig.json` und klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Klicken Sie mit der rechten Maustaste auf die Datei `ADBMobileConfig.json` in Ihrer Lösung und wählen Sie **[!UICONTROL Eigenschaften]**.

1. Ändern Sie auf der Registerkarte **[!UICONTROL Allgemein]** **[!UICONTROL Inhalt]** in **[!UICONTROL Ja]** und klicken Sie auf **[!UICONTROL OK]**.

## hinzufügen Sie die Bibliotheks- und Konfigurationsdatei in Ihr Projekt - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Starten Sie Visual Studio und öffnen Sie Ihre Projektmappe.
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **[!UICONTROL References]** und wählen Sie **[!UICONTROL Hinzufügen Reference]**.

   Weitere Informationen finden Sie im Abschnitt *Wählen Sie die korrekte Version* aus.

1. Wählen Sie die richtige Version der Bibliothek aus und navigieren Sie dann zur zugehörigen Datei `ADBMobile.winmd`.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Vergewissern Sie sich, dass `ADBMobile.winmd` im Fenster **[!UICONTROL Referenz-Manager]** markiert ist, und klicken Sie auf **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Wenn Sie einer Windows Phone-App einen Verweis hinzufügen und `ADBMobile.winmd` auswählen, ändern Sie den Standarddateifilter von **[!UICONTROL Komponentendateien]** in **Alle Dateien**.

1. Klicken Sie im **[!UICONTROL Projektmappen-Explorer]** mit der rechten Maustaste auf **[!UICONTROL References]** und wählen Sie **[!UICONTROL Hinzufügen Reference]**.

   Überspringen Sie diesen Schritt, wenn Sie auch ein C++-Projekt in Ihrer Lösung haben.

1. Wählen Sie auf der linken Registerkarte **[!UICONTROL Windows]** **[!UICONTROL Erweiterungen]** und wählen Sie **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]** und fügen Sie es hinzu.

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Hinzufügen]** > **[!UICONTROL Vorhandenes Element]**.

1. Navigieren Sie zur Datei `ADBMobileConfig.json` und klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Klicken Sie mit der rechten Maustaste auf die Datei `ADBMobileConfig.json]` in Ihrer Lösung und wählen Sie **[!UICONTROL Eigenschaften]**.

1. Wenn **[!UICONTROL Dateieigenschaften]** ausgewählt ist, stellen Sie sicher, dass **[!UICONTROL Paketaktion]** auf **[!UICONTROL Inhalt]** eingestellt ist.

   Bei JavaScript-Projekten ist die Datei standardmäßig auf **[!UICONTROL Content]** eingestellt.

## ADBMobileConfig.json-Konfigurationsdatei {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE} aktualisieren

Die Datei `ADBMobileConfig.json` enthält globale SDK-Einstellungen und befindet sich im Projektstamm, nachdem Sie die Schritte im Abschnitt *Hinzufügen der Bibliotheks- und Konfigurationsdatei zu Ihrem Projekt* ausgeführt haben. Wenn Ihre `ADBMobileConfig.json`-Datei nicht von Adobe Mobile Services vorkonfiguriert wurde, müssen Sie zunächst einige Werte aktualisieren.

Das folgende Beispiel zeigt eine `ADBMobileConfig.json`-Datei:

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

* **Analytics**:  `rsids` und  `server`
* **Target**: `clientCode`
* **Zielgruppen-Management**: `server`

Weitere Informationen finden Sie unter [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md).

## Debugging von {#section_3A10376A60394A15BEE483323E0CD4AA}

Wenn Sie das Debugging für das SDK aktivieren möchten, müssen Sie `ADBMobile.Config.setDebugLogging(true);` aufrufen.

Für C Sharp- und JS-Apps müssen Sie das Debugging von nativem Code aktivieren, indem Sie die folgenden Schritte ausführen (das native Code-Debugging ist die Standardeinstellung für C++-Apps):

### C Scharf

Klicken Sie mit der rechten Maustaste auf das Projekt und wählen Sie **[!UICONTROL Eigenschaften]** > **[!UICONTROL Registerkarte Debuggen]**. Wählen Sie in der Dropdownliste Debugger **[!UICONTROL Nur nativ]**.

### JS

Klicken Sie mit der rechten Maustaste auf das Projekt und wählen Sie **[!UICONTROL Eigenschaften]** > **[!UICONTROL Konfigurationseigenschaften]** > **[!UICONTROL Registerkarte Debuggen]**. Ändern Sie die Dropdown-Liste für den Debugger-Typ in **Nur nativ**.

Das ist alles! Sie können jetzt Analytics, Zielgruppe und Audience-Management in Ihrer Windows 8.1 Universal App Store-App implementieren.
