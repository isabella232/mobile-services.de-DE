---
description: Die Ereignis-Serialisierung wird von Verarbeitungsregeln nicht unterstützt. Im mobilen SDK müssen Sie eine spezielle Syntax innerhalb des Kontextdatenparameters verwenden, um serialisierte Ereignisse direkt beim Server-Aufruf festzulegen.
solution: Experience Cloud Services,Analytics
title: Ereignis-Serialisierung
topic-fix: Developer and implementation
uuid: a5966d05-e218-446f-9f19-8664a84b74cd
exl-id: 42ea5e0f-a69e-44ab-aa4e-bbec27815cc8
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '70'
ht-degree: 31%

---

# Ereignis-Serialisierung{#event-serialization}

Die Ereignis-Serialisierung wird von Verarbeitungsregeln nicht unterstützt. Im mobilen SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um serialisierte Ereignisse direkt beim Server-Aufruf festzulegen.

```js
cdata["&&events"] = "event1:12341234";
```

Beispiel:

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add events 
cdata["&&events"] = "event1:12341234"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("action", cdata); 
// trackState example: 
ADB.Analytics.trackState("State Name", cdata);
```
