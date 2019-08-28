---
description: Hier finden Sie eine Liste der Adobe Analytics-Methoden, die von der iOS-Bibliothek bereitgestellt werden.
seo-description: Hier finden Sie eine Liste der Adobe Analytics-Methoden, die von der iOS-Bibliothek bereitgestellt werden.
seo-title: Analytics-Methoden
solution: Marketing Cloud, Analytics
title: Analytics-Methoden
topic: Entwickler und Implementierung
uuid: d 49 fe 6 de-cb 32-4 b 96-9891-c 567310 e 59 a 6
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Analytics methods {#analytics-methods}

Hier finden Sie eine Liste der Adobe Analytics-Methoden, die von der iOS-Bibliothek bereitgestellt werden.

Das SDK unterstützt derzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target, Audience Manager und Adobe Experience Platform Identity Service. Methods are prefixed according to the solution. Experience Cloud ID methods are prefixed with `track`.

Jede dieser Methoden wird zum Senden von Daten in Ihre Adobe Analytics Report Suite verwendet.

* **trackState:&#x200B;data:**

   States are the views that are available in your app, such as `home dashboard`, `app settings`, `cart`, and so on. Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `trackState`-Aufrufe inkrementieren die Seitenansichten. If `state` is empty, it displays as *app name app version (build)* in reports. If you see this value in reports, ensure you are setting `state` in each `trackState` call.

   >[!TIP]
   >
   >Dies ist der einzige Verfolgungsaufruf, der Seitenansichten inkrementiert.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void)  trackState:(NSString  *)state
                      data:(NSDictionary  *)data;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile  trackState:@"loginScreen"
                        data:nil]; 
      ````

* **trackAction:&#x200B;data:**

   Verfolgt eine Aktion in der App. Aktionen, die Sie messen möchten, wie z. `logons`B `banner taps`., `feed subscriptions`und andere Metriken, treten in Ihrer App auf.

   >[!TIP]
   >
   >If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      +  (void)  trackAction:(NSString  *)action
                        data:(NSDictionary  *)data; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile  trackAction:@"heroBannerTouched"
                         data:nil]; 
      ```

* **trackingIdentifier**

   Ruft die Analytics-Tracking-ID ab.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (NSString *) trackingIdentifier; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      NSString *trackingId = [ADBMobile trackingIdentifier];
      ```

* **trackActionFromBackground:&#x200B;data:**

   Verfolgt eine Aktion im Hintergrund, wodurch das Auslösen von Lebenszyklusereignissen in bestimmten Szenarios unterdrückt wird.

   >[!TIP]
   >
   >Diese Methode sollte nur in Code aufgerufen werden, der ausgeführt wird, während sich Ihre App im Hintergrund befindet.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
       +  (void)  trackActionFromBackground:(NSString  *)action
                                       data:(NSDictionary  *)data; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile  trackActionFromBackground:@"downloadedUpdate"
                                       data:nil];
      ```

* **trackLocation:&#x200B;data:**

   Sendet die aktuellen XY-Koordinaten. Ermittelt außerdem anhand der in der Datei `ADBMobileConfig.json` definierten Zielpunkte (POIs), ob der als Parameter angegebene Standort in einem vorhandenen Zielpunkt liegt. Falls die aktuellen Koordinaten auf einen definierten Zielpunkt passen, wird eine Kontextdatenvariable gefüllt und zusammen mit dem `trackLocation`-Aufruf gesendet.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      +  (void)  trackLocation:(CLLocation  *)location
                          data:(NSDictionary  *)data; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile  trackLocation:userLocation
                           data:nil]; 
      ```

* **trackBeacon:&#x200B;data:**

   Verfolgt das Eintreten eines Benutzers in den Radius eines Beacons.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      +  (void)  trackLocation:(CLBeacon  *)beacon
                          data:(NSDictionary  *)data;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile  trackBeacon:beacon
                         data:nil];
      ```

* **trackingClearCurrentBeacon**

   Löscht die Beacon-Daten, sobald der Benutzer den Radius des Beacons verlässt.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) trackingClearCurrentBeacon;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile trackingClearCurrentBeacon];
      ```

