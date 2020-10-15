---
description: Diese Informationen helfen Ihnen beim Implementieren von Apple TV mit tvOS.
seo-description: Diese Informationen helfen Ihnen beim Implementieren von Apple TV mit tvOS.
seo-title: Apple TV-Implementierungen mit tvOS
solution: Experience Cloud,Analytics
title: Apple TV-Implementierungen mit tvOS
topic: Developer and implementation
uuid: d1571ea2-a5de-4b96-a527-72abbf51fab8
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '402'
ht-degree: 100%

---


# Apple TV-Implementierungen mit tvOS {#apple-tv-implementation-with-tvos}

Diese Informationen helfen Ihnen beim Implementieren von Apple TV mit tvOS.

## Neue Version des Adobe Experience Platform Mobile SDK

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDK für die Adobe Experience Platform? Klicken Sie [hier](https://aep-sdks.gitbook.io/docs/), um unsere aktuelle Dokumentation abzurufen.

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDK können über [Experience Platform Launch](https://www.adobe.com/de/experience-platform/launch.html) konfiguriert werden.

* Beginnen Sie mit Adobe Experience Platform Launch.
* Gehen Sie zu [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK-Repositorys enthalten ist.

## Übersicht

Mit Apple TV können Sie jetzt Anwendungen erstellen, die in der nativen tvOS-Umgebung ausgeführt werden. Sie können eine native App mit verschiedenen in iOS verfügbaren Frameworks oder eine App mit XML-Vorlagen und JavaScript erstellen.

>[!TIP]
>
>Unterstützung für tvOS ist ab `AdobeMobileLibrary`-Version 4.7.0 verfügbar.

## Erste Schritte {#section_CAB40A5B5FC745068C8A5DF8F9AB6199}

>[!TIP]
>
>Es wird davon ausgegangen, dass Ihr Projekt eine Apple TV-App unter tvOS als Ziel hat. Weitere Informationen finden Sie unter [tvOS](https://developer.apple.com/tvos/documentation/).

## Native Apps für tvOS konfigurieren {#section_5095F19B3C4545F68E8C1E37A7E303AE}

Führen Sie die folgenden Schritte in Ihrem Xcode-Projekt aus:

1. Ziehen Sie den Ordner AdobeMobileLibrary in Ihr Projekt.
1. Stellen Sie sicher, dass die Datei `ADBMobileConfig.json` ein Mitglied Ihres Ziels ist.
1. Blenden Sie auf der Registerkarte **[!UICONTROL Build-Phasen]** des Ziels Ihrer tvOS-App den Abschnitt **[!UICONTROL Binärdatei mit Bibliotheken verknüpfen]** ein und fügen Sie die folgenden Bibliotheken hinzu:

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

Weitere Informationen finden Sie in der iOS-Dokumentation unter [iOS](https://developer.apple.com/ios/resources/).

## TVML-/TVJS-App für tvOS konfigurieren {#section_AB2EC8C326654F3387658EBBD990BB12}

1. Ziehen Sie den Ordner `AdobeMobileLibrary` in Ihr Projekt.
1. Stellen Sie sicher, dass die Datei `ADBMobileConfig.json` ein Mitglied Ihres Ziels ist.
1. Blenden Sie auf der Registerkarte **[!UICONTROL Build-Phasen]** des Ziels Ihrer tvOS-App den Abschnitt **[!UICONTROL Binärdatei mit Bibliotheken verknüpfen]** ein und fügen Sie die folgenden Bibliotheken hinzu:

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

1. Importieren Sie das SDK in der Implementierungsdatei Ihrer `TVApplicationControllerDelegate`-Klasse.

   ```objective-c
   #import “ADBMobile.h"
   ```

1. Übergeben Sie in der `application:didFinishLaunchWithOptions:`-Methode Ihrer `TVApplicationControllerDelegate`-Klasse Ihr `TVApplicationController`-Objekt mit der `installTVMLHooks:`-Methode an das SDK.

   Das Adobe-SDK benötigt Zugriff auf das `TVApplicationController`-Objekt Ihrer App, um sich selbst im JSContext Ihrer App zu registrieren. Mit diesem Schritt können Sie die nativen Methoden im Adobe-SDK aus Ihren JavaScript-Dateien aufrufen.

   ```objective-c
   [ADBMobile installTVMLHooks:appController];
   ```

1. Verwenden Sie in Ihren JavaScript-Dateien das `ADBMobile`-Objekt, um auf die nativen Methoden des Adobe-SDK zuzugreifen.

   Eine vollständige Liste der verfügbaren Methoden finden Sie unter [TVJS-Methoden](/help/ios/apple-tv-implementation-tvos/tvjs-methods.md).

