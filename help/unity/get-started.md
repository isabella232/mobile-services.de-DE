---
description: Mit diesem Plugin senden Sie Adobe Analytics-Aufrufe aus Ihren Unity-Anwendungen heraus.
keywords: Unity
seo-description: Mit diesem Plugin senden Sie Adobe Analytics-Aufrufe aus Ihren Unity-Anwendungen heraus.
seo-title: Unity Plug-in für die iOS- und Android 4.x-SDKs
solution: Marketing Cloud,Developer
title: Unity Plug-in für die iOS- und Android 4.x-SDKs
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
translation-type: tm+mt
source-git-commit: 5fbba02eb61679344f638b6465e47b0d9ae5a988

---


# Unity Plug-in für die iOS- und Android 4.x-SDKs {#unity-plug-in-for-the-ios-and-android-x-sdks}

Mit diesem Plugin senden Sie Adobe Analytics-Aufrufe aus Ihren Unity-Anwendungen heraus.

Zuletzt aktualisiert am: **20. Oktober 2016**

## Erste Schritte {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

Laden Sie die Datei [ADBMobile.unitypackage](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) von GitHub oder Developer Connection herunter.

Im Folgenden finden Sie den Inhalt der `ADBMobile.unitypackage` Datei:

* Assets (Stammverzeichnis)

   * ADBMobile

      * Demo

         * ADBMobileDemo.cs
         * BooDemo.boo
         * BooScene.unity
         * CSharpScene.unity
         * JavaScriptDemo.js
         * JavaScriptScene.unity
         * SecondScene.unity
         * SecondSceneScript.cs
   * Plug-ins

      * ADBMobile.cs
      * Android

         * adobeMobileLibrary-{version}.jar
         * AndroidManifest.xml
         * assets

            * ADBMobileConfig.json
      * iOS

         * ADBMobile.h
         * ADBMobileConfig.json
         * ADBMobileWrapper.h
         * ADBMobileWrapper.mm
         * AdobeMobileLibrary.a



Optionale Ordner: Der Ordner „Demo“ enthält Unity-Szenen und Codebeispiele für die unterstützten Skriptsprachen.

## Importieren des ADBMobile-Plugins in ein Unity-Projekt {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. Öffnen Sie das Unity-Projekt.
1. Doppelklicken Sie auf **[!UICONTROL ADBMobile.unitypackage]**.
1. Wählen Sie die zu importierenden Ordner aus.

