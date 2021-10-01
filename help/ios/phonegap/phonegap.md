---
description: Mit diesem Plug-in können Sie iOS-AppMeasurement-Aufrufe von Ihrem PhoneGap-Projekt ausführen.
keywords: phonegap
solution: Experience Cloud,Analytics
title: PhoneGap-Plug-in
topic-fix: Developer and implementation
uuid: f88bcf10-1f9e-4c97-b348-40db797c9923
exl-id: c20b2f85-b8d4-47c7-8177-106c7ddfe083
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 100%

---

# PhoneGap-Plug-in {#phonegap-plug-in}

Mit diesem Plug-in können Sie iOS-AppMeasurement-Aufrufe von Ihrem PhoneGap-Projekt ausführen.

## Neue Version des Adobe Experience Platform Mobile SDK

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDK für die Adobe Experience Platform? Klicken Sie [hier](https://aep-sdks.gitbook.io/docs/), um unsere aktuelle Dokumentation abzurufen.

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDKs können über [Experience Platform Launch](https://www.adobe.com/de/experience-platform/launch.html) konfiguriert werden.

* Beginnen Sie mit Adobe Experience Platform Launch.
* Gehen Sie zu [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK-Repositorys enthalten ist.


## PhoneGap-Projekt erstellen

Informationen zum Erstellen eines PhoneGap-Projekts finden Sie unter [PhoneGap](https://helpx.adobe.com/de/experience-manager/6-4/mobile/using/phonegap.html).

## Installieren des Plug-ins mit npm: {#section_43229E57C16944C0B51531CB92089189}

1. Führen Sie folgenden Befehl aus:

   ```
   cordova plugin add adobe-mobile-services
   ```

## Manuelles Installieren des Plug-ins  {#section_D53BA60D488C4DB8AD2BDF90439C180A}

### AppMeasurement-Bibliothek einschließen

So schließen Sie AppMeasurement ein:

1. Ziehen Sie `ADBMobile_PhoneGap.h` und `ADBMobile_PhoneGap.m` in den Ordner **[!UICONTROL Plug-ins]** in Ihrem Xcode-Projekt.
1. Nehmen Sie die folgenden Einstellungen vor:

   1. Wählen Sie **[!UICONTROL Elemente in den Zielgruppenordner kopieren (falls erforderlich)]**.
   1. Wählen Sie die Ziele aus, an denen der AppMeasurement-Code verwendet werden soll.

1. Ziehen Sie `ADB_Helper.js` in den Ordner `www` in Ihrem Projekt.
1. Öffnen Sie im Ordner `res/xml` die Datei `config.xml` und registrieren Sie ein neues Plug-in, indem Sie Folgendes hinzufügen:

   ```
   <feature name="ADBMobile_PhoneGap"> 
     <param name="ios-package" value="ADBMobile_PhoneGap" /> 
   </feature>
   ```

### App-Berechtigungen hinzufügen

Die AppMeasurement-Bibliothek erfordert Folgendes:

1. Starten Sie die XCode IDE und öffnen Sie die App.
1. Ziehen Sie den Ordner **[!UICONTROL Adobe Mobile]** in Ihr Xcode-Projekt und nehmen Sie die folgenden Einstellungen vor:

   1. Wählen Sie **[!UICONTROL Elemente in den Zielgruppenordner kopieren (falls erforderlich)]**.
   1. Wählen Sie **[!UICONTROL Gruppen für hinzugefügte Ordner erstellen]**.
   1. Wählen Sie die Ziele aus, an denen Sie den AppMeasurement-Code verwenden möchten, und klicken Sie auf **[!UICONTROL Fertigstellen]**.

   ![](assets/xcode-settings.png){Breite=„672“}

1. Erweitern Sie auf der Registerkarte **[!UICONTROL Build-Phasen]** des Ziels Ihres Projekts den Abschnitt **[!UICONTROL Binärdatei mit Bibliotheken verknüpfen]** und fügen Sie die folgenden Bibliotheken hinzu:

   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Bestätigen Sie, dass Ihre App ohne unerwartete Fehler erstellt wird.

## Benutzerdefinierte Verfolgung implementieren {#section_FD102B3CDAA4492FB04E56BF17E28663}

Fügen Sie in `html`-Dateien, in denen Sie die Verfolgung nutzen möchten, das Tag `<head>` ein:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```
