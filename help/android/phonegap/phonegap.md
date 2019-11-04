---
description: Mit diesem Plug-in können Sie Android-AppMeasurement-Aufrufe von Ihrem PhoneGap-Projekt ausführen.
keywords: Android;Bibliothek;Mobile;SDK
seo-description: Mit diesem Plug-in können Sie Android-AppMeasurement-Aufrufe von Ihrem PhoneGap-Projekt ausführen.
seo-title: Übersicht über das PhoneGap-Plug-in
solution: Experience Cloud,Analytics
title: Übersicht über das PhoneGap-Plug-in
topic: Entwickler und Implementierung
uuid: c5c32357-d8df-458a-b0e8-e0c56040241d
translation-type: ht
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# Übersicht über das PhoneGap-Plug-in {#phonegap-plug-in}

Mit diesem Plug-in können Sie Android-AppMeasurement-Aufrufe von Ihrem PhoneGap-Projekt ausführen. Informationen zum Erstellen eines PhoneGap-Projekts finden Sie unter [PhoneGap](https://helpx.adobe.com/de/experience-manager/6-4/mobile/using/phonegap.html).

## Neue Version des Adobe Experience Platform Mobile SDK

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDK für die Adobe Experience Platform? Klicken Sie für die neueste Dokumentation [hier](https://aep-sdks.gitbook.io/docs/).

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDK können über [Experience Platform Launch](https://www.adobe.com/de/experience-platform/launch.html) konfiguriert werden.

* Beginnen Sie mit Adobe Experience Platform Launch.
* Gehen Sie zu [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK-Repositorys enthalten ist.


## Installieren des Plug-ins mit npm {#section_43229E57C16944C0B51531CB92089189}

Führen Sie folgenden Befehl aus:

```java
cordova plugin add adobe-mobile-services
```

## Manuelles Installieren des Plug-ins {#section_EA1FD59C484D44878AB509954DEE6037}

## Plug-in einschließen

1. Ziehen Sie die Datei `ADBMobile_PhoneGap.java` in Ihren `src`-Ordner.

   Um die Datei zu verschieben, klicken Sie auf **[!UICONTROL OK]**.

1. Ziehen Sie die Datei `ADB_Helper.js` in den Ordner, der die Datei `index.html` enthält.

   Um die Datei zu verschieben, klicken Sie auf **[!UICONTROL OK]**.

1. Öffnen Sie im `res/xml`-Ordner die Datei `config.xml` und registrieren Sie ein neues Plug-in, indem Sie Folgendes hinzufügen:

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

1. Informationen zum Herunterladen der AppMeasurement-Bibliothek finden Sie im Abschnitt [SDK abrufen](/help/android/getting-started/dev-qs.md).
1. Ziehen Sie die Datei `adobeMobileLibrary.jar` in Ihren `src`-Ordner.

   Um die Datei zu verschieben, klicken Sie auf **[!UICONTROL OK]**.

1. Klicken Sie mit der rechten Maustaste auf die Datei „adobeMobileLibrary.jar“ und wählen Sie **[!UICONTROL Als Bibliothek hinzufügen]** aus.
1. Geben Sie je nach Anforderungen Ihres Projekts den Namen, die Ebene und den Standort der Bibliothek ein.
1. Ziehen Sie die Datei `ADBMobileConfig.json` zum `assets`-Ordner im Stammverzeichnis der App.
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

## Benutzerdefinierte Verfolgung implementieren {#section_FD102B3CDAA4492FB04E56BF17E28663}

Fügen Sie in `html`-Dateien Folgendes zum `<head>`-Tag hinzu, den Sie für das Tracking verwenden möchten:

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

