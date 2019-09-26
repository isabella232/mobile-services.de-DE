---
description: Diese Informationen helfen Ihnen beim Implementieren von Apple TV mit tvOS.
seo-description: Diese Informationen helfen Ihnen beim Implementieren von Apple TV mit tvOS.
seo-title: Apple TV-Implementierungen mit tvOS
solution: Marketing Cloud, Analytics
title: Apple TV-Implementierungen mit tvOS
topic: Entwickler und Implementierung
uuid: d1571ea2-a5de-4b96-a527-72abbf51fab8
translation-type: tm+mt
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# Apple TV implementation with tvOS {#apple-tv-implementation-with-tvos}

Diese Informationen helfen Ihnen beim Implementieren von Apple TV mit tvOS.

## New Adobe Experience Platform Mobile SDK Release

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDKs für die Adobe Experience Platform? Klicken Sie für die neueste Dokumentation [hier](https://aep-sdks.gitbook.io/docs/).

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDKs können über die [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) konfiguriert werden.

* Beginnen Sie mit Adobe Experience Platform Launch.
* Gehen Sie zu [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK Repositorys enthalten ist.

## Übersicht

Mit Apple TV können Sie Apps erstellen, die in der nativen tvOS-Umgebung ausgeführt werden. Sie können eine native App mit mehreren in iOS verfügbaren Frameworks erstellen oder eine App über XML-Vorlagen und JavaScript erstellen.

>[!TIP]
>
>tvOS support is available starting in  version 4.7.0.`AdobeMobileLibrary`

## Erste Schritte {#section_CAB40A5B5FC745068C8A5DF8F9AB6199}

>[!TIP]
>
>Wir gehen davon aus, dass Ihr Projekt ein Ziel hat, das eine Apple TV-App ist, die auf tvOS abzielt. Weitere Informationen finden Sie unter [tvOS](https://developer.apple.com/tvos/documentation/).

## Configure a native app for tvOS {#section_5095F19B3C4545F68E8C1E37A7E303AE}

Führen Sie die folgenden Schritte in Ihrem Xcode-Projekt aus:

1. Ziehen Sie den Ordner AdobeMobileLibrary in Ihr Projekt.
1. Ensure that the `ADBMobileConfig.json` file is a member of your target.
1. Blenden Sie auf der Registerkarte **[!UICONTROL Build-Phasen]** des Ziels Ihrer tvOS-App den Abschnitt **Binärdatei mit Bibliotheken verknüpfen]ein und fügen Sie die folgenden Bibliotheken hinzu:[!UICONTROL **

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

Weitere Informationen finden Sie in der iOS-Dokumentation unter [iOS](https://developer.apple.com/ios/resources/).

## Configure a TVML/TVJS app for tvOS {#section_AB2EC8C326654F3387658EBBD990BB12}

1. Ziehen Sie den Ordner `AdobeMobileLibrary` in Ihr Projekt.
1. Ensure that the `ADBMobileConfig.json` file is a member of your target.
1. Blenden Sie auf der Registerkarte **[!UICONTROL Build-Phasen]** des Ziels Ihrer tvOS-App den Abschnitt **Binärdatei mit Bibliotheken verknüpfen]ein und fügen Sie die folgenden Bibliotheken hinzu:[!UICONTROL **

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

1. Importieren Sie das SDK in der Implementierungsdatei Ihrer `TVApplicationControllerDelegate`-Klasse.

   ```objective-c
   #import “ADBMobile.h"
   ```

1. In the `application:didFinishLaunchWithOptions:` method of your `TVApplicationControllerDelegate` class, pass your `TVApplicationController` object to the SDK with the `installTVMLHooks:` method.

   Das Adobe-SDK benötigt Zugriff auf das `TVApplicationController`-Objekt Ihrer App, um sich selbst im JSContext Ihrer App zu registrieren. Mit diesem Schritt können Sie die nativen Methoden im Adobe-SDK aus Ihren JavaScript-Dateien aufrufen.

   ```objective-c
   [ADBMobile installTVMLHooks:appController];
   ```

1. Verwenden Sie in Ihren JavaScript-Dateien das `ADBMobile`-Objekt, um auf die nativen Methoden des Adobe-SDK zuzugreifen.

   For a complete listing of the available methods, see [TVJS Methods](/help/ios/apple-tv-implementation-tvos/tvjs-methods.md).

