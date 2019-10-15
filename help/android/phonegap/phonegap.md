---
description: Mit diesem Plug-in können Sie Android-AppMeasurement-Aufrufe von Ihrem PhoneGap-Projekt ausführen.
keywords: android;library;mobile;sdk
seo-description: Mit diesem Plug-in können Sie Android-AppMeasurement-Aufrufe von Ihrem PhoneGap-Projekt ausführen.
seo-title: Überblick über das PhoneGap-Plug-in
solution: Marketing Cloud,Analytics
title: Überblick über das PhoneGap-Plug-in
topic: Entwickler und Implementierung
uuid: c5c32357-d8df-458a-b0e8-e0c56040241d
translation-type: tm+mt
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# Überblick über das PhoneGap-Plug-in {#phonegap-plug-in}

Mit diesem Plug-in können Sie Android-AppMeasurement-Aufrufe von Ihrem PhoneGap-Projekt ausführen. To create a PhoneGap project, see [PhoneGap](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html).

## Neue Version des Adobe Experience Platform Mobile SDK

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDKs für die Adobe Experience Platform? Klicken Sie für die neueste Dokumentation [hier](https://aep-sdks.gitbook.io/docs/).

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDKs können über die [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) konfiguriert werden.

* Beginnen Sie mit Adobe Experience Platform Launch.
* Gehen Sie zu [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK Repositorys enthalten ist.


## Installieren des Plug-ins mit npm {#section_43229E57C16944C0B51531CB92089189}

Führen Sie folgenden Befehl aus:

```java
cordova plugin add adobe-mobile-services
```

## Manuelles Installieren des Plug-ins {#section_EA1FD59C484D44878AB509954DEE6037}

## Plug-in einschließen

1. Ziehen Sie die `ADBMobile_PhoneGap.java` Datei in Ihren `src` Ordner.

   Um die Datei zu verschieben, klicken Sie auf **[!UICONTROL OK]**.

1. Ziehen Sie die `ADB_Helper.js` Datei in den Ordner, der die `index.html` Datei enthält

   Um die Datei zu verschieben, klicken Sie auf **[!UICONTROL OK]**.

1. In the `res/xml` folder, open the `config.xml` file and register an new plugin by adding the following:

   ```xml
   <feature name="ADBMobile_PhoneGap"> 
     <param name="android-package" value="[YOUR_PACKAGE_NAME].ADBMobile_PhoneGap" /> 
   </feature>
   ```

   Wenn Ihr Paket beispielsweise `com.example.phonegaptest` heißt, lautet der Wert `android-package` wie folgt:

   ```xml
   <param name="android-package" value="com.example.phonegaptest.ADBMobile_PhoneGap" />
   ```

## AppMeasurement-Bibliothek einschließen

1. To download the AppMeasurement library, see [Get the SDK](/help/android/getting-started/dev-qs.md).
1. Ziehen Sie die `adobeMobileLibrary.jar` Datei in Ihren `src` Ordner.

   Um die Datei zu verschieben, klicken Sie auf **[!UICONTROL OK]**.

1. Right-click the `adobeMobileLibrary.jar file and select **[!UICONTROL Add as Library]**.
1. Geben Sie je nach Anforderungen Ihres Projekts den Namen, die Ebene und den Standort der Bibliothek ein.
1. Drag the `ADBMobileConfig.json` file to your `assets` folder in the application root.
1. Bestätigen Sie, dass Sie die Stammanwendung und **nicht** eine Anwendung in einer Anwendung ausgewählt haben.

   Um die Datei zu verschieben, klicken Sie auf **[!UICONTROL OK]**.

## App-Berechtigungen hinzufügen

Die AppMeasurement-Bibliothek erfordert folgende Berechtigungen, um Daten zu senden und Offline-Verfolgungsaufrufe aufzuzeichnen:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

Ergänzen Sie die Datei `AndroidManifest.xml` im Projektverzeichnis der Anwendung um die folgenden Zeilen, um diese Berechtigungen hinzuzufügen:

```xml
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

So aktivieren Sie In-App-Nachrichten:

Aktualisieren Sie AndroidManifest.xml, um die Vollbildaktivität zu deklarieren und den Nachrichten-Handler zu aktivieren:

```java
<activity  
android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

Wenn Sie beim Erstellen einer Nachricht in Adobe Mobile Services das modale Layout gewählt haben, wählen Sie eines der folgenden Designs aus:

* `Theme.Translucent.NoTitleBar.Fullscreen`
* `Theme.Translucent.NoTitleBar`
* `Theme.Translucent`

Beispiel:

```java
<activity 
android:name="com.adobe.mobile.MessageFullScreenActivity" 
android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" 
android:windowSoftInputMode="adjustUnspecified|stateHidden" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

## Implement custom tracking {#section_FD102B3CDAA4492FB04E56BF17E28663}

In `html` files, add the following to the `<head>` tag where you want to use tracking:

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

