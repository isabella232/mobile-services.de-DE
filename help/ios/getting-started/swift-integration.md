---
description: Das iOS Adobe Mobile-SDK kann mithilfe der Funktion „Mix and Match“ (Kombinieren und abgleichen) in der iOS-Entwicklerbibliothek nahtlos in ein Swift-Projekt integriert werden.
seo-description: Das iOS Adobe Mobile-SDK kann mithilfe der Funktion „Mix and Match“ (Kombinieren und abgleichen) in der iOS-Entwicklerbibliothek nahtlos in ein Swift-Projekt integriert werden.
seo-title: Swift-Integration
solution: Marketing Cloud, Analytics
title: Swift-Integration
topic: Entwickler und Implementierung
uuid: 5 fb 77 b 57-cbf 9-4 bcf -8 b 41-65 a 933 bf 9336
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Swift integration {#swift-integration}

Das iOS Adobe Mobile-SDK kann mithilfe der Funktion „Mix and Match“ (Kombinieren und abgleichen) in der iOS-Entwicklerbibliothek nahtlos in ein Swift-Projekt integriert werden.

Weitere Informationen finden Sie unter [Sprachinteroperabilität](https://developer.apple.com/documentation/swift#2984801.html).

Beispielsweise können Sie durch Verwendung der Methode „bridging header“ entsprechend der Beschreibung in der Dokumentation die iOS-SDK-Header-Datei in Adobe Mobile importieren:

```
#import “ADBMobile.h”
```

Verwenden Sie das folgende Format, um auf Methoden im SDK in Ihren Swift-Dateien zuzugreifen:

```
ADBMobile.{methodname}
```

