---
description: Hier finden Sie eine Liste der Adobe Analytics-Methoden, die von der iOS-Bibliothek bereitgestellt werden.
seo-description: Hier finden Sie eine Liste der Adobe Analytics-Methoden, die von der iOS-Bibliothek bereitgestellt werden.
seo-title: Analytics-Methoden
solution: Marketing Cloud,Analytics
title: Analytics-Methoden
topic: Developer and implementation
uuid: d49fe6de-cb32-4b96-9891-c567310e59a6
translation-type: tm+mt
source-git-commit: 82c8e82ce5ce333c2482252e96f928829d322e7e

---


# Analytics-Methoden {#analytics-methods}

Hier finden Sie eine Liste der Adobe Analytics-Methoden, die von der iOS-Bibliothek bereitgestellt werden.

Das SDK unterstützt zurzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target, Audience Manager und Identity-Dienst für Adobe Experience Platform. Methoden erhalten je nach Lösung unterschiedliche Präfixe. Experience Cloud ID-Methoden erhalten beispielsweise das Präfix `track`.

Jede dieser Methoden wird zum Senden von Daten in Ihre Adobe Analytics Report Suite verwendet.

* **trackState:&#x200B;data:**

   Die Statusangaben entsprechen den verfügbaren Ansichten in der App, z. B. `home dashboard`, `app settings` und `cart`. Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `trackState`-Aufrufe inkrementieren die Seitenansichten. Wenn `state` leer ist, wird in Berichten *App-Name App-Version (Build)* angezeigt. Wenn dieser Wert in einem Bericht auftritt, müssen Sie den Status `state` in jedem `trackState`-Aufruf festlegen.

   >[!TIP]
   >
   >Dies ist der einzige Verfolgungsaufruf, bei dem die Seitenansichten inkrementiert werden.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void)  trackState:(NSString  *)state
                      data:(NSDictionary  *)data;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile  trackState:@"loginScreen"
                        data:nil]; 
      ```

* **trackAction:&#x200B;data:**

   Verfolgt eine Aktion in der App. Aktionen, die Sie messen möchten, wie z. B. `logons`, `banner taps`, `feed subscriptions` und andere Metriken, die in Ihrer App auftreten.

   >[!TIP]
   >
   >Falls Code aktiv ist, während die App im Hintergrund ausgeführt wird (z. B. Datenabruf im Hintergrund), verwenden Sie stattdessen `trackActionFromBackground`.

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
   >Diese Methode sollte nur in Code aufgerufen werden, der aktiv ist, während die App im Hintergrund ausgeführt wird.

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

   Übergibt `data`, mit denen die Kontextdaten für die vorliegende `action` aktualisiert werden sollen. Die übergebenen Daten (`data`) werden an die vorhandenen Daten für die Aktion angehängt und wenn der Schlüssel bereits für `action` definiert ist, werden die Daten überschrieben.

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
   >Wenn Sie `block` angeben, müssen Sie `YES` zurückgeben, um einen Treffer zu senden. Wenn Sie `nil` für `block` übergeben, wird der endgültige Treffer gesendet.

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

   Erfordert SDK 4.1. Unabhängig davon, wie viele Treffer sich derzeit in der Warteschlange befinden, wird erzwungen, dass die Bibliothek alle Treffer in der Offline-Warteschlange sendet.

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
   >Gehen Sie beim manuellen Löschen der Warteschlange vorsichtig vor. Dieser Vorgang kann nicht rückgängig gemacht werden.

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
   >Bei dieser Methode werden die Seitenansichten nicht inkrementiert.

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
