---
description: Sie können beim Starten der Anwendung eine andere ADBMobile JSON-Konfigurationsdatei laden.
seo-description: Sie können beim Starten der Anwendung eine andere ADBMobile JSON-Konfigurationsdatei laden.
seo-title: ADBMobile JSON-Konfigurationspfad überschreiben
solution: Experience Cloud,Analytics
title: ADBMobile JSON-Konfigurationspfad überschreiben
topic: Developer and implementation
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '120'
ht-degree: 100%

---


# ADBMobile JSON-Konfigurationspfad überschreiben {#override-the-adbmobile-json-config-path}

Sie können beim Starten der Anwendung eine andere ADBMobile JSON-Konfigurationsdatei laden.

Die Methode `ADBMobile overrideConfigPath:filePath` ermöglicht es Ihnen, den Pfad zu einer anderen `ADBMobile.json`-Konfigurationsdatei anzugeben, wenn die App startet. Diese Methode muss in der Methode `applicationDidFinishLaunchingWithOptions` aufgerufen werden und der Aufruf muss vor jedem anderen Experience Cloud-SDK-Aufruf wie beispielsweise `collectLifecycleData` erfolgen.

Wenn Sie diese Methode mit einem anderen Pfad aufrufen, wird hierdurch die Konfigurationsdatei überschrieben, bis die App wieder geschlossen wird.

Beispiel:

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```

