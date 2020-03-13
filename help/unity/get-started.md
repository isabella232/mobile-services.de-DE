---
description: Mit diesem Plug-in senden Sie Adobe Analytics-Aufrufe aus Ihren Unity-Anwendungen heraus.
keywords: Unity
seo-description: Mit diesem Plug-in senden Sie Adobe Analytics-Aufrufe aus Ihren Unity-Anwendungen heraus.
seo-title: Unity Plug-in für die iOS- und Android 4.x-SDKs
solution: Marketing Cloud,Developer
title: Unity Plug-in für die iOS- und Android 4.x-SDKs
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
translation-type: ht
source-git-commit: 0d50c7e6674de33b8190e74c113ae010ff226e97

---


# Unity Plug-in für die iOS- und Android 4.x-SDKs {#unity-plug-in-for-the-ios-and-android-x-sdks}

Mit diesem Plug-in senden Sie Adobe Analytics-Aufrufe aus Ihren Unity-Anwendungen heraus.

Zuletzt aktualisiert: **10. März 2020**
* [Unity-v4.19.0](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases/tag/v4.19.0-Unity)

## Erste Schritte {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

Laden Sie die Datei ADBMobile.unitypackage von GitHub herunter.

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


**Optionale Ordner**: Der *Demo*-Ordner enthält Unity-Szenen und Beispielcode.

## Importieren des ADBMobile-Plug-ins in ein Unity-Projekt {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. Öffnen Sie Ihr Unity-Projekt.
1. Doppelklicken Sie auf **[!UICONTROL ADBMobile.unitypackage]**.
1. Wählen Sie die zu importierenden Ordner aus.
