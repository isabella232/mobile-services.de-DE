---
description: Gibt Ihnen beim Starten der Anwendung die Möglichkeit, eine andere ADBMobile JSON-Konfigurationsdatei zu laden.
seo-description: Gibt Ihnen beim Starten der Anwendung die Möglichkeit, eine andere ADBMobile JSON-Konfigurationsdatei zu laden.
seo-title: ADBMobile-JSON-Konfigurationspfad überschreiben
solution: Marketing Cloud,Analytics
title: ADBMobile-JSON-Konfigurationspfad überschreiben
topic: Entwickler und Implementierung
uuid: 6872a5d7-0c5a-4fdc-b7bf-ad1534763a6a
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

Gibt Ihnen beim Starten der Anwendung die Möglichkeit, eine andere ADBMobile JSON-Konfigurationsdatei zu laden.

The `Config.overrideConfigStream(configInput)` method allows you to specify the path to a different `ADBMobile.json` configuration file when the application starts. This method must be called before any other Experience Cloud SDK call (before `Config.collectLifecycleData()` ), typically in the `onCreate` method of your first loaded activity.

Wenn Sie diese Methode mit einem anderen Pfad aufrufen, wird hierdurch die Konfigurationsdatei überschrieben, bis die Anwendung wieder geschlossen wird.

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```

