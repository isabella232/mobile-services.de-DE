---
description: Die Variable „products“ kann nicht mithilfe von Verarbeitungsregeln festgelegt werden. Im Mobile SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um die Variable „products“ beim Server-Aufruf festzulegen.
keywords: Android;Bibliothek;Mobile;SDK
solution: Experience Cloud,Analytics
title: Variable „products“
topic-fix: Developer and implementation
uuid: f4484022-cb8b-4dea-9209-5a110ba607df
exl-id: 1d850ce1-6fd4-463e-8949-8b8cf40d8467
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '155'
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
