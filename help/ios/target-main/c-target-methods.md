---
description: Hier finden Sie die Liste der Adobe Target-Methoden, die von der iOS-Bibliothek bereitgestellt werden.
solution: Experience Cloud,Analytics
title: Target-Methoden für iOS
topic-fix: Developer and implementation
uuid: 692bcda1-02ba-4902-bd65-15888adf1952
exl-id: ba03f865-970c-4b48-af35-749f05b273d8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 95%

---

# Target-Methoden für iOS {#target-methods}

Hier finden Sie die Liste der Adobe Target-Methoden, die von der iOS-Bibliothek bereitgestellt werden.

Das SDK unterstützt zurzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target, Audience Manager und Identity-Dienst für Adobe Experience Platform. Methoden erhalten je nach Lösung unterschiedliche Präfixe. Zum Beispiel weisen -Methoden das Präfix `target` target auf.

>[!TIP]
>
>Lebenszyklusmetriken werden als Parameter jeder mbox-Load gesendet. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/ios/metrics.md). Wenn Sie Target-Anforderungen innerhalb der „delegate“-Methode `didFinishLaunching` senden, fügen Sie vor dem Target-Implementierungscode einen `[ADBMobile trackAction:data:]`- oder `[ADBMobile trackState:data:]`-Aufruf hinzu. Auf diese Weise enthalten die Target-Anforderungen die vollständigen Lebenszyklusdaten.

## Class reference: ADBTargetLocationRequest

### Eigenschaften

```objective-c
NSString *name; 
NSString *defaultContent; 
NSMutableDictionary *parameters;
```

### Zeichenfolgenkonstanten

>[!TIP]
>
>Die folgenden Konstanten helfen Ihnen beim Festlegen von Schlüsseln für benutzerdefinierte Parameter.

```iOS
NSString *const ADBTargetParameterOrderId; 
NSString *const ADBTargetParameterOrderTotal; 
NSString *const ADBTargetParameterProductPurchasedId; 
NSString *const ADBTargetParameterCategoryId; 
NSString *const ADBTargetParameterMbox3rdPartyId; 
NSString *const ADBTargetParameterMboxPageValue; 
NSString *const ADBTargetParameterMboxPc; 
NSString *const ADBTargetParameterMboxSessionId; 
NSString *const ADBTargetParameterMboxHost;
```

>[!IMPORTANT]
>
>* Wenn Sie SDK **vor** Version 4.14.0 verwenden, finden Sie die Parameterbeschränkungen unter [Eingabeparameter](https://developers.adobetarget.com/api/#input-parameters).
>
>* Wenn Sie SDK der Version 4.14.0 **oder später** verwenden, finden Sie die Parameterbeschränkungen unter [Batch-Eingabeparameter](https://developers.adobetarget.com/api/#batch-input-parameters).


### Methoden

* **targetLoadRequest:&#x200B;callback**

   Sendet Anforderungen an Ihren konfigurierten Target-Server und gibt den Zeichenfolgenwert des Angebots zurück, der in einem Block-`callback` generiert wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) targetLoadRequest:(ADBTargetLocationRequest *)request
                        callback:(void (^)(NSString *content))callback;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile targetLoadRequest:myRequest
                          callback:^(NSString *content) {
                            // do something with content
                          }];
      ```

* **:defaultContent::orderParameters::requestLocationParameters:targetLoadRequestWithNameprofileParameterssmboxParameter scallback:**

   Sendet eine Anforderung an Ihren konfigurierten Target-Server und gibt den Zeichenfolgenwert des Angebots zurück, der in einem Block-Callback generiert wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) targetLoadRequestWithName:(nullable NSString *)name
                          defaultContent:(nullable NSString *)defaultContent
                      profileParameters:(nullable NSDictionary *)profileParameters
                        orderParameters:(nullable NSDictionary *)orderParameters
                         mboxParameters:(nullable NSDictionary *)mboxParameters
                requestLocationParameters:(nullable NSDictionary *)requestLocationParameters
                                 callback:(nullable void (^)(NSString
                                 * __nullable content))callback;
      ```

   * Gibt Folgendes zurück: N/A

   * Hier finden Sie die Parameter für diese Methode:

      * **`name`**

         Name der/des Target-mbox/-Standorts, die/den Sie empfangen wollen.

         * **Typ**: NSString*
      * **`defaultContent`**

         Wert, der im Rückruf zurückgegeben wird, wenn der Target-Server nicht erreichbar ist oder der Benutzer nicht für die Kampagne infrage kommt.

         * **Typ**: NSString*
      * **`profileParameters`**

         Werte in diesem Wörterbuch werden in das Objekt „profileParameters“ in der Anforderung zu Target versetzt.

         * **Typ**: NSDictionary*
      * **`orderParameters`**

         Werte in diesem Wörterbuch werden in das Objekt „order“ in der Anforderung zu Target versetzt.

         * **Typ**: NSDictionary
      * **`mboxParameters`**

         Werte in diesem Wörterbuch werden in das Objekt „mboxParameters“ in der Anforderung zu Target versetzt.

         * **Typ**: NSDictionary*
      * **`requestLocationParameters`**

         Werte in diesem Wörterbuch werden in das Objekt „requestLocation“ in der Anforderung zu Target versetzt.

         **Typ**: NSDictionary*

      * **`callback`**

         Diese Methode wird mit dem Inhalt des Angebots vom Target-Server aufgerufen. Wenn der Target-Server nicht erreicht werden kann oder der Benutzer nicht für die Kampagne qualifiziert ist, wird defaultContent zurückgegeben.
      **Typ**: Funktion

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile targetLoadRequestWithName:@"myHeroBanner"
                            defaultContent:@"defaultHeroBanner.png"
                        profileParameters:@{@"age":@"20-29"}
                          orderParameters:nil
                           mboxParameters:@{@"customParam":@"customValue"}
                requestLocationParameters:@{@"host":@"my.hostname.com"}
                                 callback:^(NSString *content){
                                   // do something with content
                                   myImageView.image = [UIImage imageNamed:content];
                                 }];
      ```

      Weitere Informationen zur zugrunde liegenden Target-API finden Sie in der [Target-API-Referenz](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-target/target-api-reference-deprecated).







* **:defaultContent::orderParameters:targetLoadRequestWithNameprofileParameterssmboxParameters:callback**

   Sendet request an Ihren konfigurierten Target-Server und gibt den Zeichenfolgenwert des in einem Block-Callback generierten Angebots zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) targetLoadRequestWithName:(nullable NSString *)name
                          defaultContent:(nullable NSString *)defaultContent
                      profileParameters:(nullable NSDictionary *)profileParameters
                        orderParameters:(nullable NSDictionary *)orderParameters
                         mboxParameters:(nullable NSDictionary *)mboxParameters
                               callback:(nullable void (^)(NSString * __nullable content))callback;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile targetLoadRequestWithName:@"mboxName"
                            defaultContent:@"defaultContent"
                         profileParameters:{@"profile-parameter-key": @"profile-parameter-value"}
                           orderParameters:@{@"order-parameter-key": @"order-parameter-value"}
                            mboxParameters:@{@"mbox-parameter-key": @"mbox-parameter-value"}
                                   callback:^(NSString * content) {
                                           //do something with content 
                                 }
                               }];
      ```

