---
description: Adobe Mobile und das Adobe Mobile SDK ermöglichen es Ihnen, Push-Nachrichten an Ihre Benutzer zu senden. Mit dem SDK können Sie darüber hinaus auf einfache Weise Benutzer erfassen, die Ihre App durch Klicken auf eine Push-Nachricht geöffnet haben.
seo-description: Adobe Mobile und das Adobe Mobile SDK ermöglichen es Ihnen, Push-Nachrichten an Ihre Benutzer zu senden. Mit dem SDK können Sie darüber hinaus auf einfache Weise Benutzer erfassen, die Ihre App durch Klicken auf eine Push-Nachricht geöffnet haben.
seo-title: Push-Nachrichten
solution: Experience Cloud,Analytics
title: Push-Nachrichten
topic: Developer and implementation
uuid: 2e2d8175-d7d0-4b6b-a14e-d419da1f9615
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 100%

---


# Push-Nachrichten {#push-messaging}

Adobe Mobile und das Adobe Mobile SDK ermöglichen es Ihnen, Push-Nachrichten an Ihre Benutzer zu senden. Mit dem SDK können Sie darüber hinaus auf einfache Weise Benutzer erfassen, die Ihre App durch Klicken auf eine Push-Nachricht geöffnet haben.

>[!IMPORTANT]
>
>Die Informationen in diesem Thema sind ein Vorschlag für eine mögliche Implementierung. Es wird dringend empfohlen, dass Sie die iOS-Dokumentation von Apple lesen, um die beste Implementierung für Ihre Anwendung zu bestimmen. Ihre Implementierung sollte anhand der von Ihnen verwendeten Frameworks und der iOS-Versionen bestimmt werden, auf die Ihre App ausgerichtet ist.

Um In-App-Nachrichten zu nutzen, ist SDK-Version 4.6 (oder höher) **erforderlich**.

>[!IMPORTANT]
>
>Legen Sie die Experience Cloud ID nicht manuell in Ihrer App fest. Dies führt zur Erstellung eines neuen Unique Users, der aufgrund seines Opt-in-Status keine Push-Nachrichten erhält. Angenommen, ein Benutzer, der sich für den Empfang von Push-Nachrichten angemeldet hat, meldet sich bei Ihrer App an. Wenn Sie nach der Anmeldung die ID manuell in Ihrer App festlegen, wird ein neuer Unique User erstellt, der sich nicht für den Empfang von Push-Nachrichten entschieden hat. Dementsprechend erhält dieser neue Benutzer keine Push-Nachrichten.

## Voraussetzungen  {#section_06655ABE973743DC965897B229A2118D}

* Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie die Lebenszyklusmetriken.

   Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/ios/metrics.md).


* Das SDK muss für den ID-Dienst aktiviert sein. 
Weitere Informationen finden Sie unter [Optionen für SDK-ID-Dienst konfigurieren](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-visitor.md).

>[!IMPORTANT]
>
>Das Verschieben Ihrer App in eine neue Report Suite wird nicht unterstützt. Wenn Sie zu einer neuen Berichtssuite migrieren, kann Ihre Push-Konfiguration kaputt gehen und Nachrichten werden möglicherweise nicht gesendet.

## Push-Nachrichten aktivieren {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

1. Überprüfen Sie, ob die Datei `ADBMobileConfig.json` die erforderlichen Einstellungen für Push-Nachrichten enthält.

   Im Objekt `"marketingCloud"` muss die zugehörige Eigenschaft `"org"` für Push-Nachrichten konfiguriert sein.

   ```objective-c
   "marketingCloud": { 
       "org": "3CE342C92046435B0A490D4C@AdobeOrg" 
   }
   ```

