---
description: Sie können beim Starten der Anwendung eine andere ADBMobile JSON-Konfigurationsdatei laden.
seo-description: Sie können beim Starten der Anwendung eine andere ADBMobile JSON-Konfigurationsdatei laden.
seo-title: ADBMobile JSON-Konfigurationspfad überschreiben
solution: Experience Cloud,Analytics
title: ADBMobile JSON-Konfigurationspfad überschreiben
topic-fix: Developer and implementation
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
exl-id: 3a191e9c-905f-4bea-8a6f-5ccf5ea02aff
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
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
