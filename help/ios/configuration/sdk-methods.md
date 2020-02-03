---
description: Hier finden Sie eine Liste der Methoden, die von der iOS-Bibliothek bereitgestellt werden.
seo-description: Hier finden Sie eine Liste der Methoden, die von der iOS-Bibliothek bereitgestellt werden.
seo-title: Konfigurationsmethoden
solution: Marketing Cloud,Analytics
title: Konfigurationsmethoden
topic: Developer and implementation
uuid: 623c7b07-fbb3-4d39-a5c4-e64faec4ca29
translation-type: tm+mt
source-git-commit: ea4b054fbeea3967c28ee938aed5997a4c287a0d

---


# Konfigurationsmethoden {#configuration-methods}

Hier finden Sie eine Liste der Methoden, die von der iOS-Bibliothek bereitgestellt werden.

Das SDK unterstützt zurzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target, Audience Manager und Identity-Dienst für Adobe Experience Platform.

* **setAppExtensionType**

   Konfiguriert die Adobe Mobile-SDK-Einstellung, um zu bestimmen, welcher Erweiterungstyp aktuell ausgeführt wird.

   Die folgenden Werte sind zulässig:
   * `ADBMobileAppExtensionTypeRegular`: Erweiterung wird mit einer übergeordneten App gepackt.
   * `ADBMobileAppExtensionTypeStandAlone`: Erweiterung wird nicht mit einer übergeordneten App gepackt.
   >[!TIP]
   >
   >Diese Methode sollte **nur** verwendet werden, wenn Ihre App eine Erweiterung oder eine eigenständige Erweiterung aufweist. Weitere Informationen finden Sie unten unter *ADBMobileAppExtensionType*.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) setAppExtensionType:(ADBMobileAppExtensionType)type;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone]; 
      ```



* **version**

   Gibt die aktuelle Version der Adobe Mobile-Bibliothek zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      +(NSString*) version;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      NSString*libraryVersion = [ADBMobileversion];
      ```

* **privacyStatus**

   Gibt die Enum-Darstellung für den Datenschutzstatus des aktuellen Benutzers zurück:

   * `ADBMobilePrivacyStatusOptIn`: Treffer werden umgehend gesendet.
   * `ADBMobilePrivacyStatusOptOut` - werden Treffer verworfen.
   * `ADBMobilePrivacyStatusUnknown`: Bei aktivierter Offline-Verfolgung werden die Treffer so lange gespeichert, bis sich der Datenschutzstatus in „opt-in“ (anschließend werden die Treffer gesendet) oder „opt-out“ (anschließend werden die Treffer verworfen) ändert. Ist die Offline-Verfolgung nicht aktiviert, werden die Zugriffe verworfen, bis der Datenschutzstatus zu „opt-in“ geändert wird. 
Der Standardwert wird in der Datei `ADBMobileConfig.json` festgelegt.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (ADBMobilePrivacyStatus) privacyStatus;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobilePrivacyStatus privacyStatus = [ADBMobileprivacyStatus];
      ```

* **setPrivacyStatus**

   Legt für den aktuellen Benutzer den Datenschutzstatus `status` fest.

   Die folgenden Werte sind zulässig:

   * `ADBMobilePrivacyStatusOptIn`: Treffer werden umgehend gesendet.
   * `ADBMobilePrivacyStatusOptOut` - werden Treffer verworfen.
   * `ADBMobilePrivacyStatusUnknown`: Bei aktivierter Offline-Verfolgung werden die Treffer so lange gespeichert, bis sich der Datenschutzstatus in „opt-in“ (anschließend werden die Treffer gesendet) oder „opt-out“ (anschließend werden die Treffer verworfen) ändert. Ist die Offline-Verfolgung nicht aktiviert, werden die Zugriffe verworfen, bis der Datenschutzstatus zu „opt-in“ geändert wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) setPrivacyStatus:(ADBMobilePrivacyStatus)status;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn];
      ```

