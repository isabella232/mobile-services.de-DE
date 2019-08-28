---
description: Sie können das Adobe-SDK verwenden, um personenbezogene Daten (Personally Identifiable Information, PII) zu erfassen und diese an Drittanbieter-Endpunkte zu senden.
seo-description: Sie können das Adobe-SDK verwenden, um personenbezogene Daten (Personally Identifiable Information, PII) zu erfassen und diese an Drittanbieter-Endpunkte zu senden.
seo-title: Postbacks personenbezogener Daten
title: Postbacks personenbezogener Daten
uuid: 08 f 76 a 52-75 dd -4 fc 1-b 4 cc -4 f 5 eef 93 d 0 f 7
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# PII postbacks {#pii-postbacks}

Sie können das Adobe-SDK verwenden, um personenbezogene Daten (Personally Identifiable Information, PII) zu erfassen und diese an Drittanbieter-Endpunkte zu senden.

Wenn Sie das Adobe-SDK zum Erfassen personenbezogener Daten nutzen wollen, sollten Sie einen trackPII-Aufruf senden. Obwohl dieser Aufruf die Erfassung personenbezogener Daten ermöglicht, sendet das SDK die Daten nicht automatisch an einen Adobe-Endpunkt. Ein Postback personenbezogener Daten muss mit dem entsprechenden Endpunkt konfiguriert werden.

>[!TIP]
>
>Ein Endpunkt, der HTTPS unterstützt, ist erforderlich, um den Postback-Typ PII zu verwenden.

## Tracking PII postbacks {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden *Sie unter SDK und Config File to your Project* in [Core Implementation and Lifecycle](/help/ios/getting-started/dev-qs.md).
1. Importieren Sie die Bibliothek:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Wenn Sie bereit sind, personenbezogene Daten zu erfassen, rufen Sie `trackPII` auf, um einen Treffer für diese Aktion, dieses Ereignis oder diese Ansicht zu senden:

   ```objective-c
   [ADBMobile collectPII data:nil];
   ```

