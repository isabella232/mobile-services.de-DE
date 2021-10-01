---
description: Sie können beim Starten der Anwendung eine andere ADBMobile JSON-Konfigurationsdatei laden.
solution: Experience Cloud,Analytics
title: ADBMobile JSON-Konfigurationspfad überschreiben
topic-fix: Developer and implementation
uuid: 6872a5d7-0c5a-4fdc-b7bf-ad1534763a6a
exl-id: 6ca8e264-af79-4734-aeb9-824582980953
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 100%

---

# ADBMobile JSON-Konfigurationspfad überschreiben {#override-the-adbmobile-json-config-path}

Sie können beim Starten der Anwendung eine andere ADBMobile JSON-Konfigurationsdatei laden.

Die Methode `Config.overrideConfigStream(configInput)` ermöglicht es Ihnen, den Pfad zu einer anderen `ADBMobile.json`-Konfigurationsdatei anzugeben, wenn die App startet. Diese Methode muss vor jedem anderen Experience Cloud-SDK-Aufruf (vor `Config.collectLifecycleData()`) aufgerufen werden – für gewöhnlich in der Methode `onCreate` Ihrer zuerst geladenen Aktivität.

Wenn Sie diese Methode mit einem anderen Pfad aufrufen, wird hierdurch die Konfigurationsdatei überschrieben, bis die Anwendung wieder geschlossen wird.

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```
