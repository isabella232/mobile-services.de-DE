---
description: Hier finden Sie die Identity-Dienst-Methoden für Adobe Experience Platform, die von der iOS-Bibliothek bereitgestellt werden.
seo-description: Hier finden Sie die Identity-Dienst-Methoden für Adobe Experience Platform, die von der iOS-Bibliothek bereitgestellt werden.
seo-title: Identity-Dienst-Methoden für Adobe Experience Platform
solution: Marketing Cloud,Analytics
title: Identity-Dienst-Methoden für Adobe Experience Platform
topic: Developer and implementation
uuid: cdd307bc-8b7d-47a8-b77e-00902b9e2968
translation-type: ht
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa
workflow-type: ht
source-wordcount: '461'
ht-degree: 100%

---


# Identity-Dienst-Methoden für Adobe Experience Platform {#experience-cloud-id-service-methods}

Hier finden Sie die Identity-Dienst-Methoden für Adobe Experience Platform, die von der iOS-Bibliothek bereitgestellt werden.

Das SDK unterstützt zurzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target, Audience Manager und des Experience Cloud-Besucher-ID-Service.

Methoden erhalten je nach Lösung unterschiedliche Präfixe. Experience Cloud ID-Methoden erhalten beispielsweise das Präfix `visitor`. Weitere Informationen finden Sie im Thema über das [Aktivieren der Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md).

* **`+`(nullable NSURL`*`)visitorAppendToURL:(nullable NSURL`*`)url;**

   Hängt die Adobe-Besucherdaten an eine URL-Zeichenfolge zur Verwendung mit der Adobe-JavaScript-Bibliothek an. Zum Verwenden dieser Methode müssen Sie über Mobile SDK-Version 4.12 oder höher verfügen. Weitere Informationen finden Sie unter [Hilfefunktion zum Anhängen der Besucher-ID](https://docs.adobe.com/content/help/de-DE/id-service/using/id-service-api/methods/appendvisitorid.html).

   >[!IMPORTANT]
   >
   >Diese Methode kann einen blockierenden Netzwerkaufruf verursachen. Rufen Sie diese Methode nicht in zeitkritischen Threads auf.

   * Eingabe: `URL<NSURL>`
Eine erforderliche URL-Zeichenfolge, an die die Besucherinformationen angehängt werden.
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
      >Diese Methode kann zu einem blockierenden Netzwerkaufruf führen und sollte **NICHT** über einen UI-Thread aufgerufen werden.

* **visitorSyncIdentifiers:**

   Mit der Experience Cloud-ID können Sie zusätzliche Kunden-IDs festlegen, die jedem Besucher zugeordnet werden können. Die Besucher-API akzeptiert mehrere Kunden-IDs für denselben Besucher sowie eine Kundentypkennung, die den Umfang der einzelnen Kunden-IDs abgrenzt. Diese Methode entspricht `setCustomerIDs` in der JavaScript-Bibliothek.

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

   Synchronisiert den bereitgestellten ID-Typ und -Wert mit dem ID-Service. Übergeben Sie `authState` als einen der folgenden Werte:

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

* **visitorgetUrlVariablesAsync**

   Diese in Version 4.16.0 eingeführte Methode gibt eine entsprechend geformte Zeichenfolge zurück, die URL-Variablen des Besucher-ID-Dienst enthält. Weitere Informationen zur Verwendung dieser Methode finden Sie unter [Identity-Dienst-Methoden für Adobe Experience Platform](/help/ios/reference/hybrid-app.md).

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

## ADBMobileVisitorAuthenticationState enum  {#section_A55A3F336DDF4F838900632087F51430}

```objective-c
ADBMobileVisitorAuthenticationStateUnknown, 
ADBMobileVisitorAuthenticationStateAuthenticated, 
ADBMobileVisitorAuthenticationStateLoggedOut
```

