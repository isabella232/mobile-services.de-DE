---
description: Die Variable „products“ kann nicht mithilfe von Verarbeitungsregeln festgelegt werden. Im iOS-SDK 4.x müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um Produkte direkt im Server-Aufruf festzulegen.
seo-description: Die Variable „products“ kann nicht mithilfe von Verarbeitungsregeln festgelegt werden. Im iOS-SDK 4.x müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um Produkte direkt im Server-Aufruf festzulegen.
seo-title: Variable „products“
solution: Marketing Cloud, Analytics
title: Variable „products“
topic: Entwickler und Implementierung
uuid: 6 ece 4 d 27-ef 66-435 c-a 6 f 7-bd 76 be 1 c 95 ca
translation-type: tm+mt
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Products variable {#products-variable}

Die Variable „products“ kann nicht mithilfe von Verarbeitungsregeln festgelegt werden. Im iOS-SDK 4.x müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um Produkte direkt im Server-Aufruf festzulegen.

To set the *`products`* variable, set a context data key to `"&&products"`, and set the value by using the syntax that is defined for the *`products`* variable:

```objective-c
[contextData setObject:@"Category;Product;Quantity;Price[,Category;Product;Quantity;Price]" forKey:@"&&products"];
```

Beispiel:

```objective-c
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
[contextData setObject:@";Running Shoes;1;69.95,;Running Socks;10;29.99" forKey:@"&&products"]; 
[contextData setObject:@"1234567890" forKey:@"m.purchaseid"]; 
[contextData setObject:@"1" forKey:@"m.purchase"]; 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"purchase" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"Order Confirmation" data:contextData]; 
```

*`products`* direkt für die Bildanforderung festgelegt ist und dass andere Variablen als Kontextdaten festgelegt werden. Sämtliche Kontextdatenvariablen müssen mithilfe von Verarbeitungsregeln zugeordnet werden:

![](assets/map-products.png)

Sie müssen die Variable *`products`* nicht mithilfe von Verarbeitungsregeln zuordnen, da sie direkt in der Bildanforderung vom SDK festgelegt wird.
