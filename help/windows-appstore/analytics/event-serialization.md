---
description: Die Ereignis-Serialisierung wird von Verarbeitungsregeln nicht unterstützt. Im Mobile-SDK müssen Sie eine spezielle Syntax innerhalb des Kontextdatenparameters verwenden, um serialisierte Ereignisse direkt beim Server-Aufruf festzulegen.
seo-description: Die Ereignis-Serialisierung wird von Verarbeitungsregeln nicht unterstützt. Im Mobile-SDK müssen Sie eine spezielle Syntax innerhalb des Kontextdatenparameters verwenden, um serialisierte Ereignisse direkt beim Server-Aufruf festzulegen.
seo-title: Ereignis-Serialisierung
solution: Marketing Cloud, Analytics
title: Ereignis-Serialisierung
topic: Entwickler und Implementierung
uuid: a 5966 d 05-e 218-446 f -9 f 19-8664 a 84 b 74 cd
translation-type: tm+mt
source-git-commit: 4faf66df50c8b65198fd139bb15927fc2c2849bc

---


# Ereignis-Serialisierung{#event-serialization}

Die Ereignis-Serialisierung wird von Verarbeitungsregeln nicht unterstützt. Im mobilen SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um serialisierte Ereignisse direkt im Serveraufruf festzulegen.

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

