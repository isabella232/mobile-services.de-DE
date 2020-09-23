---
description: Hier finden Sie ein Beispiel der Variablen „products“ mit Merchandising eVars und produktspezifischen Ereignissen.
seo-description: Hier finden Sie ein Beispiel der Variablen „products“ mit Merchandising eVars und produktspezifischen Ereignissen.
seo-title: Variable „products“ mit Merchandising-eVars und produktspezifischen Ereignissen
solution: Experience Cloud,Analytics
title: Variable „products“ mit Merchandising-eVars und produktspezifischen Ereignissen
topic: Developer and implementation
uuid: f913211e-97ad-4237-bfe4-7ded01295caf
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 100%

---


# Variable „products“ mit Merchandising-eVars und produktspezifischen Ereignissen {#products-variable-with-merchandising-evars-and-product-specific-events}

Hier finden Sie ein Beispiel der Variablen „products“ mit Merchandising eVars und produktspezifischen Ereignissen.

```
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
[contextData setObject:@"event1" forKey:@"&&events"]; 
[contextData setObject:@";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99" forKey:@"&&products"]; 
[contextData setObject:@"1234567890" forKey:@"m.purchaseid"]; 
[contextData setObject:@"1" forKey:@"m.purchase"]; 
  
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"purchase" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"Order Confirmation" data:contextData];
```

>[!TIP]
>
>Wenn Sie ein produktspezifisches Ereignis mithilfe der Variable *`&&products`* auslösen, müssen Sie dieses Ereignis auch in der Variable *`&&events`* festlegen. Wenn Sie dieses Ereignis nicht festlegen, wird es während der Verarbeitung herausgefiltert.

