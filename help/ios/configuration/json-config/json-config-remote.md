---
description: Sie können beim Starten der Anwendung eine andere ADBMobile JSON-Konfigurationsdatei laden.
seo-description: Sie können beim Starten der Anwendung eine andere ADBMobile JSON-Konfigurationsdatei laden.
seo-title: ADBMobile JSON-Konfigurationspfad überschreiben
solution: Marketing Cloud,Analytics
title: Override the ADBMobile JSON config path
topic: Entwickler und Implementierung
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

Sie können beim Starten der Anwendung eine andere ADBMobile JSON-Konfigurationsdatei laden.

The `ADBMobile overrideConfigPath:filePath` method allows you to specify the path to a different `ADBMobile.json` configuration file when the application starts. Diese Methode muss in der Methode `applicationDidFinishLaunchingWithOptions` aufgerufen werden und der Aufruf muss vor jedem anderen Experience Cloud-SDK-Aufruf wie beispielsweise `collectLifecycleData` erfolgen.

Wenn Sie diese Methode mit einem anderen Pfad aufrufen, wird die Konfigurationsdatei nur einmal außer Kraft gesetzt, bis die Anwendung geschlossen wird.

Beispiel:

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```

