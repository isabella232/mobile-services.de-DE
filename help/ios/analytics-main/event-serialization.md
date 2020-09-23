---
description: Die Serialisierung von Ereignissen wird von Verarbeitungsregeln nicht unterstützt. Im Mobile SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um serialisierte Ereignis direkt beim Serveraufruf festzulegen.
seo-description: Die Serialisierung von Ereignissen wird von Verarbeitungsregeln nicht unterstützt. Im Mobile SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um serialisierte Ereignis direkt beim Serveraufruf festzulegen.
seo-title: Ereignis-Serialisierung
solution: Experience Cloud,Analytics
title: Ereignis-Serialisierung
topic: Developer and implementation
uuid: 19a27df4-0998-403d-800c-26ff61149208
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 7%

---


# Ereignis-Serialisierung {#event-serialization}

Die Serialisierung von Ereignissen wird von Verarbeitungsregeln nicht unterstützt. Im Mobile SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um serialisierte Ereignis direkt beim Serveraufruf festzulegen.

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

