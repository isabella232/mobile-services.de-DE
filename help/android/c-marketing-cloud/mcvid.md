---
description: Der Identitätsdienst für Adobe Experience Platform stellt eine universelle Besucher-ID für alle Experience Cloud-Lösungen bereit. Der ID-Service wird von Analytics für Target, Video-Heartbeats und künftige Experience Cloud-Integrationen benötigt.
seo-description: Der Identitätsdienst für Adobe Experience Platform stellt eine universelle Besucher-ID für alle Experience Cloud-Lösungen bereit. Der ID-Service wird von Analytics für Target, Video-Heartbeats und künftige Experience Cloud-Integrationen benötigt.
seo-title: Experience Cloud ID configuration
solution: Marketing Cloud,Analytics
title: Experience Cloud ID configuration
topic: Entwickler und Implementierung
uuid: 8ebdf2bf-c581-448f-9542-f99a19784fe7
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID configuration {#experience-cloud-id-configuration}

The Adobe Experience Platform Identity Service provides a universal visitor ID across Experience Cloud solutions. Der ID-Service wird von Analytics für Target, Video-Heartbeats und künftige Experience Cloud-Integrationen benötigt.

>[!TIP]
>
>You do not need to populate this ID unless you are using the Adobe Experience Platform Identity Service. For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

>[!IMPORTANT]
>
>This functionality requires SDK version 4.3 or later.

So aktivieren Sie die Experience Cloud ID:

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   For more information, see Add the SDK and Config File to your IntelliJ IDEA or Eclipse Project in Core implementation and lifecycle.**[](/help/android/getting-started/dev-qs.md)

1. Importieren Sie die Bibliothek:

   ```java
   import com.adobe.mobile.*;
   ```

1. Vergewissern Sie sich, dass die `ADBMobileConfig.json` Datei die `marketingCloudorg`:

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Experience Cloud-Organisations-IDs identifizieren jedes Kundenunternehmen in der Adobe Experience Cloud eindeutig und weisen folgendes Format auf:

   ```js
   016D5C175213CCA80A490D05@AdobeOrg`
   ```

   >[!IMPORTANT]
   >
   >Sie müssen einschließen `@AdobeOrg`.

   If these IDs are not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Weitere Informationen finden Sie unter [Bevor Sie beginnen](/help/android/getting-started/requirements.md).

Nach der Konfiguration wird eine Experience Cloud ID generiert und für alle Treffer einbezogen. Auch andere IDs, z. B. benutzerdefinierte oder automatisch generierte IDs, werden weiterhin mit den Treffern gesendet.
