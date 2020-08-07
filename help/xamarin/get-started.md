---
description: In diesem Thema werden die ersten Schritte mit der Verwendung von Xamarin-Komponenten für das Mobile Solutions 4.x SDK beschrieben.
keywords: Xamarin
seo-description: In diesem Thema werden die ersten Schritte mit der Verwendung von Xamarin-Komponenten für das Mobile Solutions 4.x SDK beschrieben.
seo-title: Xamarin-Komponenten für Experience Cloud Solutions 4.x-SDK
solution: Marketing Cloud,Developer
title: Xamarin-Komponenten für Experience Cloud Solutions 4.x-SDK
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 5%

---


# Xamarin components for Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

In diesem Thema werden die ersten Schritte mit der Verwendung von Xamarin-Komponenten für das Mobile Solutions 4.x SDK beschrieben.

Last Updated: **January 10, 2019**

## Erste Schritte {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>Adobe Mobile SDK ist nicht mehr im Xamarin Components Store oder in der NuGet Gallery verfügbar. Um die Xamarin-Komponenten herunterzuladen, gehen Sie zu [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services).

## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

Importieren Sie die ADBMobile-Komponente in Ihr Xamarin.Android-Projekt:

1. Xamarin-Projekt öffnen
1. Öffnen Sie das Dialogfeld **[!UICONTROL Referenzen]** und klicken Sie auf die Registerkarte **[!UICONTROL .Net Assembly]** .
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

1. If you are using acquisition, add the following receiver :

   ```java
    <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
    <intent-filter>
        <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
    </receiver>
   ```

## iOS {#section_1531928DDE904D769B3987BF927D0E02}

Importieren Sie die ADBMobile-Komponente in Ihr Xamarin.iOS-Projekt:

1. Öffnen Sie Ihr Xamarin-Projekt.
1. Öffnen Sie das Dialogfeld **[!UICONTROL Referenzen]** und klicken Sie auf die Registerkarte **[!UICONTROL .Net Assembly]** .
1. Select `ADBMobile.XamarinIOSBinding.dll` from the **[!UICONTROL lib/ios-unified]** folder.
1. Add your `ADBMobileConfig.json` file to the project.