* **trackLifetimeValueIncrease:&#x200B;data:**

   Erhöht den Lebenszeitwert des Benutzers um `amount`.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
       +  (void)  trackLifetimeValueIncrease:(NSDecimalNumber  *)amount
                                       data:(NSDictionary  *)data; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile  trackLifetimeValueIncrease:30
                                         data:nil];
      ```

* **trackTimedActionStart:&#x200B;data:**

   Startet eine zeitgesteuerte Aktion mit dem Namen `action`. Wenn Sie diese Methode für eine bereits gestartete Methode aufrufen, wird die vorherige zeitgesteuerte Aktion überschrieben.

   >[!TIP]
   >
   >Dieser Aufruf sendet keinen Treffer.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      +  (void)  trackTimedActionStart:(NSString  *)action
                                  data:(NSDictionary  *)data; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile  trackTimedActionStart:@"cartToCheckout"
                                  data:nil]; 
      ```

* **trackTimedActionUpdate:&#x200B;data:**

   Übergibt `data`, mit denen die Kontextdaten für die vorliegende `action` aktualisiert werden sollen. The `data` that is passed in is appended to the existing data for the action, and if the same key is already defined for `action`, overwrites the data.

   >[!TIP]
   >
   >Dieser Aufruf sendet keinen Treffer.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
       +  (void)  trackTimedActionUpdate:(NSString  *)action
                                    data:(NSDictionary  *)data; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile  trackTimedActionUpdate:@"cartToCheckout"
                                    data:@{@"quantity":@"3"}];
      ```

* **trackTimedActionEnd:&#x200B;logic:**

   Beendet eine zeitgesteuerte Aktion. Wenn Sie `block` angeben, haben Sie Zugriff auf die endgültigen Zeitwerte und können `data` vor dem Senden des endgültigen Treffers ändern.

   >[!TIP]
   >
   >If you provide `block`, you must return `YES` to send a hit. Passing in `nil` for `block` sends the final hit.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      +  (void)  trackTimedActionEnd:(NSString  *)action
                          logic:(BOOL  (^)  (NSTimeInterval  inAppDuration,
                                                  NSTimeInterval totalDuration,
                                                  NSMutableDictionary *data))block; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile  trackTimedActionEnd:@"cartToCheckout"
                    logic:^(NSTimeInterval inApp,
                    NSTimeInterval  total,
                    NSMutableDictionary  *data)  {
                        data[@"price"]  =  @"49.95";
                        return  YES;
                    }];
      ```

* **trackingTimedActionExists**

   Gibt zurück, ob derzeit eine zeitgesteuerte Aktion ausgeführt wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (BOOL) trackingTimedActionExists:(NSString *)action;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      BOOL *actionExists = [ADBMobile trackingTimedActionExists];
      ```

* **trackingSendQueuedHits**

   Erfordert SDK 4.1. Unabhängig davon, wie viele Treffer derzeit in die Warteschlange gestellt werden, erzwingt die Bibliothek alle Treffer in der Offline-Warteschlange.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) trackingSendQueuedHits;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile trackingSendQueuedHits]; 
      ```

* **trackingGetQueueSize**

   Ruft die Anzahl der Zugriffe ab, die sich derzeit in der Offline-Warteschlange befinden.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
       + (NSUInteger) trackingGetQueueSize;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      NSUInteger *queueSize = [ADBMobile trackingGetQueueSize];
      ```

* **trackingClearQueue**

   Löscht alle Zugriffe aus der Offline-Warteschlange.

   >[!CAUTION]
   >
   >Gehen Sie beim manuellen Leeren der Warteschlange vorsichtig vor. Dieser Vorgang kann nicht rückgängig gemacht werden.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) trackingClearQueue;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile trackingClearQueue]; 
      ```



* **trackPushMessageClickThrough**

   Verfolgt die Clickthrough-Rate bei Push-Nachrichten.

   >[!IMPORTANT]
   >
   >Diese Methode erhöht keine Seitenansichten.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) trackPushMessageClickThrough:(NSDictionary *)userInfo;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      -  (void)application:(UIApplication  *)application  
      didReceiveRemoteNotification:(NSDictionary  *)userInfo  
      fetchCompletionHandler:(void  (^)
      (UIBackgroundFetchResult))completionHandler  {
          // only send the hit if the app is not active
          if (application.applicationState !=  UIApplicationStateActive)  {
              [ADBMobile  trackPushMessageClickThrough:userInfo];
      
          }
          completionHandler(UIBackgroundFetchResultNoData);
      }
      ```