* **targetCreateOrder&#x200B;ConfirmRequestWithName:&#x200B;orderId:&#x200B;orderTotal:&#x200B;productPurchasedId:&#x200B;parameters**

   Erstellt ein `ADBTargetLocationRequest`-Objekt.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (ADBTargetLocationRequest *)
      targetCreateOrderConfirmRequestWithName:(NSString *)name
                                      orderId:(NSString *)orderId
                                  orderTotal:(NSString *)orderTotal
                          productPurchasedId:(NSString *)productPurchasedId
                              parameters:(NSDictionary *)parameters;
      ```

* **targetCreateRequestWithName:&#x200B;&#x200B;defaultContent:&#x200B;parameters**

   Vordefinierter Konstruktor zum Erzeugen eines ADBTargetLocationRequest-Objekts mit den angegebenen Parametern.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (ADBTargetLocationRequest *)
      targetCreateRequestWithName:(NSString *)name
                           defaultContent:(NSString *)defaultContent
                               parameters:(NSDictionary *)parameters;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBTargetLocationRequest *myRequest =  
      [ADBMobile targetCreateRequestWithName:@"heroBanner"
                              defaultContent:@"default.png"
                                  parameters:nil];
      ```

* **targetThirdPartyID**

   Gibt die Drittanbieter-ID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (nullable NSString *) targetThirdPartyID;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      NSString *thirdPartyId = [ADBMobile targetThirdPartyID];
      ```

* **targetSetThirdPartyID**

   Legt die Drittanbieter-ID fest.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) targetSetThirdPartyID:(nullable NSString *)thirdPartyID;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile targetSetThirdPartyID:@"thirdPartyID"];
      ```

* **targetClearCookies**

   Löscht alle Ziel-Cookies aus der App.

   >[!TIP]
   >
   >Seit Version 4.10.0 des SDK werden von Target keine Cookies mehr verwendet. Durch diese Methode werden thirdPartyID und sessionID zurückgesetzt.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) targetClearCookies;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile targetClearCookies];
      ```

* **targetPcID**

   Gibt die PcID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (nullable NSString *) targetPcID;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      NSString *myTargetPcID = [ADBMobile targetPcID];
      ```

* **targetSessionID**

   Gibt die SessionID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (nullable NSString *) targetPcID;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      NSString *myTargetSessionID = [ADBMobile targetSessionID];
      ```

### Beispiel

```objective-c
// make your request 
ADBTargetLocationRequest *myRequest =  
 [ADBMobile targetCreateRequestWithName:@"heroBanner"  
                         defaultContent:@"default.png"  
                          parameters:nil]; 
// load your request 
[ADBMobile targetLoadRequest:myRequest  
                    callback:^(NSString *content) { 
                        // do something with content 
                        heroImage.image = [UIImage imageNamed:content];
                    }];
```
