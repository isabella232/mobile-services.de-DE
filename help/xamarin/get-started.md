---
description: In diesem Thema werden die ersten Schritte zur Nutzung von Xamarin-Komponenten für das Mobile-Lösungen-4.x-SDK beschrieben.
keywords: Xamarin
seo-description: In diesem Thema werden die ersten Schritte zur Nutzung von Xamarin-Komponenten für das Mobile-Lösungen-4.x-SDK beschrieben.
seo-title: Xamarin components for Experience Cloud Solutions 4.x SDK
solution: Marketing Cloud, Entwickler
title: Xamarin-Komponenten für Experience Cloud-Lösungen 4.x-SDK
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Xamarin components for Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

In diesem Thema werden die ersten Schritte zur Nutzung von Xamarin-Komponenten für das Mobile-Lösungen-4.x-SDK beschrieben.

Letzte Aktualisierung: **10. Januar 2019**

## Erste Schritte {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>Adobe Mobile SDK ist nicht mehr im Xamarin Components Store oder in der Get Gallery verfügbar. Um die Xamarin-Komponenten herunterzuladen, gehen Sie zu [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services).


## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

Importieren Sie die ADBMobile-Komponente in Ihr Xamarin.Android-Projekt:

1. Xamarin-Projekt öffnen

1. Open **[!UICONTROL References]** dialog and click the **[!UICONTROL .Net Assembly]** tab.

1. Wählen Sie `ADBMobile.XamarinAndroidBinding.dll` aus dem Ordner **[!UICONTROL lib/Android]** .

1. Add your `ADBMobileConfig.json` file to the **[!UICONTROL Assets]** folder of your project.

1. Berechtigungen hinzufügen für:

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`
   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. Wenn Sie In-App-Nachrichten verwenden, fügen Sie die folgende Aktivität und den folgenden Empfänger hinzu:

   ```java
   <activity 
   android:name="com.adobe.mobile.MessageFullScreenActivity" 
   android:theme="@android:style/Theme.Translucent.NoTitleBar" />
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. Wenn Sie Akquise verwenden, fügen Sie den folgenden Empfänger hinzu:

   ```java
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
   <intent-filter>
       <action android:name="com.android.vending.INSTALL_REFERRER" />
   </intent-filter>
   </receiver>
   ```

## iOS {#section_1531928DDE904D769B3987BF927D0E02}

Import the ADBMobile Component to your Xamarin.iOS project:

1. Öffnen Sie Ihr Xamarin-Projekt.
1. Open **[!UICONTROL References]** dialog and click the **[!UICONTROL .Net Assembly]** tab.

1. Wählen Sie `ADBMobile.XamarinIOSBinding.dll` aus dem Ordner **[!UICONTROL lib/ios-unified]** .

1. Fügen Sie die Datei `ADBMobileConfig.json` in das Projekt ein.


