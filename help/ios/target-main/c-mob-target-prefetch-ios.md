---
description: Die Vorabruffunktion von Adobe Target verwendet iOS Mobile SDKs, um so Angebotsinhalte so selten wie möglich abzurufen, indem die Serverantworten im Cache abgelegt werden.
seo-description: Die Vorabruffunktion von Adobe Target verwendet iOS Mobile SDKs, um so Angebotsinhalte so selten wie möglich abzurufen, indem die Serverantworten im Cache abgelegt werden.
seo-title: Vorabruf-Angebotsinhalte in iOS
title: Vorabruf-Angebotsinhalte in iOS
uuid: fef 58042-65 e 2-4579-b 8 f 1-d 21554 d 2 af 57
translation-type: tm+mt
source-git-commit: fa7375ac8a1345d81748bcf635791c46d3943fed

---


# Vorabruf-Angebotsinhalte in iOS {#prefetch-offer-content-in-ios}

Die Vorabruffunktion von Adobe Target verwendet iOS Mobile SDKs, um so Angebotsinhalte so selten wie möglich abzurufen, indem die Serverantworten im Cache abgelegt werden.

>[!IMPORTANT]
>
>Prefetch-Funktionen in mobilen sdks für ios werden für die Aktivitätstypen Automatisches Targeting, Automatisierte Zuordnung und automatisierte Personalisierung in Adobe Target nicht unterstützt.

Dieser Vorgang reduziert die Ladezeit, vermeidet mehrfache Netzwerk-Aufrufe und ermöglicht es Adobe Target, eine Benachrichtigung darüber zu erhalten, welche mbox vom Benutzer der mobilen App besucht wurde. Der gesamte Inhalt wird abgerufen und während des Aufrufs für den Vorabruf im Cache abgelegt, und dieser Inhalt wird bei allen zukünftigen Aufrufen abgerufen, die im Cache abgelegte Inhalte für den spezifizierten mbox-Namen enthalten.

Vorabgerufene Inhalte werden nicht über Starts hinweg behalten. The prefetch content is cached as long as the application lives or until the `clearPrefetchCache()` method is called.

