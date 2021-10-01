---
description: Sie können das Adobe SDK verwenden, um personenbezogene Daten (PII) zu erfassen und an einen Drittanbieter-Endpunkt zu senden.
title: Postbacks personenbezogener Daten
uuid: 08f76a52-75dd-4fc1-b4cc-4f5eef93d0f7
exl-id: 180c21f7-0fba-4b9b-ab7f-7afe81b85f38
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 86%

---

# PII-Postbacks {#pii-postbacks}

Sie können das Adobe SDK verwenden, um personenbezogene Daten (PII) zu erfassen und an einen Drittanbieter-Endpunkt zu senden.

Wenn Sie PII mit dem Adobe SDK erfassen möchten, sollten Sie einen PII-Aufruf für die Verfolgung senden. Obwohl die Verwendung dieses Aufrufs die Erfassung von PII-Daten ermöglicht, sendet das SDK die Daten nicht automatisch an einen Adobe-Endpunkt. Ein Postback personenbezogener Daten muss mit dem entsprechenden Endpunkt konfiguriert werden.

>[!TIP]
>
>Zum Verwenden des PII-Postback-Typs ist ein Endpunkt erforderlich, der HTTPS unterstützt.

## PII-Postbacks verfolgen {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Konfigurationsdatei zum Projekt hinzufügen* im Abschnitt [Grundlegende Implementierung und Lebenszyklus](/help/ios/getting-started/dev-qs.md).
1. Importieren Sie die Bibliothek:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Wenn Sie bereit sind, personenbezogene Daten zu erfassen, rufen Sie `trackPII` auf, um einen Treffer für diese Aktion, dieses Ereignis oder diese Ansicht zu senden:

   ```objective-c
   [ADBMobile collectPII data:nil];
   ```
