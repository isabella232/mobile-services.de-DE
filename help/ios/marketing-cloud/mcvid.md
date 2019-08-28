---
description: Der Adobe Experience Platform Identity Service bietet eine universelle Besucher-ID für die Experience Cloud-Lösungen. Der ID-Service wird von Analytics für Target, Video-Heartbeats und künftige Experience Cloud-Integrationen benötigt.
seo-description: Der Adobe Experience Platform Identity Service bietet eine universelle Besucher-ID für die Experience Cloud-Lösungen. Der ID-Service wird von Analytics für Target, Video-Heartbeats und künftige Experience Cloud-Integrationen benötigt.
seo-title: Experience Cloud ID
solution: Marketing Cloud, Analytics
title: Experience Cloud ID
topic: Entwickler und Implementierung
uuid: 13628 ea 8-3 cd 4-4 cfc -8 ff 6-722 c 33 f 7813 a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID {#experience-cloud-id}

Der Adobe Experience Platform Identity Service bietet eine universelle Besucher-ID für die Experience Cloud-Lösungen. Der ID-Service wird von Analytics für Target, Video-Heartbeats und künftige Experience Cloud-Integrationen benötigt.

>[!TIP]
>
>Sie müssen die Experience Cloud ID nur ausfüllen, wenn Sie den Adobe Experience Platform Identity Service verwenden. For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

**Erfordert SDK-Version 4.3 (oder höher)**

## Aktivieren der Experience Cloud ID {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden *Sie unter SDK und Config File to your Project* in [Core Implementation and Lifecycle](/help/ios/getting-started/dev-qs.md).
1. Importieren Sie die Bibliothek:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Überprüfen Sie, ob `ADBMobileConfig.json` die Dateien Folgendes `marketingCloud``org`enthalten:

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Experience Cloud-Organisations-IDs identifizieren jedes Kundenunternehmen in der Adobe Experience Cloud eindeutig und weisen folgendes Format auf: `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >Sie müssen Folgendes einschließen `@AdobeOrg`.

   If these values are not present, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Weitere Informationen finden Sie unter [adbmobile JSON-Konfiguration](/help/ios/getting-started/requirements.md).

Nach der Konfiguration wird eine Experience Cloud ID generiert und für alle Treffer einbezogen. Andere Besucher-IDs, beispielsweise die benutzerdefinierten und automatisch generierten, werden weiterhin mit jedem Treffer gesendet.