>[!IMPORTANT]
>
>Target prefetch APIs have been available since SDK version 4.14.0. For more information about parameter limitations, see [Batch Input Parameters](https://developers.adobetarget.com/api/#batch-input-parameters).

In der SDK-Version 4.14 oder später wird, sofern spezifiziert, `environmentId``ADBMobileConfig.json` beim Initiieren eines v2 Batch-MBox-TnT-Anrufs aus der Datei „“ gewonnen. Wenn keine `environmentId` in der Datei angegeben ist, wird kein Umgebungsparameter in den TNT-Batch-MBox-Aufruf gesendet und das Angebot für die Standardumgebung wird geliefert.

Beispiel:

```
if (MobileConfig.getInstance().mobileUsingTarget()){ 
            long environmentID = MobileConfig.getInstance().getEnvironmentID(); 
            if(environmentID != 0L){ 
                parametersJson.put(TargetJson.ENVIRONMENT_ID, environmentID); 
            } 
        }
```

## Prefetch-Methoden {#section_05967F1F3A554B0FBC2C08A954554BDE}

Hier finden Sie die Verfahren, die Sie für den Vorabruf unter iOS nutzen können:

* **targetPrefetchContent**

   Sendet eine Vorabruf-Anfrage mit einem Array von Speicherorten an den konfigurierten Target-Server und gibt den Anfragestatus im bereitgestellten Rückruf zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      (void) targetPrefetchContent:(nonnull NSArray*)targetPrefetchObjectArray 
                     withProfileParameters:(nullable NSDictionary*)profileParameters 
                            callback:(nullable void(^)(BOOL success))callback;
      ```

   * Hier sind die Parameter für diese Methode:

      * **`targetPrefetchArray`**

         Array von `TargetPrefetchObjects`, das den Namen und mboxParameters für jeden Target-Speicherort enthält, der vorab abgerufen werden soll.

      * **`profileParameters`**

         Enthält die Schlüssel und Werte von Profilparametern, die mit jedem Standortvorabruf in dieser Anfrage verwendet werden sollen.

      * **`callback`**

         Wird aufgerufen, wenn der Vorabruf abgeschlossen ist. Returns `true` if the prefetch was successful and `false` if the prefetch was unsuccesful.

* **targetLoadRequests**

   Führt eine Stapelanfrage über mehrere mbox-Orte aus, die im Anfrage-Array enthalten sind. Jedes Objekt im Array enthält eine Callback-Funktion, die aufgerufen wird, wenn für den angegebenen mbox-Speicherort Inhalt verfügbar ist.

   >[!IMPORTANT]
   >
   >Wenn der Inhalt für die angeforderten Standorte bereits zwischengespeichert ist, wird er sofort im angegebenen Rückruf zurückgegeben. Andernfalls sendet das SDK eine Netzwerkanfrage an die Target-Server, um den Inhalt abzurufen.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      (void)targetLoadRequests:(nonnullNSArray*)requests 
               withProfileParameters:(nullableNSDictionary*)profileParameters;
      ```

   * Hier sind die Parameter für diese Methode:

      * **`requests`**

         Array von `TargetRequestObjects`, das den Namen, den Standardinhalt, die Parameter und die Rückruffunktion für jeden abzurufenden Standort enthält.

      * **`profileParameters`**

         Enthält Schlüssel und Werte von Profilparametern, die mit jedem Standortvorabruf in dieser Anfrage verwendet werden.

* **targetPrefetchClearCache**

   Löscht die Daten, die vom Target-Vorabruf zwischengespeichert wurden.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      (void) targetPrefetchClearCache; 
      ```

   * Für diese Methode gibt es keine Parameter.

* **targetRequestObjectWithName**

   Erstellt mit den bereitgestellten Daten eine `TargetRequestObject`-Instanz und gibt diese zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      +(nullableADBTargetRequestObject*)targetRequestObjectWithName:(nonnullNSString*)name
      defaultContent:(nonnullNSString*)defaultContent
      mboxParameters:(nullableNSDictionary*)mboxParameters
      callback:(nullablevoid(^)(NSString*__nullablecontent))callback;
      ```

   * Für diese Methode gibt es keine Parameter.

* **createTargetPrefetchObject**

   Erstellt mit den bereitgestellten Daten eine `TargetPrefetchObject`-Instanz und gibt diese zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      +(nullable ADBTargetPrefetchObject *) targetPrefetchObjectWithName:(nonnullNSString *)name
      mboxParameters:(nullableNSDictionary *)mboxParameters;
      ```

## Public classes {#section_A273E53F069E4327BBC8CE4910B37888}

Dies sind die öffentlichen Klassen, die den Vorabruf in iOS unterstützen:

### Klassenverweis: Targetprefetchobject

Umfasst mbox-Namen sowie die Parameter, die für den mbox-Vorabruf verwendet werden.

* **`name`**

   Name der gewünschten Position/mbox.

   * **Typ**: NSString*

* **`mboxParameters`**

   Optionales Wörterbuch, das die Schlüssel-Wert-Paare der mbox-Parameter enthält.

   * **Typ**: NSDictionary*

* **`orderParameters`**

   Optionales Wörterbuch, das die Schlüssel-Wert-Paare der Auftragsparameter enthält.

   * **Typ**: NSDictionary*

* **`productParameters`**

   Optionales Wörterbuch, das die Schlüssel-Wert-Paare der Produktparameter enthält.

   * **Typ**: NSDictionary*

### Klassenverweis: Targetrequestobject

Diese Klasse kapselt den mbox-Namen, den Standardinhalt, die mbox-Parameter und den Rückruf ein, die für die Target-Standortanfragen verwendet werden.

* **`name`**

   Name des angefragten Standorts.

   * **Typ**: NSString*

* **`mboxParameters`**

   Der NSString-Wert steht für den Namen des Orts/der mbox, den oder die Sie aufrufen möchten.

   * **Typ**: NSString*

* **`defaultContent`**

   Der Standardinhalt, der zurückgegeben wird, wenn die Target-Server nicht erreichbar sind.

   * **Typ**: NSString*

* **`callback`**

   Werden vom Stapel Target-Orte angefragt, wird der Rückruf aktiviert, wenn für den entsprechenden Ort Inhalte bereitstehen.

   * **Typ**: Funktion

## Code sample {#section_BF7F49763D254371B4656E17953D520C}

Hier finden Sie ein Beispiel dafür, wie Sie mit iOS-SDKs einen Vorabruf vornehmen können:

```objective-c
/** 
 * Prefetch Content 
 */ 
  
    NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
    NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
    NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
  
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    // Creating Prefetch Objects 
    ADBTargetPrefetchObject *prefetch1 = [ADBMobile targetPrefetchObjectWithName:@"logo" mboxParameters:mboxParameters1]; 
    prefetch1.productParameters = productParameters1; 
    prefetch1.orderParameters = orderParameters1; 
  
    ADBTargetPrefetchObject *prefetch2 = [ADBMobile targetPrefetchObjectWithName:@"buttonColor" mboxParameters:mboxParameters2]; 
    prefetch2.productParameters = productParameters2; 
    prefetch2.orderParameters = orderParameters2; 

    // Creating prefetch Array 
    NSArray *prefetchArray = @[prefetch1,prefetch2]; 
  
    // Creating Profile parameters 
    NSDictionary *profileParmeters = @{@"age":@"20-32"};

    // Target API Call 
    [ADBMobile targetPrefetchContent:prefetchArray withProfileParameters:profileParmeters callback:^(BOOL isSuccess){ 
       // do something with the Boolean result 
    }];
```

Hier finden Sie ein Beispiel für den Stapel `loadRequest` unter Verwendung der iOS-SDKs:

```objective-c
/** 
 * Batch loadRequest  
 */ 
  
   NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
   NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
   NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    ADBTargetRequestObject *request1 = [ADBMobile targetRequestObjectWithName:@"logo" defaultContent:@"BlueWhale" mboxParameters:mboxParameters1 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
  
    request1.productParameters = productParameters1; 
    request1.orderParameters = orderParameters1;

    ADBTargetRequestObject *request2 = [ADBMobile targetRequestObjectWithName:@"buttonColor" defaultContent:@"red" mboxParameters:mboxParameters2 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
    request2.productParameters = productParameters1; 
    request2.orderParameters = orderParameters1;

    // create request object array 
    NSArray *requestArray = @[request1,request2]; 
  
    // Call the API 
    [ADBMobile targetLoadRequests:requestArray withProfileParameters:profileParmeters];
```

## Weitere Informationen {#section_A454BAD1CD49423E86C71BAEE06125FD}

Im Folgenden einige zusätzliche Informationen zu diesen Beispielen:

* `ProductParameters` erlaubt nur die folgenden Schlüssel:

   * `id`
   * `categoryId`

* `OrderParameters` erlaubt nur die folgenden Schlüssel:

   * `id`
   * `total`
   * `purchasedProductIds`

* Für `purchasedProducts` können zahlreiche Zeichenfolgen verwendet werden.