---
description: Erstellen von iOS-Projekten
keywords: Unity
solution: Experience Cloud Services
title: Erstellen eines Projekts
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
exl-id: 9da99392-b34e-4e36-b255-f3787e26015c
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 18%

---

# Erstellen eines Projekts{#building-your-project}

## iOS

Beim Erstellen für iOS wird ein Xcode-Projekt erstellt. Standardmäßig wird die `ADBMobileWrapper.mm` und  `AdobeMobileLibrary.a` -Dateien befinden sich in der Gruppe &quot;Bibliotheken&quot;Ihres neuen Projekts. Führen Sie die folgenden manuellen Schritte aus, die zum Erstellen Ihrer App erforderlich sind:

1. Fügen Sie Ihre `ADBMobileConfig.json`-Datei zum Projekt hinzu.

   Stellen Sie sicher, dass es Mitglied des Builds ist, alle erforderlichen Ziele zu erstellen.

1. Im **[!UICONTROL Build-Phasen]** Fügen Sie in Ihrem Projekt einen Link zu den folgenden Bibliotheken hinzu:

   * `SystemConfiguration.framework`
(Diese Bibliothek ist möglicherweise bereits verknüpft.)

   * `libsqlite3.0.dylib`

>[!TIP]
>
>Um In-App-Nachrichten mit lokalen Benachrichtigungen aus dem SDK zu verwenden, müssen Sie `ADBMobile.EnableLocalNotifications();` aus der Start -Methode in Ihrer ersten Unity-Szene.

## Android

Wenn Sie für Android erstellen, wird die `apk` -Datei enthält bereits `ADBMobileConfig.json` an der richtigen Stelle. Standardmäßig wird die `AndroidManifest.xml` in der Datei `/Plugins/Android` -Ordner verwendet wird.

Wenn Sie Ihre eigene benutzerdefinierte Manifestdatei verwenden müssen, sollten die folgenden Änderungen hinzugefügt werden.

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
