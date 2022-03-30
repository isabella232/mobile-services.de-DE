---
description: Informationen zur Implementierung der universellen Windows-Plattform-Bibliothek.
solution: Experience Cloud Services,Analytics
title: Schnellstart für Entwickler
topic-fix: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
exl-id: 28fc2a96-907e-41fc-a798-3e8d43fc7616
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 4%

---

# Schnellstart für Entwickler{#developer-quick-start}

Im Folgenden finden Sie einige Informationen zur Implementierung der universellen Windows-Plattform-Bibliothek.

>[!IMPORTANT]
>
>Zum Implementieren des SDK benötigen Sie Visual Studio 2013 oder höher.

## SDK abrufen   {#section_99FE1A17A36D4A2C943939023CF6265C}

Nachdem Sie die [SDK-Download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) -Datei, verfügen Sie für jede unterstützte Architektur und Plattformkombination über einen separaten Ordner. Sie haben auch eine `ADBMobileConfig.json` -Datei. Weitere Informationen zu dieser Datei finden Sie unter [Konfigurationsdatei &quot;ADBMobileConfig.json&quot;](/help/universal-windows/c-configuration/c.json.md).

## Auswählen der richtigen Version {#section_E53C5AA7D5474824A89BB32C003865A1}

Unterschiedlich `.dll/.winmd` -Dateien werden für jede unterstützte Architektur bereitgestellt (x86, x64, ARM).

>[!IMPORTANT]
>
>Die Version von `ADBMobile.winmd` spiegelt nicht die Version der Bibliothek wider. Die `.winmd` -Datei enthält nur Metadaten und hat eine Versionsnummer `255.255.255.255`, das gemäß Microsoft akzeptiert wird. Weitere Informationen finden Sie unter [Wie kann ich Assemblyinformationen für eine WinRT C++ / CX-Komponenten-DLL hinzufügen?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). Um die Version der verwendeten Bibliothek zu überprüfen, überprüfen Sie die Version der zugrunde liegenden `ADBMobile.dll` -Datei.

## Syntaxunterschiede {#section_A02DE120B6D240F5AFFE7509755C4F14}

Die universelle Windows-Plattform-Bibliothek kann in verschiedenen Programmiersprachen verwendet werden. Die Beispiele in diesem Handbuch beziehen sich auf WinJS (JavaScript). Wenn Sie eine andere Sprache verwenden, müssen Sie möglicherweise geändert werden. Wenn Sie winmd-Methoden von winJS verwenden, wird der erste Buchstabe automatisch in Kleinbuchstaben geschrieben.

Der Hauptunterschied zwischen den Implementierungen ist die Datenstruktur, die für Kontextdaten verwendet wird. Verwenden Sie außerdem bei Verwendung des SDK in einem WinJS-Projekt eine leere Zeichenfolge ( `""` oder `''`) anstelle von `null` für leere Zeichenfolgenwerte.

## Bibliothek und Konfigurationsdatei zu Ihrem Projekt hinzufügen - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Starten Sie Visual Studio und öffnen Sie die Projektmappe.
1. Im **[!UICONTROL Solution Explorer]**, Rechtsklick **[!UICONTROL Verweise]** und wählen Sie **[!UICONTROL Referenz hinzufügen]**.

1. Wählen Sie die richtige Version der Bibliothek aus und navigieren Sie zur zugehörigen Datei ADBMobile.winmd .

   Weitere Informationen finden Sie unter *Auswählen der richtigen Version* auf dieser Seite.

1. Klicken Sie auf **Hinzufügen**.

1. Überprüfen Sie, ob die Datei ADBMobile.winmd im **[!UICONTROL Referenz-Manager]** Fenster und klicken Sie auf **[!UICONTROL OK]**.

1. Im **[!UICONTROL Solution Explorer]**, Rechtsklick **[!UICONTROL Verweise]** und wählen Sie **[!UICONTROL Referenz hinzufügen]**.

   Wenn Ihre Lösung auch ein C++-Projekt enthält, überspringen Sie diesen Schritt.

1. Im **[!UICONTROL Windows]** auf der linken Seite, wählen Sie **[!UICONTROL Erweiterungen]**, auswählen und hinzufügen **[!UICONTROL Visual C++ 2015 Runtime für universelle Windows Platform-Apps]**.

1. Fügen Sie Ihrer Klasse die folgende Zeile hinzu:

   ```csharp
   using ADBMobile;
   ```

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt und klicken Sie auf **[!UICONTROL Hinzufügen]** > **[!UICONTROL Vorhandenes Element]**.

1. Navigieren Sie zum `ADBMobileConfig.json` Datei und klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Klicken Sie mit der rechten Maustaste auf die `ADBMobileConfig.json` Datei in Ihrer Lösung und wählen Sie **[!UICONTROL Eigenschaften]**.

1. Änderung **[!UICONTROL Aktion erstellen]** nach **[!UICONTROL Inhalt]**.

## Bibliothek und Konfigurationsdatei zu Ihrem Projekt hinzufügen - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Starten Sie Visual Studio und öffnen Sie die Projektmappe.
1. Im **[!UICONTROL Solution Explorer]**, klicken Sie mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Hinzufügen]** > **[!UICONTROL Verweise]**.

