---
description: Die Vorabruffunktion von Adobe Target verwendet iOS Mobile SDK, um so Angebotsinhalte so selten wie möglich abzurufen, indem die Serverantworten im Cache abgelegt werden.
title: Vorabruf-Angebotsinhalte in iOS
uuid: fef58042-65e2-4579-b8f1-d21554d2af57
exl-id: 64d43be7-6bd1-4657-8154-5b2c1cbbf42b
source-git-commit: 5d44c09a18a557e934628533c4eefaa9e26aba42
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 85%

---

# Vorabruf-Angebotsinhalte in iOS {#prefetch-offer-content-in-ios}

Die Vorabruffunktion von Adobe Target verwendet iOS Mobile SDK, um so Angebotsinhalte so selten wie möglich abzurufen, indem die Serverantworten im Cache abgelegt werden.

Dadurch wird die Ladezeit verkürzt, es werden mehrere Netzwerkaufrufe verhindert und Adobe Target kann darüber informiert werden, welche Mbox vom Benutzer der mobilen App besucht wurde. Alle Inhalte werden während des Vorabrufs abgerufen und zwischengespeichert. Dieser Inhalt wird für alle zukünftigen Aufrufe abgerufen, die zwischengespeicherten Inhalt für den angegebenen Mbox-Namen enthalten.

Vorabgerufene Inhalte werden nicht über Starts hinweg behalten. Der vorabgerufene Inhalt verbleibt im Cache, bis die Lebensdauer der App endet oder die Methode `clearPrefetchCache()` aufgerufen wird.

>[!IMPORTANT]
>
>Vorabruf-APIs für Target gibt es bereits seit SDK-Version 4.14.0. Weitere Informationen zu den Parameterbeschränkungen finden Sie unter [Batch-Eingabeparameter](https://developers.adobetarget.com/api/#batch-input-parameters).

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

## Vorabrufmethoden {#section_05967F1F3A554B0FBC2C08A954554BDE}

Hier finden Sie die Verfahren, die Sie für den Vorabruf unter iOS nutzen können:

* **targetPrefetchContent**

   Sendet eine Vorabruf-Anfrage mit einem Array von Speicherorten an den konfigurierten Target-Server und gibt den Anfragestatus im bereitgestellten Rückruf zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      (void) targetPrefetchContent:(nonnull NSArray*)targetPrefetchObjectArray 
                     withProfileParameters:(nullable NSDictionary*)profileParameters 
                            callback:(nullable void(^)(BOOL success))callback;
      ```

   * Hier finden Sie die Parameter für diese Methode:

      * **`targetPrefetchArray`**

         Array von `TargetPrefetchObjects`, das den Namen und mboxParameters für jeden Target-Speicherort enthält, der vorab abgerufen werden soll.

      * **`profileParameters`**

         Enthält die Schlüssel und Werte von Profilparametern, die mit jedem Standortvorabruf in dieser Anfrage verwendet werden sollen.

      * **`callback`**

         Wird aufgerufen, wenn der Vorabruf abgeschlossen ist. Gibt den Wert `true` aus, wenn der Vorabruf erfolgreich war, und den Wert `false`, wenn der Vorabruf nicht erfolgreich war.

* **targetLoadRequests**

   Führt eine Stapelanfrage über mehrere mbox-Orte aus, die im Anfrage-Array enthalten sind. Jedes Objekt im Array enthält eine Callback-Funktion, die aufgerufen wird, wenn für den angegebenen mbox-Speicherort Inhalt verfügbar ist.

   >[!IMPORTANT]
   >
   >Wenn der Inhalt für die angefragten Speicherorte bereits zwischengespeichert ist, wird er sofort im bereitgestellten Rückruf zurückgegeben. Andernfalls sendet das SDK eine Netzwerkanfrage an die Target-Server, um den Inhalt abzurufen.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      (void)targetLoadRequests:(nonnullNSArray*)requests 
               withProfileParameters:(nullableNSDictionary*)profileParameters;
      ```

   * Hier finden Sie die Parameter für diese Methode:

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

## Öffentliche Klassen {#section_A273E53F069E4327BBC8CE4910B37888}

Dies sind die öffentlichen Klassen, die den Vorabruf in iOS unterstützen:

### Class reference: TargetPreFetchObject

Umfasst mbox-Namen sowie die Parameter, die für den mbox-Vorabruf verwendet werden.

* **`name`**

   Name für den Speicherort/die mbox, den/die Sie abrufen möchten.

   * **Typ**: NSString*

* **`mboxParameters`**

   Optionales Wörterbuch, das die Schlüssel-Wert-Paare der mbox-Parameter enthält.

   * **Typ**: NSDictionary*

* **`orderParameters`**

   Wörterbuch, das die Schlüssel-Wert-Paare von Bestellparametern enthält.

   * **Typ**: NSDictionary*

* **`productParameters`**

   Wörterbuch, das die Schlüssel-Wert-Paare von Produktparametern enthält.

   * **Typ**: NSDictionary*

### Class reference: TargetRequestObject

Diese Klasse kapselt den mbox-Namen, den Standardinhalt, die mbox-Parameter und den Rückruf ein, die für die Target-Standortanfragen verwendet werden.

* **`name`**

   Name des angefragten Standorts.

   * **Typ**: NSString*

* **`mboxParameters`**

   Der NSString-Wert, der den Namen für den Standort/die Mbox darstellt, den/die Sie abrufen möchten.

   * **Typ**: NSString*

* **`defaultContent`**

   Der Standardinhalt, der zurückgegeben wird, wenn Target-Server nicht erreichbar sind.

   * **Typ**: NSString*

* **`callback`**

   Werden vom Stapel Target-Orte angefragt, wird der Rückruf aktiviert, wenn für den entsprechenden Ort Inhalte bereitstehen.

   * **Typ**: Funktion

## Codebeispiel {#section_BF7F49763D254371B4656E17953D520C}

Hier finden Sie ein Beispiel dafür, wie Sie mit iOS-SDK einen Vorabruf vornehmen können:

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

Hier finden Sie ein Beispiel für den Stapel `loadRequest` unter Verwendung der iOS-SDK:

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
