---
description: Sie können das Adobe SDK verwenden, um personenbezogene Daten (PII) zu erfassen und an einen Drittanbieter-Endpunkt zu senden.
seo-description: Sie können das Adobe SDK verwenden, um personenbezogene Daten (PII) zu erfassen und an einen Drittanbieter-Endpunkt zu senden.
seo-title: Postbacks personenbezogener Daten
title: Postbacks personenbezogener Daten
uuid: 8d1f1fb8-6842-478b-a164-e7f727755bd9
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 100%

---


# PII-Postbacks {#pii-postbacks}

Sie können das Adobe SDK verwenden, um personenbezogene Daten (PII) zu erfassen und an einen Drittanbieter-Endpunkt zu senden.

Wenn Sie PII mit dem Adobe SDK erfassen möchten, sollten Sie einen PII-Aufruf für die Verfolgung senden. Obwohl die Verwendung dieses Aufrufs die Erfassung von PII-Daten ermöglicht, sendet das SDK die Daten nicht automatisch an einen Adobe-Endpunkt. Ein Postback personenbezogener Daten muss mit dem entsprechenden Endpunkt konfiguriert werden.

>[!TIP]
>
>Zum Verwenden des PII-Postback-Typs ist ein Endpunkt erforderlich, der HTTPS unterstützt.

## PII-Postbacks verfolgen {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Konfigurationsdatei zu Ihrem IntelliJ IDEA- oder Eclipse-Projekt hinzufügen* in [Grundlegende Implementierung und Lebenszyklus](/help/android/getting-started/dev-qs.md).

1. Importieren Sie die Bibliothek:

   ```java
   #import "ADBMobile.h"
   ```

1. Wenn Sie bereit sind, personenbezogene Daten zu erfassen, rufen Sie `trackPII` auf, um einen Treffer für diese Aktion, dieses Ereignis oder diese Ansicht zu senden:

   ```java
   Config.collectPII(new HashMap<String, Object>(){{
     put("key","value");
   }});
   ```

