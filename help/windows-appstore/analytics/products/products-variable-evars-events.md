---
description: Ein Beispiel für die Produktvariable mit Merchandising eVars und produktspezifischen Ereignissen.
seo-description: Ein Beispiel für die Produktvariable mit Merchandising eVars und produktspezifischen Ereignissen.
seo-title: Variable „products“ mit Merchandising-eVars und produktspezifischen Ereignissen
solution: Experience Cloud,Analytics
title: Variable „products“ mit Merchandising-eVars und produktspezifischen Ereignissen
topic: Developer and implementation
uuid: 94e882e4-b19d-4c48-9dfb-331465490347
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 27%

---


# Variable „products“ mit Merchandising-eVars und produktspezifischen Ereignissen{#products-variable-with-merchandising-evars-and-product-specific-events}

Ein Beispiel für die Produktvariable mit Merchandising eVars und produktspezifischen Ereignissen.

```
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&events"] = "event1 "; 
cdata["&&products"] = ";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
  
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

>[!TIP]
>
>Wenn Sie ein produktspezifisches Ereignis mithilfe der *`&&products`* Variablen auslösen, müssen Sie dieses Ereignis auch in der *`&&events`* Variablen einstellen, da das Ereignis andernfalls während der Verarbeitung herausgefiltert wird.

