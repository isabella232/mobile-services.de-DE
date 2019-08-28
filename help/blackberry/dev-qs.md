---
title: Schnellstart für Entwickler
seo-title: Blackberry Developer Quick Start for Adobe Mobile Services
description: Im blackberry Developer Quick Start Guide erfahren Sie, wie Sie die blackberry-Bibliothek für Adobe Mobile Services implementieren.
seo-description: Im blackberry Developer Quick Start Guide erfahren Sie, wie Sie die blackberry-Bibliothek für Adobe Mobile Services implementieren.
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Schnellstart für Entwickler

Diese Information ist hilfreich, um den Implementierungsprozess der BlackBerry-Bibliothek zu verstehen.

## SDK abrufen

**Für das SDK ist BlackBerry 10 oder höher erforderlich.**

Nachdem Sie das heruntergeladene SDK entpackt haben, überprüfen Sie, ob die folgenden Dateien im Ordner `AdobeMobile` liegen:

* `Device-Coverage/libADBMobileShared.so`
* `Device-Debug/libADBMobileShared.so`
* `Device-Profile/libADBMobileShared.so`
* `Device-Release/libADBMobileShared.so`
* `public/ADBMediaAnalytics.hpp`
* `public/ADBMediaSharedHeader.hpp`
* `public/ADBMediaState.hpp`
* `public/ADBMobile.hpp`
* `Simulator-Coverage/libADBMobileShared.so`
* `Simulator-Debug/libADBMobileShared.so`
* `Simulator-Profile/libADBMobileShared.so`

## SDKs zu Ihrem Projekt hinzufügen

1. Right-click on your project and select **[!UICONTROL Configure]** &gt; **[!UICONTROL Add Library]**.
1. Select **[!UICONTROL External library]** and click **[!UICONTROL Next]**.
1. Klicken Sie neben dem Feld „**[!UICONTROL Gerätebibliothek]“ auf „****Durchsuchen[!UICONTROL “.]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. In the `Device-Debug` folder, select `libADBMobileShared.so` and click **[!UICONTROL Open]**.
1. Klicken Sie neben dem Feld „**[!UICONTROL Simulatorbibliothek]“ auf „****Durchsuchen[!UICONTROL “.]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. In the `Device-Debug` folder, select `libADBMobileShared.so` and click **[!UICONTROL Open]**.
1. Klicken Sie neben dem Feld „**[!UICONTROL Ordner einbinden]“ auf „****Hinzufügen[!UICONTROL “.]**
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. Fügen Sie den Ordner „`public`“ zu den eingebundenen Ordnern hinzu.
1. In the `ADBMobile-4.0.0BETA-BlackBerry` folder, there is a `.json` config file named `ADBMobileConfig.json`.

   Kopieren Sie diese Datei in das Stammverzeichnis Ihres Projekts.
1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt und wählen Sie „**[!UICONTROL Aktualisieren“ aus]**.

   The `.json` file should now be visible in your **[!UICONTROL Project Explorer]**.
1. Öffnen Sie die Datei „`bar-descriptor.xml`“ für Ihr Projekt.
1. Wählen Sie unten im Fenster die Registerkarte „**[!UICONTROL Assets]“ aus.**
1. Stellen Sie sicher, dass die Einstellung „**[!UICONTROL (Alle Konfigurationen)]**“ ausgewählt ist, und klicken Sie dann im Bereich „**[!UICONTROL Assets]“ des Fensters auf „** Dateien hinzufügen **“.**
   >[!TIP]
   >
   >In der QNX Momentics IDE gibt es einen Fehler, der manchmal verhindert, dass diese Schaltflächen sichtbar sind. Wenn die Schaltflächen nicht angezeigt werden, ändern Sie die Größe der Fenster, bis sie angezeigt werden.

1. Klicken **[!UICONTROL Sie auf Arbeitsbereich]**.
1. Find the `ADBMobileConfig.json` file in your project and click **[!UICONTROL OK]**.

Your application can import the classes/interfaces from the `adobeMobileLibrary.jar` library by using `#include <ADBMobile.hpp>`.

## App-Berechtigungen hinzufügen

In `bar-descriptor.xml` in the project directory, add the line `<permission>access_internet</permission>`, or in the QNX Momentics IDE, select the **[!UICONTROL Internet]** box on the permissions section of the **[!UICONTROL Application]** tab.

## `ADBMobileConfig.json` Konfigurationsdatei aktualisieren

Die Datei „`ADBMobileConfig.json`“ enthält globale SDK-Einstellungen. Sie müssen zunächst einige Werte aktualisieren, um loslegen zu können.

Im Folgenden finden Sie ein Beispiel für eine `ADBMobileConfig.json`-Datei:

```json
{
    "version" : "1.0",
    "analytics" : {
        "rsids" : "coolApp",
        "server" : "my.CoolApp.com",
        "charset" : "UTF-8",
        "ssl" : true,
        "offlineEnabled" : true,
        "lifecycleTimeout" : 5,
        "privacyDefault" : "optedin",
    }
}
```

You must at least update the `rsids` and `server` parameters. Weitere Informationen finden Sie unter [Adobe Mobile-Klassen- und Methodenreferenz](/help/blackberry/methods.md).

Sie können Analytics nun in Ihre BlackBerry 10-Anwendung implementieren.
