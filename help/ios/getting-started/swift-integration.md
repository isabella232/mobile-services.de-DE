---
description: Das iOS Adobe Mobile-SDK kann mithilfe der Funktion „Mix and Match“ (Kombinieren und abgleichen) in der iOS-Entwicklerbibliothek nahtlos in ein Swift-Projekt integriert werden.
seo-description: Das iOS Adobe Mobile-SDK kann mithilfe der Funktion „Mix and Match“ (Kombinieren und abgleichen) in der iOS-Entwicklerbibliothek nahtlos in ein Swift-Projekt integriert werden.
seo-title: Swift-Integration
solution: Experience Cloud,Analytics
title: Swift-Integration
topic: Developer and implementation
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 71%

---


# Swift-Integration {#swift-integration}

Das iOS Adobe Mobile-SDK kann mithilfe der Funktion „Mix and Match“ (Kombinieren und abgleichen) in der iOS-Entwicklerbibliothek nahtlos in ein Swift-Projekt integriert werden.

Weitere Informationen finden Sie unter [Language Interoperability (Sprachinteroperabilität)](https://developer.apple.com/documentation/swift#2984801.html).

Durch Verwendung der Überbrückungs-Header-Methode, wie in der Dokumentation beschrieben, können Sie z. B. die Header-Datei der Adobe Mobile iOS SDK importieren:

```
#import “ADBMobile.h”
```

Verwenden Sie das folgende Format, um auf Methoden aus dem SDK in Ihren Swift-Dateien zuzugreifen:

```
ADBMobile.{methodname}
```

