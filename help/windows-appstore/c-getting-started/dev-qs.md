---
description: Schnellstartartikel für Entwickler
solution: Experience Cloud Services,Analytics
title: Schnellstart für Entwickler
topic-fix: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
exl-id: dd3262b1-e211-4758-9b4a-9dc7c4920c10
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 2%

---

# Schnellstart für Entwickler {#developer-quick-start}

Sie benötigen Visual Studio 2013 oder höher, um das SDK zu implementieren.

## SDK abrufen   {#section_99FE1A17A36D4A2C943939023CF6265C}

Nachdem Sie die [SDK-Download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases), verfügen Sie über einen separaten Ordner für jede unterstützte Architektur und Plattformkombination. Sie haben auch eine `ADBMobileConfig.json` -Datei, die weiter unten in diesem Handbuch erläutert wird.

## Auswählen der richtigen Version {#section_E53C5AA7D5474824A89BB32C003865A1}

Unterschiedlich `.dll`/ `.winmd` -Dateien werden für jede Zielplattform (Windows 8.1, Windows Phone 8.1) und unterstützte Architektur (x86, x64, ARM) bereitgestellt. Die Dateien werden wie folgt in eine Ordnerstruktur unterteilt:

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>Die Version von `ADBMobile.winmd` spiegelt nicht die Version der Bibliothek wider. Die `.winmd` -Datei enthält nur Metadaten und weist daher eine Versionsnummer von `255.255.255.255` das nach Microsoft akzeptiert wird (siehe [Wie kann ich Assemblyinformationen für eine WinRT C++ / CX-Komponenten-DLL hinzufügen?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). Um die Version der verwendeten Bibliothek zu überprüfen, überprüfen Sie die Version der zugrunde liegenden `ADBMobile.dll` -Datei.

## Syntaxunterschiede {#section_A02DE120B6D240F5AFFE7509755C4F14}

Die Windows 8.1 Universal App Store-Bibliothek kann in mehreren Programmiersprachen verwendet werden. Die Beispiele in diesem Handbuch beziehen sich auf WinJS (JavaScript) und müssen ggf. geändert werden, wenn Sie eine andere Sprache verwenden. Beachten Sie, dass bei der Verwendung von winmd-Methoden aus winJS (JavaScript) alle Methoden automatisch ihren ersten Buchstaben kleingeschrieben haben.

Der Hauptunterschied zwischen den Implementierungen ist die Datenstruktur, die für Kontextdaten verwendet wird.

Verwenden Sie außerdem bei Verwendung des SDK in einem WinJS-Projekt eine leere Zeichenfolge ( `""` oder `''`) anstelle von `null` für leere Zeichenfolgenwerte.

## Bibliothek und Konfigurationsdatei zu Ihrem Projekt hinzufügen - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Starten Sie Visual Studio und öffnen Sie die Projektmappe.
1. Im **Solution Explorer**, Rechtsklick **[!UICONTROL Verweise]** und wählen Sie **[!UICONTROL Referenz hinzufügen]**.

1. Wählen Sie die richtige Version der Bibliothek aus und navigieren Sie zur zugehörigen `ADBMobile.winmd` -Datei.

   Weitere Informationen finden Sie unter *Auswählen der richtigen Version* unten.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Stellen Sie sicher, dass `ADBMobile.winmd` wird im **[!UICONTROL Referenz-Manager]** Fenster und klicken Sie auf **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Wenn Sie eine Referenz zu einer Windows Phone-App hinzufügen, wählen Sie `ADBMobile.winmd`ändern Sie den Standarddateifilter von **[!UICONTROL Komponentendateien]** nach **Alle Dateien**.

1. Im **[!UICONTROL Solution Explorer]**, Rechtsklick **[!UICONTROL Verweise]** und wählen Sie **[!UICONTROL Referenz hinzufügen]**.

   Überspringen Sie diesen Schritt, wenn Ihre Lösung auch ein C++-Projekt enthält.

1. Im **Windows** auf der linken Seite, wählen Sie **[!UICONTROL Erweiterungen]**, dann auswählen und hinzufügen **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**.

1. Fügen Sie Ihrer Klasse die folgende Zeile hinzu:

   ```
   using ADBMobile;
   ```

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Hinzufügen]** > **[!UICONTROL Vorhandenes Element]**.

1. Navigieren Sie zu Ihrer `ADBMobileConfig.json` Datei und klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Klicken Sie mit der rechten Maustaste auf die `ADBMobileConfig.json` Datei in Ihrer Lösung und wählen Sie **[!UICONTROL Eigenschaften]**.

1. Änderung **[!UICONTROL Aktion erstellen]** nach **[!UICONTROL Inhalt]**.

## Bibliothek und Konfigurationsdatei zu Ihrem Projekt hinzufügen - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Starten Sie Visual Studio und öffnen Sie die Projektmappe.
1. Im **[!UICONTROL Solution Explorer]**, klicken Sie mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Hinzufügen]** > **[!UICONTROL Verweise]**.

