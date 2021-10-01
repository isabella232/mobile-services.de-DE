---
description: Die Ereignis-Serialisierung wird von Verarbeitungsregeln nicht unterstützt. Im Mobile SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um serialisierte Ereignisse direkt beim Server-Aufruf festzulegen.
solution: Experience Cloud,Analytics
title: Ereignis-Serialisierung
topic-fix: Developer and implementation
uuid: 19a27df4-0998-403d-800c-26ff61149208
exl-id: c34331a4-bfe2-4955-807b-92a3303f8d81
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '70'
ht-degree: 100%

---

# Ereignis-Serialisierung {#event-serialization}

Die Ereignis-Serialisierung wird von Verarbeitungsregeln nicht unterstützt. Im Mobile SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um serialisierte Ereignisse direkt beim Server-Aufruf festzulegen.

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
