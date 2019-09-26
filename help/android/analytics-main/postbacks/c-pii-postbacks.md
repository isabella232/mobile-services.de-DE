---
description: Sie können das Adobe-SDK verwenden, um personenbezogene Daten (Personally Identifiable Information, PII) zu erfassen und diese an Drittanbieter-Endpunkte zu senden.
seo-description: Sie können das Adobe-SDK verwenden, um personenbezogene Daten (Personally Identifiable Information, PII) zu erfassen und diese an Drittanbieter-Endpunkte zu senden.
seo-title: Postbacks personenbezogener Daten
title: Postbacks personenbezogener Daten
uuid: 8d1f1fb8-6842-478b-a164-e7f727755bd9
translation-type: tm+mt
source-git-commit: 70ac08c74e11a68d94d3f10ed6d7fc133d34149d

---


# PII postbacks {#pii-postbacks}

Sie können das Adobe-SDK verwenden, um personenbezogene Daten (Personally Identifiable Information, PII) zu erfassen und diese an Drittanbieter-Endpunkte zu senden.

Wenn Sie das Adobe-SDK zum Erfassen personenbezogener Daten nutzen wollen, sollten Sie einen trackPII-Aufruf senden. Obwohl die Verwendung dieses Aufrufs die Sammlung von PII-Daten ermöglicht, sendet das SDK die Daten nicht automatisch an einen Adobe-Endpunkt. Ein Postback personenbezogener Daten muss mit dem entsprechenden Endpunkt konfiguriert werden.

>[!TIP]
>
>Ein Endpunkt, der HTTPS unterstützt, ist erforderlich, um den PII-Postback-Typ zu verwenden.

## Tracking PII postbacks {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Fügen Sie [die Bibliothek] zum Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK- und Konfigurationsdatei zu Ihrer IntelliJ-IDEA- oder Eclipse-Projekt* in der [Core-Implementierung und im Lebenszyklus](/help/android/getting-started/dev-qs.md)hinzufügen.

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

