---
description: Die Ereignis-Serialisierung wird von Verarbeitungsregeln nicht unterstützt. Im mobilen SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um serialisierte Ereignis direkt beim Serveraufruf festzulegen.
seo-description: Die Ereignis-Serialisierung wird von Verarbeitungsregeln nicht unterstützt. Im mobilen SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um serialisierte Ereignis direkt beim Serveraufruf festzulegen.
seo-title: Ereignis-Serialisierung
solution: Experience Cloud,Analytics
title: Ereignis-Serialisierung
topic-fix: Developer and implementation
uuid: a5966d05-e218-446f-9f19-8664a84b74cd
exl-id: 42ea5e0f-a69e-44ab-aa4e-bbec27815cc8
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 30%

---

# Ereignis-Serialisierung{#event-serialization}

Die Ereignis-Serialisierung wird von Verarbeitungsregeln nicht unterstützt. Im mobilen SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um serialisierte Ereignis direkt beim Serveraufruf festzulegen.

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
