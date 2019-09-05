---
description: Hier finden Sie die Liste der Adobe Target-Methoden, die von der iOS-Bibliothek bereitgestellt werden.
seo-description: Hier finden Sie die Liste der Adobe Target-Methoden, die von der iOS-Bibliothek bereitgestellt werden.
seo-title: Ios-Zielmethoden für Adobe Mobile Services
solution: Marketing Cloud, Analytics
title: Zielmethoden für ios
topic: Entwickler und Implementierung
uuid: 692 bcda 1-02 ba -4902-bd 65-15888 adf 1952
translation-type: tm+mt
source-git-commit: 8dc075603544aaab7fdedb1ff10a12f7fa7e21f5

---


# Target-Methoden für ios {#target-methods}

Hier finden Sie die Liste der Adobe Target-Methoden, die von der iOS-Bibliothek bereitgestellt werden.

Das SDK unterstützt derzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target, Audience Manager und Adobe Experience Platform Identity Service. Methoden erhalten je nach Lösung unterschiedliche Präfixe. Zum Beispiel weisen -Methoden das Präfix `target`target auf.

>[!TIP]
>
>Lebenszyklusmetriken werden als Parameter jeder mbox-Load gesendet. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/ios/metrics.md). Wenn Sie Target-Anforderungen innerhalb der `didFinishLaunching` Delegate-Methode senden, fügen Sie einen `[ADBMobile trackAction:data:]` oder `[ADBMobile trackState:data:]` einen Aufruf vor dem Target-Implementierungscode hinzu. Auf diese Weise enthalten die Target-Anforderungen die vollständigen Lebenszyklusdaten.

## Klassenverweis: Adbtargetlocationrequest

### Eigenschaften

```objective-c
NSString *name; 
NSString *defaultContent; 
NSMutableDictionary *parameters;
```

### Zeichenfolgen-Konstanten

>[!TIP]
>
>Die folgenden Konstanten dienen zur Benutzerfreundlichkeit, wenn Sie Schlüssel für benutzerdefinierte Parameter festlegen.

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
>* If you are using SDKs **before** version 4.14.0, see [Input Parameters](https://developers.adobetarget.com/api/#input-parameters) for parameters limitations.
   >
   >
* If you are using SDKs version 4.14.0 **or after**, see [Batch Input Parameters](https://developers.adobetarget.com/api/#batch-input-parameters) for parameters limitations.


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

* **targetLoadRequestWithName:defaultContent:profileParameters:orderParameters:mboxParameters:requestLocationParameters:callback:**

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

   * Hier sind die Parameter für diese Methode:

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

      Weitere Informationen zur zugrunde liegenden Target-API finden Sie unter [Adobe Target-Entwickler](https://docs.adobe.com/dev/products/target/reference/delivery.html).







* **targetLoadRequestWithName:defaultContent:profileParameters:orderParameters:mboxParameters:callback**

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

   Erstellt eine `ADBTargetLocationRequest`.

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
   >Seit Version 4.10.0 des SDK verwendet Target keine Cookies mehr. Durch diese Methode werden thirdPartyID und sessionID zurückgesetzt.

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
