---
description: Sie können das Adobe-SDK verwenden, um personenbezogene Daten (Personally Identifiable Information, PII) zu erfassen und diese an Drittanbieter-Endpunkte zu senden.
seo-description: Sie können das Adobe-SDK verwenden, um personenbezogene Daten (Personally Identifiable Information, PII) zu erfassen und diese an Drittanbieter-Endpunkte zu senden.
seo-title: Postbacks personenbezogener Daten
title: Postbacks personenbezogener Daten
uuid: 08f76a52-75dd-4fc1-b4cc-4f5eef93d0f7
translation-type: ht
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# PII-Postbacks {#pii-postbacks}

Sie können das Adobe-SDK verwenden, um personenbezogene Daten (Personally Identifiable Information, PII) zu erfassen und diese an Drittanbieter-Endpunkte zu senden.

Wenn Sie das Adobe-SDK zum Erfassen personenbezogener Daten nutzen wollen, sollten Sie einen trackPII-Aufruf senden. Obwohl dieser Aufruf die Erfassung personenbezogener Daten ermöglicht, sendet das SDK die Daten nicht automatisch an einen Adobe-Endpunkt. Ein Postback personenbezogener Daten muss mit dem entsprechenden Endpunkt konfiguriert werden.

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

