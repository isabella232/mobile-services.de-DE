---
description: Die Variable „products“ kann nicht mithilfe von Verarbeitungsregeln festgelegt werden. Im iOS SDK 4.x müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um die Variable „products“ direkt beim Server-Aufruf festzulegen.
solution: Experience Cloud Services,Analytics
title: Variable „products“
topic-fix: Developer and implementation
uuid: 6ece4d27-ef86-435c-a6f7-bd76be1c95ca
exl-id: c945add4-5358-44f6-b445-554b0df056c1
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '148'
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
