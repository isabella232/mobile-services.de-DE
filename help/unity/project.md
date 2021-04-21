---
description: Erstellen von iOS-Projekten
keywords: Unity
solution: Experience Cloud
title: Erstellen eines Projekts
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
exl-id: 9da99392-b34e-4e36-b255-f3787e26015c
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 18%

---

# Erstellen eines Projekts{#building-your-project}

## iOS

Beim Erstellen für iOS wird ein Xcode-Projekt erstellt. Standardmäßig befinden sich die Dateien `ADBMobileWrapper.mm` und `AdobeMobileLibrary.a` in der Gruppe &quot;Bibliotheken&quot;Ihres neuen Projekts. Führen Sie zum Erstellen der App die folgenden manuellen Schritte aus:

1. Fügen Sie Ihre `ADBMobileConfig.json`-Datei zum Projekt hinzu.

   Stellen Sie sicher, dass es Mitglied des Builds ist, alle erforderlichen Zielgruppen.

1. Fügen Sie auf der Registerkarte **[!UICONTROL Build Phases]** Ihres Projekts einen Link zu den folgenden Bibliotheken hinzu:

   * `SystemConfiguration.framework`
(Diese Bibliothek ist möglicherweise bereits verknüpft.)

   * `libsqlite3.0.dylib`

>[!TIP]
>
>Um In-App-Nachrichten für lokale Benachrichtigungen aus dem SDK zu verwenden, müssen Sie `ADBMobile.EnableLocalNotifications();` aus der Beginn-Methode in Ihrer ersten Unity-Szene aufrufen.

## Android

Wenn Sie für Android erstellen, enthält die Datei `apk` bereits die Datei `ADBMobileConfig.json` am richtigen Speicherort. Standardmäßig wird auch die Datei `AndroidManifest.xml` im Ordner `/Plugins/Android` verwendet.

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
