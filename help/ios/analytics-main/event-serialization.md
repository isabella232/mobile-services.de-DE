---
description: Die Ereignis-Serialisierung wird von Verarbeitungsregeln nicht unterstützt. Im Mobile-SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um serialisierte Ereignisse direkt beim Server-Aufruf festzulegen.
seo-description: Die Ereignis-Serialisierung wird von Verarbeitungsregeln nicht unterstützt. Im Mobile-SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um serialisierte Ereignisse direkt beim Server-Aufruf festzulegen.
seo-title: Ereignis-Serialisierung
solution: Marketing Cloud, Analytics
title: Ereignis-Serialisierung
topic: Entwickler und Implementierung
uuid: 19 a 27 df 4-0998-403 d -800 c -26 ff 61149208
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Ereignis-Serialisierung {#event-serialization}

Die Ereignis-Serialisierung wird von Verarbeitungsregeln nicht unterstützt. Im Mobile-SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um serialisierte Ereignisse direkt beim Server-Aufruf festzulegen.

```objective-c
[contextData setObject:@"eventN:serial number" forKey:@"&&events"];
```

Beispiel:

```objective-c
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
 
// add events 
[contextData setObject:@"event1:12341234" forKey:@"&&events"]; 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"action" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"State Name" data:contextData]; 
```

