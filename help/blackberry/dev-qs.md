---
title: Schnellstart für Entwickler
description: Die Kurzanleitung für BlackBerry-Entwickler hilft Ihnen, den Prozess zur Implementierung der BlackBerry-Bibliothek für Adobe Mobile Services zu verstehen.
exl-id: 65f39667-541a-4bbd-af9b-823638aa6f42
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 6%

---

# Schnellstart für Entwickler

Diese Informationen helfen Ihnen dabei, den Prozess zur Implementierung der BlackBerry-Bibliothek zu verstehen.

## SDK abrufen  

**Für das SDK ist BlackBerry 10 oder höher erforderlich.**

Überprüfen Sie nach dem Entpacken des heruntergeladenen SDK, ob die folgenden Dateien in einem Ordner `AdobeMobile` vorhanden sind:

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

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Konfigurieren]** > **[!UICONTROL Bibliothek hinzufügen]**.
1. Wählen Sie **[!UICONTROL Externe Bibliothek]** und klicken Sie auf **[!UICONTROL Weiter]**.
1. Klicken Sie auf **[!UICONTROL Browse]** neben dem Feld **[!UICONTROL Gerätebibliothek]** .
1. Navigieren Sie zum Ordner `ADBMobile-4.0.0BETA-BlackBerry`. 
1. Wählen Sie im Ordner `Device-Debug` die Option `libADBMobileShared.so` aus und klicken Sie auf **[!UICONTROL Öffnen Sie]**.
1. Klicken Sie auf **[!UICONTROL Browse]** neben dem Feld **[!UICONTROL Simulator library]** .
1. Navigieren Sie zum Ordner `ADBMobile-4.0.0BETA-BlackBerry`. 
1. Wählen Sie im Ordner `Device-Debug` die Option `libADBMobileShared.so` aus und klicken Sie auf **[!UICONTROL Öffnen Sie]**.
1. Klicken Sie neben dem Feld **[!UICONTROL Ordner einschließen]** auf **[!UICONTROL Hinzufügen]** .
1. Navigieren Sie zum Ordner `ADBMobile-4.0.0BETA-BlackBerry`. 
1. Fügen Sie den Ordner `public` zu Ihren Includes hinzu.
1. Im Ordner `ADBMobile-4.0.0BETA-BlackBerry` befindet sich eine `.json` Konfigurationsdatei mit dem Namen `ADBMobileConfig.json`.

   Kopieren Sie diese Datei in den Stammordner Ihres Projekts.
1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt und wählen Sie **[!UICONTROL Aktualisieren]** aus.

   Die Datei `.json` sollte jetzt im **[!UICONTROL Projekt-Explorer]** sichtbar sein.
1. Öffnen Sie die Datei `bar-descriptor.xml` für Ihr Projekt.
1. Wählen Sie unten im Fenster die Registerkarte **[!UICONTROL Assets]** aus.
1. Vergewissern Sie sich, dass **[!UICONTROL (Alle Konfigurationen)]** ausgewählt ist, und klicken Sie dann im Abschnitt **[!UICONTROL Assets]** auf **[!UICONTROL Dateien hinzufügen]** .
   >[!TIP]
   >
   >Es gibt einen Fehler in der QNX Momentics IDE, der manchmal verhindert, dass diese Schaltflächen sichtbar sind. Wenn Sie die Schaltflächen nicht sehen können, ändern Sie die Fenstergröße, bis sie angezeigt werden.

1. Klicken Sie auf **[!UICONTROL Workspace]**.
1. Suchen Sie die Datei `ADBMobileConfig.json` in Ihrem Projekt und klicken Sie auf **[!UICONTROL OK]**.

Ihre Anwendung kann die Klassen/Schnittstellen aus der `adobeMobileLibrary.jar`-Bibliothek mithilfe von `#include <ADBMobile.hpp>` importieren.

## App-Berechtigungen hinzufügen

Fügen Sie in `bar-descriptor.xml` im Projektverzeichnis die Zeile `<permission>access_internet</permission>` hinzu oder wählen Sie in der QNX Momentics IDE das Feld **[!UICONTROL Internet]** im Berechtigungsabschnitt der Registerkarte **[!UICONTROL Application]** aus.

## Aktualisieren der Konfigurationsdatei `ADBMobileConfig.json`

Die Datei `ADBMobileConfig.json` enthält globale SDK-Einstellungen. Sie müssen einige Werte aktualisieren, um zu beginnen.

Im Folgenden finden Sie ein Beispiel für eine `ADBMobileConfig.json` -Datei:

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

Sie müssen mindestens die Parameter `rsids` und `server` aktualisieren. Weitere Informationen finden Sie unter [Adobe Mobile-Klasse und Methodenreferenz](/help/blackberry/methods.md).

Sie können Analytics jetzt in Ihrer BlackBerry 10-App implementieren.
