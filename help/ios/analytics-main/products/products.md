---
description: Die Variable „products“ kann nicht mithilfe von Verarbeitungsregeln festgelegt werden. Im iOS SDK 4.x müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um die Variable „products“ direkt beim Server-Aufruf festzulegen.
seo-description: Die Variable „products“ kann nicht mithilfe von Verarbeitungsregeln festgelegt werden. Im iOS SDK 4.x müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um die Variable „products“ direkt beim Server-Aufruf festzulegen.
seo-title: Variable „products“
solution: Experience Cloud,Analytics
title: Variable „products“
topic: Developer and implementation
uuid: 6ece4d27-ef86-435c-a6f7-bd76be1c95ca
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '184'
ht-degree: 100%

---


# Variable „products“ {#products-variable}

Die Variable „products“ kann nicht mithilfe von Verarbeitungsregeln festgelegt werden. Im iOS SDK 4.x müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um die Variable „products“ direkt beim Server-Aufruf festzulegen.

Um die Variable *`products`* festzulegen, setzen Sie einen Kontextdatenschlüssel auf `"&&products"` und legen Sie mithilfe der für die Variable *`products`* definierten Syntax den Wert fest:

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

*`products`* wird direkt für die Bildanforderung festgelegt und die anderen Variablen werden als Kontextdaten festgelegt. Sämtliche Kontextdatenvariablen müssen mithilfe von Verarbeitungsregeln zugeordnet werden:

![](assets/map-products.png)

Sie müssen die Variable  *`products`* nicht mithilfe von Verarbeitungsregeln zuordnen, da sie direkt in der Bildanforderung vom SDK festgelegt wird.
