---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Projekt erstellen
solution: Marketing Cloud, Entwickler
title: Projekt erstellen
uuid: 5550 a 394-6 f 3 f -4 b 87-b 840-89621 d 8 a 0 c 1 e
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Building your project{#building-your-project}

## iOS

Beim Aufbauen für iOS wird ein Xcode-Projekt erstellt. Standardmäßig befinden sich die Dateien `ADBMobileWrapper.mm` und `AdobeMobileLibrary.a` in der Gruppe „Bibliotheken“ des neuen Projekts. Führen Sie die folgenden manuellen Schritte zum Aufbauen der App aus:

1. Fügen Sie die Datei `ADBMobileConfig.json` in das Projekt ein.

   Diese Datei muss Mitglied aller erforderlichen Ziele im Build sein.

1. In the **[!UICONTROL Build Phases]** tab of your project, add a link to the following libraries:

   * `SystemConfiguration.framework`(Diese Bibliothek kann bereits verknüpft werden.)

   * `libsqlite3.0.dylib`

>[!TIP]
>
>To use Local Notification In-App messages from the SDK, you must call `ADBMobile.EnableLocalNotifications();` from the Start method in your first Unity Scene.

## Android

Beim Aufbau für Android enthält die `apk`-Datei bereits die Datei `ADBMobileConfig.json` an der richtigen Position. By default, the `AndroidManifest.xml` file in your `/Plugins/Android` folder is also used.

Falls eine benutzerdefinierte Manifestdatei verwendet werden soll, nehmen Sie die nachfolgenden Änderungen vor.

Berechtigungen hinzufügen für:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

Wenn Sie In-App-Nachrichten verwenden, fügen Sie die folgende Aktivität und den folgenden Empfänger hinzu:

```java
<activity android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" /> 
```

Wenn Sie Akquise verwenden, fügen Sie den folgenden Empfänger hinzu:

```java
<receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true"> 
   <intent-filter> 
      <action android:name="com.android.vending.INSTALL_REFERRER" /> 
   </intent-filter> 
</receiver>
```
