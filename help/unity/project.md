---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Erstellen eines Projekts
solution: Experience Cloud
title: Erstellen eines Projekts
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 20%

---


# Erstellen eines Projekts{#building-your-project}

## iOS

Beim Erstellen für iOS wird ein Xcode-Projekt erstellt. Standardmäßig befinden sich die Dateien `ADBMobileWrapper.mm` und `AdobeMobileLibrary.a` Dateien in der Gruppe &quot;Bibliotheken&quot;Ihres neuen Projekts. Führen Sie zum Erstellen der App die folgenden manuellen Schritte aus:

1. Fügen Sie Ihre `ADBMobileConfig.json`-Datei zum Projekt hinzu.

   Stellen Sie sicher, dass es Mitglied des Builds ist, alle erforderlichen Zielgruppen.

1. Fügen Sie auf der Registerkarte &quot; **[!UICONTROL Build-Phasen]** &quot;Ihres Projekts einen Link zu den folgenden Bibliotheken hinzu:

   * `SystemConfiguration.framework`
(Diese Bibliothek ist möglicherweise bereits verknüpft.)

   * `libsqlite3.0.dylib`

>[!TIP]
>
>Um In-App-Nachrichten für lokale Benachrichtigungen aus dem SDK zu verwenden, müssen Sie in Ihrer ersten Unity-Szene `ADBMobile.EnableLocalNotifications();` die Beginn-Methode aufrufen.

## Android

Wenn Sie für Android erstellen, enthält die `apk` Datei die `ADBMobileConfig.json` Datei bereits am richtigen Speicherort. Standardmäßig wird auch die `AndroidManifest.xml` Datei in Ihrem `/Plugins/Android` Ordner verwendet.

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