1. Wählen Sie die richtige Version der Bibliothek aus und fügen Sie der zugehörigen Datei ADBMobile.winmd einen Verweis hinzu.

   Weitere Informationen finden Sie unter *Auswählen der richtigen Version* auf dieser Seite.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Stellen Sie sicher, dass `ADBMobile.winmd` ist im **[!UICONTROL Referenz-Manager]** Fenster und klicken Sie auf **[!UICONTROL OK]**.

1. Fügen Sie Ihrer Klasse die folgende Zeile hinzu:

   ```c++
   using namespace ADBMobile;
   ```

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Hinzufügen]** > **[!UICONTROL Vorhandenes Element]**.

1. Navigieren Sie zu `ADBMobileConfig.json` Datei und klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Klicken Sie mit der rechten Maustaste auf die `ADBMobileConfig.json` Datei in Ihrer Lösung und wählen Sie **[!UICONTROL Eigenschaften]**.

1. Im **[!UICONTROL Allgemein]** Registerkarte, ändern **[!UICONTROL Inhalt]** nach **[!UICONTROL Ja]** und klicken Sie auf **[!UICONTROL OK]**.

## Bibliothek und Konfigurationsdatei zu Ihrem Projekt hinzufügen - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Starten Sie Visual Studio und öffnen Sie die Projektmappe.

1. Im **[!UICONTROL Solution Explorer]**, Rechtsklick **[!UICONTROL Verweise]** und wählen Sie **[!UICONTROL Referenz hinzufügen]**.

1. Wählen Sie die richtige Version der Bibliothek aus und navigieren Sie zur zugehörigen Datei ADBMobile.winmd .

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Überprüfen Sie, ob die Datei ADBMobile.winmd im **[!UICONTROL Referenz-Manager]** Fenster und klicken Sie auf **[!UICONTROL OK]**.

1. Im **[!UICONTROL Solution Explorer]**, Rechtsklick **[!UICONTROL Verweise]** und wählen Sie **[!UICONTROL Referenz hinzufügen]**.

   Wenn Ihre Lösung auch ein C++-Projekt enthält, überspringen Sie diesen Schritt.

1. Im **[!UICONTROL Windows]** auf der linken Seite, wählen Sie **[!UICONTROL Erweiterungen]** und wählen Sie aus und fügen Sie **[!UICONTROL Visual C++ 2015 Runtime für universelle Windows Platform-Apps]**.

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Hinzufügen]** > **[!UICONTROL Vorhandenes Element]**.

1. Navigieren Sie zum `ADBMobileConfig.json` Datei und klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Klicken Sie mit der rechten Maustaste auf die `ADBMobileConfig.json` Datei in Ihrer Lösung und wählen Sie **[!UICONTROL Eigenschaften]**.

1. Mit **[!UICONTROL Dateieigenschaften]** ausgewählt sein, stellen Sie sicher, **[!UICONTROL Paketaktion]** auf **[!UICONTROL Inhalt]**.

   Bei JavaScript-Projekten ist die Datei standardmäßig auf Inhalt eingestellt.

## ADBMobileConfig.json-Konfigurationsdatei aktualisieren {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

Die `ADBMobileConfig.json` enthält globale SDK-Einstellungen und befindet sich nach Abschluss der Schritte in *Bibliothek und Konfigurationsdatei zu Ihrem Projekt hinzufügen* Abschnitt. Wenn `ADBMobileConfig.json` -Datei nicht von Adobe Mobile Services vorkonfiguriert wurde, müssen Sie einige Werte aktualisieren, um zu beginnen.

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

Aktualisieren Sie mindestens die folgenden Werte für die von Ihnen verwendeten Lösungen:

* **Adobe Analytics**: `rsids` und `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

Weitere Informationen finden Sie unter [SDK-Methoden](/help/universal-windows/c-configuration/methods.md).

## Debugging {#section_3A10376A60394A15BEE483323E0CD4AA}

Rufen Sie auf, um das Debugging für das SDK zu aktivieren `ADBMobile.Config.setDebugLogging(true);`.

Für C Sharp- und JavaScript-Apps müssen Sie das Debugging von nativem Code aktivieren, indem Sie die folgenden Schritte ausführen (für C++-Apps ist das native Code-Debugging die Standardeinstellung):

### C Scharf

1. Klicken Sie mit der rechten Maustaste auf das Projekt und klicken Sie auf  **[!UICONTROL Eigenschaften]** > **[!UICONTROL Registerkarte &quot;Debuggen&quot;]**.

1. Ändern Sie die Dropdown-Liste des Debugger-Typs in **Nur native**.

### JavaScript

1. Klicken Sie mit der rechten Maustaste auf das Projekt und klicken Sie auf **[!UICONTROL Eigenschaften]** > **[!UICONTROL Konfigurationseigenschaften]** > **[!UICONTROL Registerkarte &quot;Debuggen&quot;]**.

1. Ändern Sie die Dropdown-Liste des Debugger-Typs in **[!UICONTROL Nur native]**.

Das ist alles! Sie können jetzt Analytics, Target und Zielgruppen-Management in Ihre universelle Windows-Plattform-App implementieren.
