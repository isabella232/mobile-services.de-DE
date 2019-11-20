---
description: Mit diesem Plug-in senden Sie Adobe Analytics-Aufrufe aus Ihren Unity-Anwendungen heraus.
keywords: Unity
seo-description: Mit diesem Plug-in senden Sie Adobe Analytics-Aufrufe aus Ihren Unity-Anwendungen heraus.
seo-title: Unity Plug-in für die iOS- und Android 4.x-SDKs
solution: Experience Cloud, Entwickler
title: Unity Plug-in für die iOS- und Android 4.x-SDKs
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
translation-type: ht
source-git-commit: df4ff7128357a18c56d840eb5697f9c8813ad751

---


# Unity Plug-in für die iOS- und Android 4.x-SDKs {#unity-plug-in-for-the-ios-and-android-x-sdks}

Mit diesem Plug-in senden Sie Adobe Analytics-Aufrufe aus Ihren Unity-Anwendungen heraus.

Zuletzt aktualisiert: **12. November 2019**

## Erste Schritte {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

Laden Sie die Datei [ADBMobile.unitypackage](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) von GitHub oder Developer Connection herunter.

Im Folgenden finden Sie den Inhalt der Datei `ADBMobile.unitypackage`:

* Assets (Stammverzeichnis)

   * ADBMobile

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

## Importieren des ADBMobile-Plug-ins in ein Unity-Projekt  {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. Öffnen Sie Ihr Unity-Projekt.
1. Doppelklicken Sie auf **[!UICONTROL ADBMobile.unitypackage]**.
1. Wählen Sie die zu importierenden Ordner aus.

