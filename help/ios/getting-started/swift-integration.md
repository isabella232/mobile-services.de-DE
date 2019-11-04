---
description: Das iOS Adobe Mobile-SDK kann mithilfe der Funktion „Mix and Match“ (Kombinieren und abgleichen) in der iOS-Entwicklerbibliothek nahtlos in ein Swift-Projekt integriert werden.
seo-description: Das iOS Adobe Mobile-SDK kann mithilfe der Funktion „Mix and Match“ (Kombinieren und abgleichen) in der iOS-Entwicklerbibliothek nahtlos in ein Swift-Projekt integriert werden.
seo-title: Swift-Integration
solution: Experience Cloud,Analytics
title: Swift-Integration
topic: Entwickler und Implementierung
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
translation-type: ht
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Swift-Integration {#swift-integration}

Das iOS Adobe Mobile-SDK kann mithilfe der Funktion „Mix and Match“ (Kombinieren und abgleichen) in der iOS-Entwicklerbibliothek nahtlos in ein Swift-Projekt integriert werden.

Weitere Informationen finden Sie unter [Language Interoperability (Sprachinteroperabilität)](https://developer.apple.com/documentation/swift#2984801.html).

Beispielsweise können Sie durch Verwendung der Methode „bridging header“ entsprechend der Beschreibung in der Dokumentation die iOS-SDK-Header-Datei in Adobe Mobile importieren:

```
#import “ADBMobile.h”
```

Verwenden Sie das folgende Format, um auf Methoden im SDK in Ihren Swift-Dateien zuzugreifen:

```
ADBMobile.{methodname}
```

