---
description: Die Variable "products"kann nicht mit Verarbeitungsregeln eingestellt werden. Im mobilen SDK müssen Sie eine spezielle Syntax innerhalb des Kontextdatenparameters verwenden, um Produkte direkt beim Server-Aufruf festzulegen.
seo-description: Die Variable "products"kann nicht mit Verarbeitungsregeln eingestellt werden. Im mobilen SDK müssen Sie eine spezielle Syntax innerhalb des Kontextdatenparameters verwenden, um Produkte direkt beim Server-Aufruf festzulegen.
seo-title: 'Variable „products“ '
solution: Experience Cloud,Analytics
title: 'Variable „products“ '
topic: Developer and implementation
uuid: 607983d6-48ac-4274-bfc8-b1ca4e5dad1b
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 7%

---


# Variable „products“ {#products-variable}

Die Variable &quot;products&quot;kann nicht mit Verarbeitungsregeln eingestellt werden. Im mobilen SDK müssen Sie eine spezielle Syntax innerhalb des Kontextdatenparameters verwenden, um Produkte direkt beim Server-Aufruf festzulegen.

To set the *`products`* variable, set a context data key to `"&&products"`, and set the value using the syntax defined for the *`products` variable:

```js
cdata["&&products"] = "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]";
```

Beispiel:

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&products"] = ";Running Shoes;1;69.95,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

The *`products`* is set directly on the image request, and the other variables are set as context data. Alle Kontextdatenvariablen müssen mithilfe von Verarbeitungsregeln zugeordnet werden:

![](assets/products-procrules.png)

Sie müssen die *`products`* Variable nicht mithilfe von Verarbeitungsregeln zuordnen, da sie direkt auf der Bildanforderung des SDK eingestellt wird.

## Variable „products“ mit Merchandising-eVars und produktspezifischen Ereignissen {#section_685D53AD3D064F9A8E225F995A9BA545}

An example of the *`products`* variable with Merchandising eVars and product-specific events.

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