* **lifetimeValue**

   Gibt den Lebenszeitwert für den aktuellen Benutzer zurück. Der Standardwert lautet `0`.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (NSDecimalNumber *) lifetimeValue;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      NSDecimalNumber *lifeValue = [ADBMobile lifetimeValue];
      ```

* **trackingIdentifier**

   Gibt die automatisch generierte Besucher-ID zurück. Hierbei handelt es sich um eine App-spezifische Unique Visitor-ID, die von den Adobe-Servern generiert wird. Wenn die Adobe-Server zum Zeitpunkt der Generierung nicht erreicht werden können, wird die ID mithilfe der CFUUID von Apple generiert. Der Wert wird beim ersten Start generiert, dann gespeichert und von diesem Zeitpunkt an verwendet. Diese ID wird zwischen App-Upgrades beibehalten. Sie wird gespeichert und während des Standardanwendungs-Backup-Vorgangs wiederhergestellt und bei der Deinstallation entfernt.

   >[!TIP]
   >
   >Wenn für Ihre App ein Upgrade vom Experience Cloud-SDK 3.x auf 4.x vorgenommen wird, wird die vorherige benutzerdefinierte oder automatisch generierte Besucher-ID abgerufen und als die benutzerdefinierte Benutzer-ID gespeichert. Weitere Informationen finden Sie unten in der Zeile `userIdentifier`. Dadurch werden Besucherdaten zwischen SDK-Upgrades beibehalten. Für neue Installationen für das SDK der Version 4.x lautet die Benutzer-ID `nil` und die Tracking-ID wird verwendet.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (NSString *) trackingIdentifier;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      NSString *tid = [ADBMobile trackingIdentifier];
      ```

* **userIdentifier**

   Wurde eine benutzerdefinierte ID festgelegt, wird die Benutzer-ID zurückgegeben. Wird keine benutzerdefinierte ID festgelegt, wird der Wert `nil` zurückgegeben. Der Standardwert lautet `nil`.

   >[!TIP]
   >
   >Wenn für Ihre App ein Upgrade vom Experience Cloud-SDK 3.x auf 4.x vorgenommen wird, wird die vorherige benutzerdefinierte oder automatisch generierte Besucher-ID abgerufen und als die benutzerdefinierte Benutzer-ID gespeichert. Dadurch werden Besucherdaten zwischen SDK-Upgrades beibehalten.

   Bei neuen Installationen der SDK-Version 4.x lautet die Benutzer-ID `nil`, bis sie festgelegt wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      +(NSString *) userIdentifier;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      NSString *uid = [ADBMobileuserIdentifier];
      ```

* **setUserIdentifier**

   Legt die Benutzerkennung auf `identifier` fest.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      +(void)setUserIdentifier:(NSString*)identifier;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile setUserIdentifier:@"billybob"]; 
      ```

* **debugLogging**

   Gibt die aktuelle Vorgabe für die Debug-Protokollierung zurück. Der Standardwert lautet `NO`.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (BOOL) debugLogging;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      BOOL debugging = [ADBMobile debugLogging];
      ```

* **setDebugLogging**

   Legt die Debug-Protokollierungseinstellung auf `debug` fest.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) setDebugLogging:(BOOL)debug;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile setDebugLogging:YES];
      ```

* **keepLifecycleSessionAlive**

   Gibt dem SDK gegenüber an, dass beim nächsten Fortsetzen aus der Ausführung im Hintergrund keine neue Sitzung gestartet werden soll, unabhängig vom Wert für den Lebenszyklussitzungs-Timeout in der Konfigurationsdatei.

   >[!TIP]
   >
   >Diese Methode ist für Apps vorgesehen, die sich für Benachrichtigungen während der Ausführung im Hintergrund registrieren und die nur aus dem Code heraus aufgerufen werden sollen, der aktiv ist, wenn die App im Hintergrund ausgeführt wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) keepLifecycleSessionAlive;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile keepLifecycleSessionAlive]; 
      ```

* **collectLifecycleData**

   Gibt dem SDK gegenüber an, dass Lebenszyklusdaten für die Nutzung aller Lösungen im SDK erfasst werden sollen. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/ios/metrics.md).

   >[!TIP]
   >
   >Der bevorzugte Speicherort zum Abrufen dieser Methode lautet `application:didFinishLaunchingWithOptions:`.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) collectLifecycleData;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile collectLifecycleData];
      ```

