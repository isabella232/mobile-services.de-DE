---
description: Nachdem Sie die Deep-Link-URL in der Adobe Mobile Services-Benutzeroberfläche konfiguriert haben, befindet sich diese URL in der Push-Payload mit dem Schlüssel „adb_deeplink“.
seo-description: Nachdem Sie die Deep-Link-URL in der Adobe Mobile Services-Benutzeroberfläche konfiguriert haben, befindet sich diese URL in der Push-Payload mit dem Schlüssel „adb_deeplink“.
seo-title: Push-Nachrichten mit Deep-Linking implementieren
title: Push-Nachrichten mit Deep-Linking implementieren
uuid: ee9590fc-8bd3-4111-9221-9011d9edbd84
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 93%

---


# Push-Nachrichten mit Deep-Links implementieren {#implement-push-messaging-with-deep-linking}

Nachdem Sie die Deep-Link-URL in der Adobe Mobile Services-Benutzeroberfläche konfiguriert haben, befindet sich diese URL in der Push-Payload mit dem Schlüssel `adb_deeplink`.

1. In „AppDelegate“ können Sie die Deep-Link-URL zurückerhalten und sie manuell an den folgenden Orten verarbeiten:

   * Mit `application:didFinishLaunchingWithOptions`:

      Wenn die App nicht ausgeführt wird, wenn ein Push-Clickthrough-Vorgang erfolgt, können Sie die Push-Nutzlast aus `launchOptions` abrufen und die Deep-Link-URL befindet sich durch den Schlüssel `adb_deeplink` im Nutzlastverzeichnis.

   * Die „delegate“-Methoden für Remotebenachrichtigung

      In der `didReceiveRemoteNotification:`-App oder in der `didReceiveRemoteNotification:fetchCompletionHandler:`-App können Sie die URL abrufen, indem Sie auf das Verzeichnis `userInfo` mit dem `adb_deeplink`-Schlüssel zugreifen.

   * Die „delegate“-Methoden für `UNUserNotificationCenter`

      In der `userNotificationCenter:didReceiveNotificationResponse:withCompletionHandler:`-Methode können Sie die Push-Payload aus dem `userInfo`-Wörterbuch im `adb_deeplink`-Schlüssel abrufen.

Beispiel:

```objective-c
- (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    NSDictionary *remoteNotification = launchOptions[UIApplicationLaunchOptionsRemoteNotificationKey]; 
    if (remoteNotification && [remoteNotification isKindOfClass:[NSDictionary class]]) { 
        NSString *deeplink = remoteNotification[@"adb_deeplink"]; 
        // handle deep link url 
    }
    return YES; 
} 
  
// app target < iOS 7 
- (void) application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
    // only send the hit if the app is not active 
    if (application.applicationState == UIApplicationStateInactive) { 
        [ADBMobile trackPushMessageClickThrough:userInfo]; 
        NSString *deeplink = userInfo[@"adb_deeplink"]; 
        // handle deep link url 
    } 
} 
  
// app target >= iOS 7 
- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler { 
    if (application.applicationState == UIApplicationStateInactive) { 
        [ADBMobile trackPushMessageClickThrough:userInfo]; 
        NSString *deeplink = userInfo[@"adb_deeplink"]; 
        // handle deep link url 
    } 
    ... 
} 
 
// if using UNUserNotificationCenterDelegate and device is running iOS 10 or newer 
- (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
    if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
        [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
        NSString *deeplink = response.notification.request.content.userInfo[@"adb_deeplink"]; 
        // handle deep link url  
    } 
    ... 
}
```