1. Wählen Sie die richtige Version der Bibliothek aus und fügen Sie dann einen Verweis zur zugehörigen `ADBMobile.winmd` -Datei.

   Weitere Informationen finden Sie unter *Auswählen der richtigen Version* unten.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Im **[!UICONTROL Referenz-Manager]** überprüfen Sie, ob `ADBMobile.winmd` ausgewählt ist und auf **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Wenn Sie eine Referenz zu einer Windows Phone-App hinzufügen, wählen Sie `ADBMobile.winmd`ändern Sie den Standarddateifilter von **[!UICONTROL Komponentendateien]** nach **Alle Dateien**.

1. Fügen Sie Ihrer Klasse die folgende Zeile hinzu:

   ```
   using namespace ADMS::Measurement;
   ```

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Hinzufügen]** > **[!UICONTROL Vorhandenes Element]**.

1. Navigieren Sie zum `ADBMobileConfig.json` Datei und klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Klicken Sie mit der rechten Maustaste auf die `ADBMobileConfig.json` Datei in Ihrer Lösung und wählen Sie **[!UICONTROL Eigenschaften]**.

1. Im **[!UICONTROL Allgemein]** Registerkarte, ändern **[!UICONTROL Inhalt]** nach **[!UICONTROL Ja]** und klicken Sie auf **[!UICONTROL OK]**.

## Bibliothek und Konfigurationsdatei zu Ihrem Projekt hinzufügen - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Starten Sie Visual Studio und öffnen Sie die Projektmappe.
1. Im **Solution Explorer**, Rechtsklick **[!UICONTROL Verweise]** und wählen Sie **[!UICONTROL Referenz hinzufügen]**.

   Weitere Informationen finden Sie unter *Auswählen der richtigen Version* unten.

1. Wählen Sie die richtige Version der Bibliothek aus und navigieren Sie dann zur zugehörigen `ADBMobile.winmd` -Datei.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Stellen Sie sicher, dass `ADBMobile.winmd` ist im **[!UICONTROL Referenz-Manager]** Fenster und klicken Sie auf **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Wenn Sie eine Referenz zu einer Windows Phone-App hinzufügen, wählen Sie `ADBMobile.winmd`ändern Sie den Standarddateifilter von **[!UICONTROL Komponentendateien]** nach **Alle Dateien**.

1. Im **[!UICONTROL Solution Explorer]**, Rechtsklick **[!UICONTROL Verweise]** und wählen Sie **[!UICONTROL Referenz hinzufügen]**.

   Überspringen Sie diesen Schritt, wenn Ihre Lösung auch ein C++-Projekt enthält.

1. Im **[!UICONTROL Windows]** auf der linken Seite, wählen Sie **[!UICONTROL Erweiterungen]** und wählen Sie aus und fügen Sie **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**.

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Hinzufügen]** > **[!UICONTROL Vorhandenes Element]**.

1. Navigieren Sie zum `ADBMobileConfig.json` Datei und klicken Sie auf **[!UICONTROL Hinzufügen]**.

1. Klicken Sie mit der rechten Maustaste auf die `ADBMobileConfig.json]` Datei in Ihrer Lösung und wählen Sie **[!UICONTROL Eigenschaften]**.

1. Mit **[!UICONTROL Dateieigenschaften]** ausgewählt sein, stellen Sie sicher, **[!UICONTROL Paketaktion]** auf **[!UICONTROL Inhalt]**.

   Bei JavaScript-Projekten ist die Datei auf **[!UICONTROL Inhalt]** Standardmäßig.

## ADBMobileConfig.json-Konfigurationsdatei aktualisieren {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

Die `ADBMobileConfig.json` -Datei enthält globale SDK-Einstellungen und befindet sich nach Abschluss der Schritte im *Bibliothek und Konfigurationsdatei zu Ihrem Projekt hinzufügen* Abschnitt. Wenn `ADBMobileConfig.json` -Datei nicht von Adobe Mobile Services vorkonfiguriert wurde, müssen Sie einige Werte aktualisieren, um zu beginnen.

Im Folgenden finden Sie ein Beispiel für eine `ADBMobileConfig.json` Datei:

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

Wenn Sie das Debugging für das SDK aktivieren möchten, müssen Sie `ADBMobile.Config.setDebugLogging(true);`.

Für C Sharp- und JS-Apps müssen Sie das Debugging von nativem Code aktivieren, indem Sie die folgenden Schritte ausführen (für C++-Apps ist das native Code-Debugging die Standardeinstellung):

### C Scharf

Klicken Sie mit der rechten Maustaste auf das Projekt und wählen Sie **[!UICONTROL Eigenschaften]** > **[!UICONTROL Registerkarte &quot;Debuggen&quot;]**. Wählen Sie in der Debugger-Dropdown-Liste **[!UICONTROL Nur native]**.

### JS

Klicken Sie mit der rechten Maustaste auf das Projekt und wählen Sie  **[!UICONTROL Eigenschaften]** > **[!UICONTROL Konfigurationseigenschaften]** > **[!UICONTROL Registerkarte &quot;Debuggen&quot;]**. Ändern Sie die Dropdown-Liste des Debugger-Typs in **Nur native**.

Das ist alles! Sie können jetzt Analytics, Target und Zielgruppen-Management in Ihre Windows 8.1 Universal App Store-App implementieren.
