---
description: Die Variable „products“ kann nicht mithilfe von Verarbeitungsregeln festgelegt werden. Im Mobile-SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um Produkte direkt im Server-Aufruf festzulegen.
seo-description: Die Variable „products“ kann nicht mithilfe von Verarbeitungsregeln festgelegt werden. Im Mobile-SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um Produkte direkt im Server-Aufruf festzulegen.
seo-title: Produktvariable
solution: Marketing Cloud, Analytics
title: Produktvariable
topic: Entwickler und Implementierung
uuid: 2057 a 564-06 ae -4171-bbe 7-0 baffa 71608 b
translation-type: tm+mt
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Products variable{#products-variable}

Die Variable „products“ kann nicht mithilfe von Verarbeitungsregeln festgelegt werden. Im Mobile-SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um Produkte direkt im Server-Aufruf festzulegen.

To set the *`products`* variable, set a context data key to `"&&products"`, and set the value using the syntax defined for the *`products`*:

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

*`products`* direkt für die Bildanforderung festgelegt ist und dass andere Variablen als Kontextdaten festgelegt werden. Sämtliche Kontextdatenvariablen müssen mithilfe von Verarbeitungsregeln zugeordnet werden:

![](assets/products-procrules.png)

Sie müssen die *`products`* Variable nicht mithilfe von Verarbeitungsregeln zuordnen, da sie direkt in der Bildanforderung durch das SDK festgelegt ist.