* **collectLifecycleDataWithAdditionalData:**

   Ermöglicht Ihnen die Weitergabe zusätzlicher Daten beim Erfassen von Lebenszyklusmetriken.

   Diese Methode muss vom Einstiegspunkt Ihrer App aufgerufen werden. Dies umfasst ggf. eine oder beide der Methoden `application:didFinishLaunchingWithOptions:` bzw. `applicationWillEnterForeground:` in Ihrer Klasse „AppDelegate“.

   >[!IMPORTANT]
   >
   >Daten, die über `collectLifecycleDataWithAdditionalData:` an das SDK weitergeleitet werden, bestehen unter `NSUserDefaults` im SDK fort. Das SDK entfernt die Werte im Parameter `NSDictionary`, die nicht vom Typ `NSString` oder `NSNumber` sind. Um `collectLifecycleDataWithAdditionalData:` zu nutzen, ist SDK-**Version 4.4** oder höher erforderlich.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) collectLifecycleDataWithAdditionalData:(nullableNSDictionary*)data; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile collectLifecycleDataWithAdditionalData:@{@"entryType":@"appShortcutIcon"}]; 
      ```

* **pauseCollectingLifecycleData**

   Verwenden Sie diese API, um die Erfassung von Lebenszyklusdaten anzuhalten. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/ios/metrics.md).

   >[!IMPORTANT]
   >
   >In der `applicationDidEnterBackground` Delegate-Methode müssen Sie zuerst die `pauseCollectingLifecycleData` Methode aufrufen.
   >
   >Die API wird bereitgestellt, um das Problem auf iPhone 7/7 oder älteren Geräten mit iOS 13 zu beheben, bei denen die Metrik zur Sitzungslänge abnorm wurde. Dies ist auf einige unbekannte Änderungen zurückzuführen, die in iOS 13 vorgenommen wurden, wobei iOS nicht genügend Zeit lässt, um die Hintergrundaufgabe abzuschließen, wenn Sie die App mit einem Hintergrund erstellt haben.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) pauseCollectingLifecycleData;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      - (void)applicationDidEnterBackground:(UIApplication *)application{
          // manually stop the lifecycle of SDK
          // important: do NOT call any track state or track action after this line
          [ADBMobile pauseCollectingLifecycleData];   
      
      
          // the following code is optional, may help to mitigate the issue a bit more. If you have other logic to run here that probably takes more than 10ms, then there is no need to add this line of code.
          [NSThread sleepForTimeInterval:0.01];
      
      
          // app's code to handle applicationDidEnterBackground
      }
      ```


* **overrideConfigPath**

   Sie können beim Starten der Anwendung eine andere ADBMobile JSON-Konfigurationsdatei laden. Die andere Konfiguration wird verwendet, bis die Anwendung geschlossen wird.

   >[!IMPORTANT]
   >
   >Um `overrideConfigPath` zu nutzen, ist SDK-Version 4.2 oder höher erforderlich.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
       + (void) overrideConfigPath: (nullableNSString *) path;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
      [ADBMobile overrideConfigPath:filePath];
      ```

* **setPushIdentifier**

   Legt das Geräte-Token für Push-Benachrichtigungen fest.

   >[!IMPORTANT]
   >
   >Dieses Verfahren kann nur in der Methode `application:didRegisterForRemoteNotificationsWithDeviceToken:`verwendet werden.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) setPushIdentifier:(NSData *)deviceToken;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      - (void) application:(UIApplication *) application  didRegisterForRemoteNotificationsWithDeviceToken:(NSData *)deviceToken { 
      [ADBMobile setPushIdentifier:deviceToken];  
      }
      ```

* **setAdvertisingIdentifier**

   Legt den IDFA im SDK fest. Wurde der IDFA im SDK eingerichtet, wird er im Lebenszyklus übermittelt. Auf ihn kann auch in Signalen (Postbacks) zugegriffen werden.

   >[!TIP]
   >
   >Rufen Sie den IDFA **nur** dann aus den Apple-APIs ab, wenn Sie einen Dienst für Werbeanzeigen verwenden. Wenn Sie den IDFA abrufen und ihn nicht richtig verwenden, wird Ihre App ggf. abgelehnt.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      +(void) setAdvertisingIdentifier:(NSString*)identifier;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      NSString *idfa = [[[ASIdentifierManager sharedManager]advertisingIdentifier] UUIDString]; 
      [ADBMobile setAdvertisingIdentifier:idfa]; 
      ```

## ADBMobileAppExtensionType enum {#section_18DB491D0ABC4765BB5A467D8FEF4F1B}

```objective-c
/** 
 * @brief An enum type. 
 * The possible types of app extension you might use 
 * @see setAppExtensionType 
 */ 
typedef NS_ENUM(NSUInteger, ADBMobileAppExtensionType) { 
    ADBMobileAppExtensionTypeRegular = 0, /*!< Enum value ADBMobileAppExtensionTypeRegular. */ 
    ADBMobileAppExtensionTypeStandAlone = 1 /*!< Enum value ADBMobileAppExtensionTypeStandAlone. */ 
};
```

