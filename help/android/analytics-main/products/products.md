---
description: Die Variable „products“ kann nicht mithilfe von Verarbeitungsregeln festgelegt werden. Im Mobile SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um die Variable „products“ beim Server-Aufruf festzulegen.
keywords: android;library;mobile;sdk
seo-description: Die Variable „products“ kann nicht mithilfe von Verarbeitungsregeln festgelegt werden. Im Mobile SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um die Variable „products“ beim Server-Aufruf festzulegen.
seo-title: Variable „products“
solution: Experience Cloud,Analytics
title: Variable „products“
topic: Developer and implementation
uuid: f4484022-cb8b-4dea-9209-5a110ba607df
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 100%

---


# Variable „products“ {#products-variable}

Die Variable „products“ kann nicht mithilfe von Verarbeitungsregeln festgelegt werden. Im Mobile SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um die Variable „products“ beim Server-Aufruf festzulegen.

Um die Variable *products* festzulegen, setzen Sie einen Kontextdatenschlüssel auf `"&&products"` und legen Sie mithilfe der für die Variable *products* definierten Syntax den Wert fest:

```java
cdata.put("&&products", "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]");
```

Beispiel:

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata.put("&&products", ";Running Shoes;1;69.95,;Running Socks;10;29.99"); 
cdata.put("myapp.purchase", "1"); 
cdata.put("myapp.purchaseid", "1234567890"); 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("purchase", cdata); 
// trackState example: 
Analytics.trackState("Order Confirmation", cdata);
```

Die Variable *products* wird in der Bildanfrage festgelegt und die anderen Variablen werden als Kontextdaten festgelegt. Sämtliche Kontextdatenvariablen müssen mithilfe von Verarbeitungsregeln zugeordnet werden:

![](assets/map-products.png)

Sie müssen die Variable  *products* nicht mithilfe von Verarbeitungsregeln zuordnen, da diese Variable direkt in der Bildanfrage vom SDK festgelegt wird.
