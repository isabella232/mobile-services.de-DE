---
description: Der Identitätsdienst für Adobe Experience Platform stellt eine universelle Besucher-ID für alle Experience Cloud-Lösungen bereit. Der ID-Service wird von Analytics für Target, Video-Heartbeats und künftige Experience Cloud-Integrationen benötigt.
seo-description: Der Identitätsdienst für Adobe Experience Platform stellt eine universelle Besucher-ID für alle Experience Cloud-Lösungen bereit. Der ID-Service wird von Analytics für Target, Video-Heartbeats und künftige Experience Cloud-Integrationen benötigt.
seo-title: Experience Cloud ID
solution: Marketing Cloud,Analytics
title: Experience Cloud ID
topic: Entwickler und Implementierung
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID {#experience-cloud-id}

The Adobe Experience Platform Identity Service provides a universal visitor ID across Experience Cloud solutions. Der ID-Service wird von Analytics für Target, Video-Heartbeats und künftige Experience Cloud-Integrationen benötigt.

>[!TIP]
>
>You do not need to populate the Experience Cloud ID unless you are using the Adobe Experience Platform Identity Service. For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

**Erfordert SDK-Version 4.3 (oder höher)**

## Enable the Experience Cloud ID {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   For more information, see Add the SDK and Config File to your Project in Core Implementation and Lifecycle.**[](/help/ios/getting-started/dev-qs.md)
1. Importieren Sie die Bibliothek:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verify that the  files contains the  :`ADBMobileConfig.json``marketingCloud``org`

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Experience Cloud-Organisations-IDs identifizieren jedes Kundenunternehmen in der Adobe Experience Cloud eindeutig und weisen folgendes Format auf: `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >You must include .`@AdobeOrg`

   If these values are not present, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Weitere Informationen finden Sie unter [ADBMobile JSON-Konfiguration](/help/ios/getting-started/requirements.md).

Nach der Konfiguration wird eine Experience Cloud ID generiert und für alle Treffer einbezogen. Andere Besucher-IDs, beispielsweise die benutzerdefinierten und automatisch generierten, werden weiterhin mit jedem Treffer gesendet.
