---
description: Ab WatchOS 2 werden Ihre WatchKit-Erweiterungen auf einem Apple Watch-Gerät ausgeführt. Für Anwendungen, die in dieser Umgebung ausgeführt werden, ist das WatchConnectivity-Framework erforderlich, damit Daten für die übergeordnete iOS-App freigegeben werden können.
seo-description: Ab WatchOS 2 werden Ihre WatchKit-Erweiterungen auf einem Apple Watch-Gerät ausgeführt. Für Anwendungen, die in dieser Umgebung ausgeführt werden, ist das WatchConnectivity-Framework erforderlich, damit Daten für die übergeordnete iOS-App freigegeben werden können.
seo-title: Apple Watch-Implementierungen mit WatchOS 2
solution: Marketing Cloud, Analytics
title: Apple Watch-Implementierungen mit WatchOS 2
topic: Entwickler und Implementierung
uuid: 9498467e-db5e-411e-a00e-d19841f485de
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Apple Watch implementation with WatchOS 2{#apple-watch-implementation-with-watchos}

Starting with WatchOS 2, your WatchKit Extensions can run on an Apple Watch. Applications that run in this environment require the `WatchConnectivity` framework to share data with their containing iOS app.

>[!TIP]
>
>Ab `AdobeMobileLibrary` Version 4.6.0 wird `WatchConnectivity` unterstützt.

## Erste Schritte {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>Vergewissern Sie sich, dass Sie über ein Projekt mit mindestens den folgenden Zielen verfügen:
>
>* die übergeordnete App.
>* die WatchKit-App.
>* die WatchKit-Erweiterung.
>



Weitere Informationen zum Entwickeln von WatchKit-Apps finden Sie im Artikel zur [Watch-App-Architektur](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/DesigningaWatchKitApp.html#//apple_ref/doc/uid/TP40014969-CH3-SW1).

## Konfigurieren der zugehörigen App {#section_0A2A3995575B4E2ABD12E426BA06AEFF}

Führen Sie die folgenden Schritte in Ihrem Xcode-Projekt aus:

1. Ziehen Sie den Ordner `AdobeMobileLibrary` in Ihr Projekt.
1. Ensure that the `ADBMobileConfig.json` file is a member of the containing app’s target.
1. Blenden Sie auf der Registerkarte **[!UICONTROL Build-Phasen]** des Ziels Ihrer übergeordneten App den Abschnitt **Binärdatei mit Bibliotheken verknüpfen]ein und fügen Sie die folgenden Bibliotheken hinzu:[!UICONTROL **

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
   #import “ADBMobile.h”
   ```

1. Before making a call to the `ADBMobile` library, in `application:didFinishLaunchingWithOptions:` of your app delegate, configure your `WCSession`.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. In your app delegate, implement the `session:didReceiveMessage:` and `session:didReceiveUserInfo:` methods.

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

1. Ensure that the `ADBMobileConfig.json` file is a member of your WatchKit extension’s target.
1. Blenden Sie auf der Registerkarte **[!UICONTROL Build-Phasen]** des Ziels Ihrer WatchKit-Erweiterung den Abschnitt **Binärdatei mit Bibliotheken verknüpfen]ein und fügen Sie die folgenden Bibliotheken hinzu:[!UICONTROL **

   * `AdobeMobileLibrary_Watch.a`
   * `libsqlite3.tbd`

1. In your class that implements the `WKExtensionDelegate` protocol, import `WatchConnectivity` and add the `WCSessionDelegate` protocol.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface ExtensionDelegate : NSObject <WKExtensionDelegate, WCSessionDelegate>
   ```

1. Importieren Sie in der Implementierungsdatei Ihrer Erweiterungsdelegatklasse `AdobeMobileLibrary`.

   ```objective-c
   #import “ADBMobile.h”
   ```

1. In `applicationDidFinishLaunching` of your extension delegate, configure your `WCSession` before making any calls to the `ADBMobile` library.

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

1. In your extension delegate, implement the `session:didReceiveMessage:` and `session:didReceiveUserInfo:` methods.

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

* For WatchKit apps, `a.RunMode` will be set to `Extension`.
* Da WatchKit-Apps auf der Uhr ausgeführt werden, melden die Apps ihre Namen richtig in `a.AppID`.
* Für WatchOS2-Apps wird kein Lebenszyklusaufruf ausgelöst.

