---
description: Die Variable "products"kann nicht mithilfe von Verarbeitungsregeln festgelegt werden. Im mobilen SDK müssen Sie eine spezielle Syntax innerhalb des Kontextdatenparameters verwenden, um Produkte direkt beim Server-Aufruf festzulegen.
solution: Experience Cloud,Analytics
title: Variable „products“
topic-fix: Developer and implementation
uuid: 2057a564-06ae-4171-bbe7-0baffa71608b
exl-id: b731e794-7134-4c6d-a41b-09ac9b84763d
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 15%

---

# Variable „products“{#products-variable}

Die Variable &quot;products&quot;kann nicht mithilfe von Verarbeitungsregeln festgelegt werden. Im mobilen SDK müssen Sie eine spezielle Syntax innerhalb des Kontextdatenparameters verwenden, um Produkte direkt beim Server-Aufruf festzulegen.

Um die Variable *`products`* festzulegen, setzen Sie einen Kontextdatenschlüssel auf `"&&products"` und legen Sie den Wert mithilfe der für *`products`* definierten Syntax fest:

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

*`products`* wird direkt für die Bildanforderung festgelegt und die anderen Variablen werden als Kontextdaten festgelegt. Alle Kontextdatenvariablen müssen mithilfe von Verarbeitungsregeln zugeordnet werden:

![](assets/products-procrules.png)

Sie müssen die Variable *`products`* nicht mithilfe von Verarbeitungsregeln zuordnen, da sie vom SDK direkt in der Bildanforderung festgelegt wird.
