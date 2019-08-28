---
description: Im Folgenden finden Sie die Methoden für den Identitätsdienst von Adobe Experience Platform, die von der ios-Bibliothek bereitgestellt werden.
seo-description: Im Folgenden finden Sie die Methoden für den Identitätsdienst von Adobe Experience Platform, die von der ios-Bibliothek bereitgestellt werden.
seo-title: Methoden des Adobe Experience Platform Identity Service
solution: Marketing Cloud, Analytics
title: Methoden des Adobe Experience Platform Identity Service
topic: Entwickler und Implementierung
uuid: cdd 307 bc -8 b 7 d -47 a 8-b 77 e -00902 b 9 e 2968
translation-type: tm+mt
source-git-commit: cbbb85b4d117fcaa502a1e01423f1f5d3b2ecc2b

---


# Methoden des Adobe Experience Platform Identity Service {#experience-cloud-id-service-methods}

Im Folgenden finden Sie die Methoden für den Identitätsdienst von Adobe Experience Platform, die von der ios-Bibliothek bereitgestellt werden.

Das SDK unterstützt zurzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target, Audience Manager und des Experience Cloud-Besucher-ID-Service.

Methods are prefixed according to the solution, and Experience Cloud ID methods are prefixed with `visitor`. Weitere Informationen finden Sie im Thema über das [Aktivieren der Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md).

* **`+`(nullable NSURL`*`) visitorappendtourl: (nullable NSURL`*`) url;**

   Hängt die Adobe-Besucherdaten an eine URL-Zeichenfolge zur Verwendung mit der Adobe-JavaScript-Bibliothek an. Für die Verwendung dieser Methode muss Mobile SDK Version 4.12 oder höher verwendet werden. Weitere Informationen finden Sie unter [Hilfefunktion zum Anhängen der Besucher-ID](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-appendvisitorid.html).

   >[!IMPORTANT]
   >
   >Diese Methode kann einen blockierten Netzwerkaufruf verursachen. Rufen Sie diese Methode nicht in zeitkritischen Threads auf.

   * Input: `URL<NSURL>`
A required URL string that the visitor information will be appended to.
   * `URL<NSURL>`
Zeichenfolge mit angehängten Besucherinformationen.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
       NSURL *url = [NSURL URLWithString:@"https://www.example.com"];  
       NSURL *decoratedURL = [ADBMobile visitorAppendToURL: url];  
       [[UIApplication sharedApplication] openURL: decoratedURL];  
      ```

* **visitorMarketingCloudID**

   Ruft die Experience Cloud ID vom ID-Service ab.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (NSString  *)  visitorMarketingCloudID;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      NSString *mcid = [ADBMobile visitorMarketingCloudID]; 
      ```

      >[!IMPORTANT]
      >
      >This method can cause a blocking network call and should **not** be called from a UI thread.

* **visitorSyncIdentifiers:**

   Mit der Experience Cloud ID können Sie zusätzliche Kunden-IDs festlegen, die Besuchern zugewiesen werden können. Die Besucher-API akzeptiert mehrere Kunden-IDs für denselben Besucher sowie eine Kundentypkennung, die den Umfang der einzelnen Kunden-IDs abgrenzt. Diese Methode entspricht `setCustomerIDs` in der JavaScript-Bibliothek.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      +  (void)  visitorSyncIdentifiers:(NSDictionary  *)identifiers;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"idType":@"idValue"}];
      ```

* **visitorSyncIdentifiers:authenticationState:**

   Synchronisiert die bereitgestellten IDs mit dem ID-Service. Übergeben Sie `authState` als einen der folgenden Werte:

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      +  (void) visitorSyncIdentifiers:(nullable NSDictionary  *)identifiers  authenticationState:(ADBMobileVisitorAuthenticationState)authState; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"myIdType":@"valueForUser"}  authenticationState:ADBMobileVisitorAuthenticationStateAuthenticated]; 
      ```

* **visitorSyncIdentifierWithType:identifier:authenticationState:**

   Synchronisiert den bereitgestellten ID-Typ und -Wert mit dem ID-Service. Pass in the `authState` one of the following values:

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) visitorSyncIdentifierWithType:(nullable NSString *)identifierType  
      identifier:(nullable NSString *)identifier authenticationState:
      (ADBMobileVisitorAuthenticationState)authState; 
      ```

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      [ADBMobile visitorSyncIdentifierWithType:@"myIdType" identifier:@"valueForUser"  
      authenticationState:ADBMobileVisitorAuthenticationStateLoggedOut]; 
      ```

* **visitorGetIDs**

   Ruft ein Array schreibgeschützter `ADBVisitorID`-Objekte ab.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      +  (nullable NSArray *) visitorGetIDs;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      NSArray *myVisitorIDs = [ADBMobile visitorGetIDs];
      ```

* **Visitorgeturlvariablesasync**

   Diese Methode wird in Version 4.16.0 eingeführt und gibt eine korrekt formatierte Zeichenfolge zurück, die URL-Variablen des Besucher-ID-Service enthält. Weitere Informationen zur Verwendung dieser Methode finden Sie unter Methoden des [Adobe Experience Platform Identity Service](/help/ios/reference/hybrid-app.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```objectivec
      + (void) visitorGetUrlVariablesAsync:(nullable void (^)(NSString* __nullable urlVariables))callback;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objectivec
      NSString *urlString = @"https://www.mydomain.com/index.php"; 
      [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
        NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
        // use urlStringWithVisitorData 
      }];
      ```

## ADBVisitorID-Schnittstelle {#section_2FF74454D25C4ADABAC5E43CBFAAEC26}

**Öffentliche Methoden:**

```objective-c
- (nullable NSString *) idType; 
- (nullable NSString *) identifier; 
- (ADBMobileVisitorAuthenticationState) authenticationState; 
```

## ADBMobileVisitorAuthenticationState enum {#section_A55A3F336DDF4F838900632087F51430}

```objective-c
ADBMobileVisitorAuthenticationStateUnknown, 
ADBMobileVisitorAuthenticationStateAuthenticated, 
ADBMobileVisitorAuthenticationStateLoggedOut
```

