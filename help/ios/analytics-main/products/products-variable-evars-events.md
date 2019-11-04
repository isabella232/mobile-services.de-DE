---
description: Hier finden Sie ein Beispiel der Variablen „products“ mit Merchandising eVars und produktspezifischen Ereignissen.
seo-description: Hier finden Sie ein Beispiel der Variablen „products“ mit Merchandising eVars und produktspezifischen Ereignissen.
seo-title: Variable „products“ mit Merchandising-eVars und produktspezifischen Ereignissen
solution: Experience Cloud,Analytics
title: Variable „products“ mit Merchandising-eVars und produktspezifischen Ereignissen
topic: Entwickler und Implementierung
uuid: f913211e-97ad-4237-bfe4-7ded01295caf
translation-type: ht
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

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

