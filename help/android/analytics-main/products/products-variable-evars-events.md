---
description: Hier finden Sie ein Beispiel der Variablen „products“ mit Merchandising eVars und produktspezifischen Ereignissen.
keywords: Android;Bibliothek;Mobile;SDK
seo-description: Hier finden Sie ein Beispiel der Variablen „products“ mit Merchandising eVars und produktspezifischen Ereignissen.
seo-title: Variable „products“ mit Merchandising-eVars und produktspezifischen Ereignissen
solution: Experience Cloud,Analytics
title: Variable „products“ mit Merchandising-eVars und produktspezifischen Ereignissen
topic: Entwickler und Implementierung
uuid: 64f822a0-6ccf-48e7-8886-31b93d8198a3
translation-type: ht
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Variable „products“ mit Merchandising-eVars und produktspezifischen Ereignissen {#products-variable-with-merchandising-evars-and-product-specific-events}

Hier finden Sie ein Beispiel der Variablen „products“ mit Merchandising eVars und produktspezifischen Ereignissen.

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata.put("&&events", "event1"); 
cdata.put("&&products", ";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99"); 
cdata.put("myapp.purchase", "1"); 
cdata.put("myapp.purchaseid", "1234567890"); 
  
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("purchase", cdata); 
// trackState example: 
Analytics.trackState("Order Confirmation", cdata);
```

>[!TIP]
>
>Wenn Sie ein produktspezifisches Ereignis mithilfe der Variable *`&&products`* auslösen, müssen Sie dieses Ereignis auch in der Variable *`&&events`* festlegen. Wenn Sie dieses Ereignis nicht festlegen, wird es während der Verarbeitung herausgefiltert.

