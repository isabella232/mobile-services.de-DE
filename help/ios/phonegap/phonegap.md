---
description: Mit diesem Plug-in können Sie iOS-AppMeasurement-Aufrufe von Ihrem PhoneGap-Projekt ausführen.
keywords: phonegap
seo-description: Mit diesem Plug-in können Sie iOS-AppMeasurement-Aufrufe von Ihrem PhoneGap-Projekt ausführen.
seo-title: PhoneGap-Plug-in
solution: Marketing Cloud, Analytics
title: PhoneGap-Plug-in
topic: Entwickler und Implementierung
uuid: f 88 bcf 10-1 f 9 e -4 c 97-b 348-40 db 797 c 9923
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# PhoneGap plug-in{#phonegap-plug-in}

Mit diesem Plug-in können Sie iOS-AppMeasurement-Aufrufe von Ihrem PhoneGap-Projekt ausführen.

## Neue Adobe Experience Cloud SDK-Version

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDKs für die Adobe Experience Platform? Klicken Sie für die neueste Dokumentation [hier](https://aep-sdks.gitbook.io/docs/).

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDKs können über die [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) konfiguriert werden.

* Gehen Sie zu Launch, um zu beginnen.
* Gehen Sie zu [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK Repositorys enthalten ist.

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Weitere Informationen finden Sie unter [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).

To create a PhoneGap project, see [PhoneGap](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html).

## Installieren des Plug-ins mit npm: {#section_43229E57C16944C0B51531CB92089189}

1. Führen Sie folgenden Befehl aus:

   ```
   cordova plugin add adobe-mobile-services
   ```

## Manuelles Installieren des Plug-ins {#section_D53BA60D488C4DB8AD2BDF90439C180A}

### Appmeasurement-Bibliothek einschließen

So schließen Sie AppMeasurement ein:

1. Drag `ADBMobile_PhoneGap.h` and  `ADBMobile_PhoneGap.m` into the **[!UICONTROL Plugins]** folder in your Xcode project.
1. Nehmen Sie die folgenden Einstellungen vor:

   1. Wählen Sie **[!UICONTROL Elemente in den Zielgruppenordner kopieren (falls erforderlich)]**.
   1. Wählen Sie die Ziele aus, an denen der AppMeasurement-Code verwendet werden soll.

1. Drag `ADB_Helper.js` into the `www` folder in your project.
1. In the `res/xml` folder, open `config.xml` and register an new plugin by adding the following:

   ```
   <feature name="ADBMobile_PhoneGap"> 
     <param name="ios-package" value="ADBMobile_PhoneGap" /> 
   </feature>
   ```

### App-Berechtigungen hinzufügen

Für die AppMeasurement-Bibliothek ist Folgendes erforderlich:

1. Starten Sie die XCode IDE und öffnen Sie die App.
1. Ziehen Sie den Ordner **[!UICONTROL Adobe Mobile]in Ihr Xcode-Projekt und nehmen Sie die folgenden Einstellungen vor:**

   1. Wählen Sie **[!UICONTROL Elemente in den Zielgruppenordner kopieren (falls erforderlich)]**.
   1. Wählen Sie **[!UICONTROL Gruppen für hinzugefügte Ordner erstellen]**.
   1. Wählen Sie die Ziele aus, an denen Sie den AppMeasurement-Code verwenden möchten, und klicken Sie auf **[!UICONTROL Fertigstellen]**.
   ![](assets/xcode-settings.png){width = "672"}

1. Erweitern Sie auf der Registerkarte **[!UICONTROL Build-Phasen]** des Ziels Ihres Projekts den Abschnitt **Binärdatei mit Bibliotheken verknüpfen]und fügen Sie die folgenden Bibliotheken hinzu:[!UICONTROL **

   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Bestätigen Sie, dass Ihre App ohne unerwartete Fehler erstellt wird.

## Implement custom tracking {#section_FD102B3CDAA4492FB04E56BF17E28663}

In `html` files where you want to use tracking, add the following to the `<head>` tag:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

