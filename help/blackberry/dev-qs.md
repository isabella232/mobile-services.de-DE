---
title: Developer Quick Beginn
seo-title: BlackBerry Developer Quick Beginn zur Adobe von Mobile Services
description: Die BlackBerry Developer Quick Beginn-Anleitung hilft Ihnen, den Vorgang zur Implementierung der BlackBerry-Bibliothek für Adobe Mobile Services zu verstehen.
seo-description: Die BlackBerry Developer Quick Beginn-Anleitung hilft Ihnen, den Vorgang zur Implementierung der BlackBerry-Bibliothek für Adobe Mobile Services zu verstehen.
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 5%

---


# Schnellstart für Entwickler

Diese Informationen helfen Ihnen, den Vorgang zur Implementierung der BlackBerry-Bibliothek zu verstehen.

## SDK abrufen  

**Das SDK erfordert BlackBerry 10 oder höher.**

Nachdem Sie das heruntergeladene SDK entpackt haben, überprüfen Sie, ob die folgenden Dateien in einem `AdobeMobile` Ordner vorhanden sind:

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

## SDKs in Ihr Projekt Hinzufügen

1. Klicken Sie mit der rechten Maustaste auf das Projekt und wählen Sie **[!UICONTROL Konfigurieren]** > **[!UICONTROL Hinzufügen Bibliothek]**.
1. Wählen Sie **[!UICONTROL Externe Bibliothek]** und klicken Sie auf **[!UICONTROL Weiter]**.
1. Klicken Sie auf **[!UICONTROL Durchsuchen]** neben dem Feld **[!UICONTROL Gerätebibliothek]** .
1. Navigieren Sie zum Ordner `ADBMobile-4.0.0BETA-BlackBerry`. 
1. Wählen Sie im `Device-Debug` Ordner die Option `libADBMobileShared.so` und klicken Sie auf **[!UICONTROL Öffnen]**.
1. Klicken Sie auf **[!UICONTROL Durchsuchen]** neben dem Feld **[!UICONTROL Simulator-Bibliothek]** .
1. Navigieren Sie zum Ordner `ADBMobile-4.0.0BETA-BlackBerry`. 
1. Wählen Sie im `Device-Debug` Ordner die Option `libADBMobileShared.so` und klicken Sie auf **[!UICONTROL Öffnen]**.
1. Klicken Sie auf **[!UICONTROL Hinzufügen]** neben dem Feld **[!UICONTROL Einschließen von Ordnern]** .
1. Navigieren Sie zum Ordner `ADBMobile-4.0.0BETA-BlackBerry`. 
1. hinzufügen Sie den `public` Ordner mit Ihren Inhalten.
1. Im `ADBMobile-4.0.0BETA-BlackBerry` Ordner befindet sich eine `.json` Konfigurationsdatei mit dem Namen `ADBMobileConfig.json`.

   Kopieren Sie diese Datei in den Stammordner Ihres Projekts.
1. Klicken Sie mit der rechten Maustaste auf das Projekt und wählen Sie **[!UICONTROL Aktualisieren]**.

   Die `.json` Datei sollte jetzt in Ihrem **[!UICONTROL ProjektExplorer]** sichtbar sein.
1. Öffnen Sie die `bar-descriptor.xml` Datei für Ihr Projekt.
1. Wählen Sie unten im Fenster die Registerkarte &quot; **[!UICONTROL Assets]** &quot;aus.
1. Vergewissern Sie sich, dass **[!UICONTROL (Alle Konfigurationen)]** ausgewählt ist, und klicken Sie dann auf die **[!UICONTROL Hinzufügen Dateien]** im Abschnitt &quot; **[!UICONTROL Assets]** &quot;des Fensters.
   >[!TIP]
   >
   >Es gibt einen Fehler in der QNX Momentics-IDE, der manchmal verhindert, dass diese Schaltflächen sichtbar sind. Wenn Sie die Schaltflächen nicht sehen können, passen Sie die Größe der Fenster an, bis sie angezeigt werden.

1. Klicken Sie auf **[!UICONTROL Arbeitsbereich]**.
1. Suchen Sie die `ADBMobileConfig.json` Datei im Projekt und klicken Sie auf **[!UICONTROL OK]**.

Ihre Anwendung kann die Klassen/Schnittstellen aus der `adobeMobileLibrary.jar` Bibliothek importieren, indem sie `#include <ADBMobile.hpp>`.

## App-Berechtigungen hinzufügen

Fügen Sie `bar-descriptor.xml` im Projektverzeichnis die Zeile hinzu `<permission>access_internet</permission>`oder wählen Sie in der QNX Momentics IDE das Feld **[!UICONTROL Internet]** im Abschnitt &quot;Berechtigungen&quot;der Registerkarte &quot; **[!UICONTROL Anwendung]** &quot;aus.

## Aktualisieren der `ADBMobileConfig.json` Konfigurationsdatei

Die `ADBMobileConfig.json` Datei enthält globale SDK-Einstellungen. Sie müssen zunächst einige Werte aktualisieren.

The following is an example of an `ADBMobileConfig.json` file:

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

Sie müssen mindestens die Parameter `rsids` und `server` aktualisieren. Weitere Informationen finden Sie unter [Adobe Mobile-Klassen- und Methodenreferenz](/help/blackberry/methods.md).

Sie können Analytics jetzt in Ihrer BlackBerry 10-App implementieren.
