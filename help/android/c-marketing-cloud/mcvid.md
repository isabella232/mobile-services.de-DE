---
description: Der Adobe Experience Platform Identity Service bietet eine universelle Besucher-ID für die Experience Cloud-Lösungen. Der ID-Service wird von Analytics für Target, Video-Heartbeats und künftige Experience Cloud-Integrationen benötigt.
seo-description: Der Adobe Experience Platform Identity Service bietet eine universelle Besucher-ID für die Experience Cloud-Lösungen. Der ID-Service wird von Analytics für Target, Video-Heartbeats und künftige Experience Cloud-Integrationen benötigt.
seo-title: Experience Cloud ID-Konfiguration
solution: Marketing Cloud, Analytics
title: Experience Cloud ID-Konfiguration
topic: Entwickler und Implementierung
uuid: 8 ebdf 2 bf-c 581-448 f -9542-f 99 a 19784 fe 7
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID configuration {#experience-cloud-id-configuration}

Der Adobe Experience Platform Identity Service bietet eine universelle Besucher-ID für die Experience Cloud-Lösungen. Der ID-Service wird von Analytics für Target, Video-Heartbeats und künftige Experience Cloud-Integrationen benötigt.

>[!TIP]
>
>Sie müssen diese ID nur ausfüllen, wenn Sie den Adobe Experience Platform Identity Service verwenden. For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

>[!IMPORTANT]
>
>Für diese Funktion ist SDK Version 4.3 oder höher erforderlich.

So aktivieren Sie die Experience Cloud ID:

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Config File to your intellij IDEA oder Eclipse Project* in [Core Implementation and Lifecycle](/help/android/getting-started/dev-qs.md).

1. Importieren Sie die Bibliothek:

   ```java
   import com.adobe.mobile.*;
   ```

1. Überprüfen Sie, ob die `ADBMobileConfig.json` Datei Folgendes `marketingCloudorg`enthält:

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
   >Sie müssen Folgendes einschließen `@AdobeOrg`.

   If these IDs are not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Weitere Informationen finden Sie unter [Bevor Sie beginnen](/help/android/getting-started/requirements.md).

Nach der Konfiguration wird eine Experience Cloud ID generiert und für alle Treffer einbezogen. Auch andere IDs, z. B. benutzerdefinierte oder automatisch generierte IDs, werden weiterhin mit den Treffern gesendet.