1. Importieren Sie die Bibliothek in Ihr `AppDelegate`.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Lesen Sie [Support für Remote-Benachrichtigung konfigurieren](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/HandlingRemoteNotifications.html#//apple_ref/doc/uid/TP40008194-CH6-SW1), um die Einstellungen zu bestimmen, für die Ihre App eine Berechtigung anfordern muss.

   Hier ist ein Beispiel einer möglichen Implementierung, die um Zugriffsberechtigung zum Verwenden von Warnhinweisen, Zeichen, Tönen und Remote-Benachrichtigungen bittet:

   ```objective-c
   // iOS 10 and newer 
   if (NSClassFromString(@"UNUserNotificationCenter")) { 
       UNUserNotificationCenter *center = [UNUserNotificationCenter currentNotificationCenter];   
       [center requestAuthorizationWithOptions:(UNAuthorizationOptionAlert + UNAuthorizationOptionSound + UNAuthorizationOptionBadge) 
           completionHandler:^(BOOL granted, NSError * _Nullable error) { 
           if (granted) { NSLog(@"authorization given"); } 
           else { NSLog(@"authorization rejected"); } 
           if (error) { NSLog(@"error during authorization: %@", error.localizedDescription); } 
       }]; 
       // have to ask for permission for remote notifications separately  
       [application registerForRemoteNotifications]; 
       // make this class the delegate for user notification handling  
       center.delegate = self; 
   } 
   // iOS 8.0 to iOS 9.3.5 
   else if ([application respondsToSelector:@selector(registerUserNotificationSettings:)]) { 
   #pragma GCC diagnostic push 
   #pragma GCC diagnostic ignored "-Wdeprecated-declarations" 
       UIUserNotificationTypetypes = UIUserNotificationTypeAlert | UIUserNotificationTypeBadge| UIUserNotificationTypeSound; 
       UIUserNotificationSettings *settings = [UIUserNotificationSettings settingsForTypes:types categories:nil]; 
       [application registerUserNotificationSettings:settings]; 
       // have to ask for permission for remote notifications separately  
       [application registerForRemoteNotifications]; 
   } 
   // older than iOS 8.0  
   else { 
       [application registerForRemoteNotificationTypes:UIRemoteNotificationTypeAlert | UIRemoteNotificationTypeBadge| UIRemoteNotificationTypeSound];  
   #pragma GCC diagnostic pop 
   }
   ```

1. Das Push-Token muss mithilfe der Methode `setPushIdentifier:` in der ADBMobile-Klasse an das SDK weitergegeben werden.

   ```objective-c
   - (void) application:(UIApplication *)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken { 
       ... 
       [ADBMobile setPushIdentifier:deviceToken]; 
       ... 
   }
   ```

1. Lesen Sie [UserNotifications](https://developer.apple.com/documentation/usernotifications), um die richtige Implementierung für Ihre Umgebung zu ermitteln.

   Dieser Schritt hilft Ihnen beim Aktivieren der Push-Berichterstellung, indem das `userInfo`-Wörterbuch an das SDK übergeben wird, wenn der Benutzer die Anwendung durch das Klicken auf eine Push-Nachricht öffnet.

   Der folgende Code ist ein Beispiel für eine mögliche Implementierung:

   ```objective-c
   // device running < iOS 7 
   - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
       // only send the hit if the app is inactive 
       if (application.applicationState == UIApplicationStateInactive) {  
           [ADBMobile trackPushMessageClickThrough:userInfo]; 
       } 
   } 
   // device running between iOS 7 and iOS 9.3.5 
   - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult)) completionHandler { 
       // only send the hit if the app is inactive 
       if (application.applicationState == UIApplicationStateInactive) { 
           // only run this code if the UNUserNotificationCenterclass is not available or its delegate is not set (pre iOS 10) 
           if (!NSClassFromString(@"UNUserNotificationCenter") || ![UNUserNotificationCenter currentNotificationCenter].delegate) {  
               [ADBMobiletrackPushMessageClickThrough:userInfo]; 
           } 
       } 
       completionHandler(UIBackgroundFetchResultNoData); 
   } 
   // device running >= iOS 10 
   - (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
       if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
           [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
       } 
       completionHandler(); 
   }
   ```

1. Damit Ihre geschätzte Push-Zielgruppe genau erhalten bleibt, benachrichtigen Sie das SDK, wenn ein Benutzer die Push-Nachrichten für Ihre App manuell deaktiviert, indem Sie `[ADBMobile setPushIdentifier: nil]` in der `applicationDidBecomeActive:`-Methode in `AppDelegate` aufrufen.

   ```objective-c
   // device running < iOS 7 
   - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
       // only send the hit if the app is inactive 
       if (application.applicationState == UIApplicationStateInactive) {  
           [ADBMobile trackPushMessageClickThrough:userInfo]; 
       } 
   } 
   // device running between iOS 7 and iOS 9.3.5 
   - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult)) completionHandler { 
       // only send the hit if the app is inactive 
       if (application.applicationState == UIApplicationStateInactive) { 
           // only run this code if the UNUserNotificationCenterclass is not available or its delegate is not set (pre iOS 10) 
           if (!NSClassFromString(@"UNUserNotificationCenter") || ![UNUserNotificationCenter currentNotificationCenter].delegate) {  
               [ADBMobiletrackPushMessageClickThrough:userInfo]; 
           } 
       } 
       completionHandler(UIBackgroundFetchResultNoData); 
   } 
   // device running >= iOS 10 
   - (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
       if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
           [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
       } 
       completionHandler(); 
   }
   ```

## Beispiel {#section_20BEA0D64F7C4D45A5EBEF21066E62AD}

Im Folgenden finden Sie ein Beispiel dafür, wie eine `AppDelegate.m`-Implementierung aussehen könnte:

```objective-c
#import "AppDelegate.h" 
#import "ADBMobile.h" 
 
@implementation AppDelegate 
  
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
    if (NSClassFromString(@"UNUserNotificationCenter")) { 
        UNUserNotificationCenter *center = [UNUserNotificationCenter currentNotificationCenter]; 
        [center requestAuthorizationWithOptions:(UNAuthorizationOptionAlert + UNAuthorizationOptionSound + UNAuthorizationOptionBadge) 
                              completionHandler:^(BOOL granted, NSError * _Nullable error) {  
            if (granted) { NSLog(@"authorization given"); } 
            else { NSLog(@"authorization rejected"); } 
            if (error) { NSLog(@"error during authorization: %@", error.localizedDescription); } 
        }]; 
        center.delegate = self; 
        [application registerForRemoteNotifications]; 
    } 
    else if ([application respondsToSelector:@selector(registerUserNotificationSettings:)]) { 
#pragma GCC diagnostic push 
#pragma GCC diagnostic ignored "-Wdeprecated-declarations"  
        UIUserNotificationType types = UIUserNotificationTypeAlert | UIUserNotificationTypeBadge| UIUserNotificationTypeSound; 
        UIUserNotificationSettings *settings = [UIUserNotificationSettings settingsForTypes:types categories:nil]; 
        [application registerUserNotificationSettings:settings];  
        [application registerForRemoteNotifications]; 
    } 
    else { 
        [application registerForRemoteNotificationTypes:UIRemoteNotificationTypeAlert| UIRemoteNotificationTypeBadge| UIRemoteNotificationTypeSound]; 
#pragma GCC diagnostic pop 
    } 
 
    return YES; 
} 
 
- (void) applicationDidBecomeActive:(UIApplication *)application {  
    if (NSClassFromString(@"UNUserNotifcationCenter")) { 
        UNUserNotificationCenter *center = [UNUserNotificationCenter currentNotificationCenter]; 
        [center getNotificationSettingsWithCompletionHandler:^(UNNotificationSettings * _Nonnull settings) { 
            if (settings.authorizationStatus != UNAuthorizationStatusAuthorized) {  
                [ADBMobile setPushIdentifier:nil]; 
            } 
        }]; 
    } 
#pragma GCC diagnostic push 
#pragma GCC diagnostic ignored "-Wdeprecated-declarations"  
    else if ([application respondsToSelector:@selector(isRegisteredForRemoteNotifications)]) { 
        if (![application isRegisteredForRemoteNotifications]) {  
            [ADBMobile setPushIdentifier:nil]; 
        } 
    } 
    else if ([application enabledRemoteNotificationTypes] == UIRemoteNotificationTypeNone) { 
        [ADBMobile setPushIdentifier:nil]; 
    } 
#pragma GCC diagnostic pop 
} 
 
- (void) application:(UIApplication *)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken { 
    [ADBMobile setPushIdentifier:deviceToken]; 
} 
 
- (void) application:(UIApplication *)application didFailToRegisterForRemoteNotificationsWithError:(NSError *)error { 
    [ADBMobile setPushIdentifier:nil]; 
} 
 
- (void) application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo { 
    if (application.applicationState == UIApplicationStateInactive) {  
        [ADBMobile trackPushMessageClickThrough:userInfo];  
    } 
} 
 
- (void) application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler { 
    if (application.applicationState == UIApplicationStateInactive) {  
        if (!NSClassFromString(@"UNUserNotificationCenter") || ![UNUserNotificationCenter currentNotificationCenter].delegate) {  
            [ADBMobile trackPushMessageClickThrough:userInfo]; 
        } 
    } 
 
    completionHandler(UIBackgroundFetchResultNoData); 
} 
 
- (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler { 
    if ([response.notification.request.trigger isKindOfClass:UNPushNotificationTrigger.class]) { 
        [ADBMobile trackPushMessageClickThrough:response.notification.request.content.userInfo]; 
    } 
 
    completionHandler(); 
} 
 
@end
```
