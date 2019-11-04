---
description: Sie können beim Starten der Anwendung eine andere ADBMobile JSON-Konfigurationsdatei laden.
seo-description: Sie können beim Starten der Anwendung eine andere ADBMobile JSON-Konfigurationsdatei laden.
seo-title: ADBMobile-JSON-Konfigurationspfad überschreiben
solution: Experience Cloud,Analytics
title: ADBMobile-JSON-Konfigurationspfad überschreiben
topic: Entwickler und Implementierung
uuid: 6872a5d7-0c5a-4fdc-b7bf-ad1534763a6a
translation-type: ht
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

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

