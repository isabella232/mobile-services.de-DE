---
description: Der Identity-Dienst für Adobe Experience Platform stellt eine universale Besucher-ID für alle Experience Cloud-Lösungen bereit. Der ID-Service wird von Analytics für Target, Video-Heartbeats und künftige Experience Cloud-Integrationen benötigt.
seo-description: Der Identity-Dienst für Adobe Experience Platform stellt eine universale Besucher-ID für alle Experience Cloud-Lösungen bereit. Der ID-Service wird von Analytics für Target, Video-Heartbeats und künftige Experience Cloud-Integrationen benötigt.
seo-title: Experience Cloud ID
solution: Experience Cloud,Analytics
title: Experience Cloud-ID
topic-fix: Developer and implementation
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
exl-id: aa7db365-ad21-431f-bff6-2a6da212dd0c
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 100%

---

# Experience Cloud ID {#experience-cloud-id}

Der Identity-Dienst für Adobe Experience Platform stellt eine universale Besucher-ID für alle Experience Cloud-Lösungen bereit. Der ID-Service wird von Analytics für Target, Video-Heartbeats und künftige Experience Cloud-Integrationen benötigt.

>[!TIP]
>
>Sie müssen die Experience Cloud ID nicht angeben, wenn Sie den Identity-Dienst für Adobe Experience Platform nicht verwenden. Weitere Informationen finden Sie unter [Identity-Dienst für Adobe Experience Platform](https://docs.adobe.com/content/help/de-DE/id-service/using/home.html).

**Erfordert SDK-Version 4.3 (oder höher)**

## Experience Cloud ID aktivieren {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Konfigurationsdatei zum Projekt hinzufügen* im Abschnitt [Grundlegende Implementierung und Lebenszyklus](/help/ios/getting-started/dev-qs.md).
1. Importieren Sie die Bibliothek:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Vergewissern Sie sich, dass die `ADBMobileConfig.json`-Dateien `marketingCloud` `org` enthalten:

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Experience Cloud-Organisations-IDs identifizieren jedes Kundenunternehmen in der Adobe Experience Cloud eindeutig und weisen folgendes Format auf: `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >Sie müssen `@AdobeOrg` einschließen.

   Wenn diese Werte nicht vorhanden sind, sollten Sie eine aktualisierte `ADBMobileConfig.json`-Datei aus Adobe Mobile Services herunterladen. Weitere Informationen finden Sie unter [ADBMobile JSON-Konfiguration](/help/ios/getting-started/requirements.md).

Nach der Konfiguration wird eine Experience Cloud-ID generiert und allen Treffern hinzugefügt. Andere Besucher-IDs, beispielsweise die benutzerdefinierten und automatisch generierten, werden weiterhin mit jedem Treffer gesendet.
