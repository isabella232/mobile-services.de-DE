---
description: Das iOS Adobe Mobile-SDK kann mithilfe der Funktion „Mix and Match“ (Kombinieren und abgleichen) in der iOS-Entwicklerbibliothek nahtlos in ein Swift-Projekt integriert werden.
solution: Experience Cloud Services,Analytics
title: Swift-Integration
topic-fix: Developer and implementation
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
exl-id: 3c1a2e28-53b0-4128-a5d9-d2403885098d
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 100%

---

# Swift-Integration {#swift-integration}

Das iOS Adobe Mobile-SDK kann mithilfe der Funktion „Mix and Match“ (Kombinieren und abgleichen) in der iOS-Entwicklerbibliothek nahtlos in ein Swift-Projekt integriert werden.

Weitere Informationen finden Sie unter [Language Interoperability (Sprachinteroperabilität)](https://developer.apple.com/documentation/swift#2984801.html).

Mithilfe der in der Dokumentation beschriebenen Bridging-Header-Methode können Sie beispielsweise die Adobe Mobile iOS SDK-Header-Datei importieren:

```
#import "ADBMobile.h"
```

Verwenden Sie das folgende Format, um auf Methoden aus dem SDK in Ihren Swift-Dateien zuzugreifen:

```
ADBMobile.{methodname}
```
