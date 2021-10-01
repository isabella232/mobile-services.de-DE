---
description: Ab WatchOS 2 können Ihre WatchKit-Erweiterungen auf einer Apple Watch ausgeführt werden. Für Apps, die in dieser Umgebung ausgeführt werden, ist das WatchConnectivity-Framework erforderlich, damit Daten für die übergeordnete iOS-App freigegeben werden können.
solution: Experience Cloud,Analytics
title: Apple Watch-Implementierungen mit WatchOS 2
topic-fix: Developer and implementation
uuid: 9498467e-db5e-411e-a00e-d19841f485de
exl-id: 9fc9b799-1081-42e4-acf3-569fdeb07aff
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 100%

---

# Apple Watch-Implementierungen mit WatchOS 2 {#apple-watch-implementation-with-watchos}

Ab WatchOS 2 können Ihre WatchKit-Erweiterungen auf einer Apple Watch ausgeführt werden. Für Apps, die in dieser Umgebung ausgeführt werden, ist das `WatchConnectivity`-Framework erforderlich, damit Daten für die übergeordnete iOS-App freigegeben werden können.

>[!TIP]
>
>Ab `AdobeMobileLibrary`-Version 4.6.0 wird `WatchConnectivity` unterstützt.

## Neue Version des Adobe Experience Platform Mobile SDK

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDK für die Adobe Experience Platform? Klicken Sie [hier](https://aep-sdks.gitbook.io/docs/), um unsere aktuelle Dokumentation abzurufen.

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDKs können über [Experience Platform Launch](https://www.adobe.com/de/experience-platform/launch.html) konfiguriert werden.

* Beginnen Sie mit Adobe Experience Platform Launch.
* Gehen Sie zu [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK-Repositorys enthalten ist.

## Erste Schritte {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>Stellen Sie sicher, dass Sie ein Projekt mit mindestens den folgenden Zielen haben:
>
>* Die übergeordnete App
>* Die WatchKit-App
>* Die WatchKit-Erweiterung

>


Weitere Informationen zum Entwickeln von WatchKit-Apps finden Sie unter [Die Watch-App-Architektur](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/DesigningaWatchKitApp.html#//apple_ref/doc/uid/TP40014969-CH3-SW1).

## Übergeordnete Apps konfigurieren {#section_0A2A3995575B4E2ABD12E426BA06AEFF}

Führen Sie die folgenden Schritte in Ihrem Xcode-Projekt aus:

1. Ziehen Sie den Ordner `AdobeMobileLibrary` in Ihr Projekt.
1. Stellen Sie sicher, dass die `ADBMobileConfig.json`-Datei ein Mitglied des Ziels Ihrer übergeordneten App ist.
1. Blenden Sie auf der Registerkarte **[!UICONTROL Build-Phasen]** des Ziels Ihrer übergeordneten App den Abschnitt **[!UICONTROL Binärdatei mit Bibliotheken verknüpfen]** ein und fügen Sie die folgenden Bibliotheken hinzu:

   * `AdobeMobileLibrary.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. Fügen Sie in Ihrer Klasse, die das `UIApplicationDelegate`-Protokoll implementiert, das `WCSessionDelegate`-Protokoll hinzu.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface AppDelegate : UIResponder <UIApplicationDelegate, WCSessionDelegate>
   ```

1. Importieren Sie in der Implementierungsdatei Ihrer App-Delegatklasse `AdobeMobileLibrary`.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Bevor Sie einen Aufruf für die `ADBMobile`-Bibliothek vornehmen, konfigurieren Sie in `application:didFinishLaunchingWithOptions:` Ihres App-Delegats Ihre `WCSession`.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. Implementieren Sie in Ihrem App-Delegat die Methoden `session:didReceiveMessage:` und `session:didReceiveUserInfo:`.

   `syncSettings:` wird in der `ADBMobile`-Bibliothek aufgerufen und gibt einen booleschen Wert zurück, der angibt, ob das Wörterbuch für die Verwendung durch die `ADBMobile`-Bibliothek vorgesehen war. Wenn `No` (NEIN) zurückgegeben wird, wurde die Nachricht nicht vom Adobe-SDK initiiert.

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## WatchKit-Erweiterung konfigurieren {#section_5ADE31741E514330A381F2E3CFD4A814}

1. Stellen Sie sicher, dass die `ADBMobileConfig.json`-Datei ein Mitglied des Ziels Ihrer WatchKit-Erweiterung ist.
1. Blenden Sie auf der Registerkarte **[!UICONTROL Build-Phasen]** des Ziels Ihrer WatchKit-Erweiterung den Abschnitt **[!UICONTROL Binärdatei mit Bibliotheken verknüpfen]** ein und fügen Sie die folgenden Bibliotheken hinzu:

   * `AdobeMobileLibrary_Watch.a`
   * `libsqlite3.tbd`

1. Importieren Sie in Ihrer Klasse, die das `WKExtensionDelegate`-Protokoll implementiert, `WatchConnectivity` und fügen Sie das `WCSessionDelegate`-Protokoll hinzu.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface ExtensionDelegate : NSObject <WKExtensionDelegate, WCSessionDelegate>
   ```

1. Importieren Sie in der Implementierungsdatei Ihrer Erweiterungsdelegatklasse `AdobeMobileLibrary`.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Konfigurieren Sie in `applicationDidFinishLaunching` Ihres Erweiterungsdelegats Ihre `WCSession`, bevor Sie Aufrufe für die `ADBMobile`-Bibliothek vornehmen.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. Initialisieren Sie in `applicationDidFinishLaunching` Ihres Erweiterungsdelegats die Watch-App für das SDK.

   ```objective-c
   [ADBMobile initializeWatch];
   ```

1. Implementieren Sie in Ihrem Erweiterungsdelegat die Methoden `session:didReceiveMessage:` und `session:didReceiveUserInfo:`.

   `syncSettings:` wird in der `ADBMobile`-Bibliothek aufgerufen und gibt einen booleschen Wert zurück, der angibt, ob das Wörterbuch für die Verwendung durch die `ADBMobile`-Bibliothek vorgesehen war. Wenn `NO` (NEIN) zurückgegeben wird, wurde die Nachricht nicht vom Adobe-SDK initiiert.

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## Zusätzliche Informationen {#section_7BCDB5CF0D424DCA97883753D1881233}

Beachten Sie die folgenden Informationen:

* Bei WatchKit-Apps wird `a.RunMode` auf `Extension` festgelegt.
* Da WatchKit-Apps auf der Uhr ausgeführt werden, melden die Apps ihre Namen richtig in `a.AppID`.
* Für WatchOS2-Apps wird kein Lebenszyklusaufruf ausgelöst.
