---
description: Der Identity-Dienst für Adobe Experience Platform stellt eine universale Besucher-ID für alle Experience Cloud-Lösungen bereit. Der ID-Service wird von Analytics für Target, Video-Heartbeats und künftige Experience Cloud-Integrationen benötigt.
seo-description: Der Identity-Dienst für Adobe Experience Platform stellt eine universale Besucher-ID für alle Experience Cloud-Lösungen bereit. Der ID-Service wird von Analytics für Target, Video-Heartbeats und künftige Experience Cloud-Integrationen benötigt.
seo-title: Experience Cloud ID-Konfiguration
solution: Marketing Cloud,Analytics
title: Experience Cloud ID-Konfiguration
topic: Developer and implementation
uuid: 8ebdf2bf-c581-448f-9542-f99a19784fe7
translation-type: tm+mt
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa

---


# Experience Cloud ID-Konfiguration {#experience-cloud-id-configuration}

Der Identity-Dienst für Adobe Experience Platform stellt eine universale Besucher-ID für alle Experience Cloud-Lösungen bereit. Der ID-Service wird von Analytics für Target, Video-Heartbeats und künftige Experience Cloud-Integrationen benötigt.

>[!TIP]
>
>Sie müssen diese ID nicht angeben, wenn Sie den Identity-Dienst für Adobe Experience Platform nicht verwenden. Weitere Informationen finden Sie unter [Identity-Dienst für Adobe Experience Platform](https://docs.adobe.com/content/help/de-DE/id-service/using/home.html).

>[!IMPORTANT]
>
>Für diese Funktion ist die SDK-Version 4.3 oder höher erforderlich.

So aktivieren Sie die Experience Cloud ID:

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Konfigurationsdatei zu Ihrem IntelliJ IDEA- oder Eclipse-Projekt hinzufügen* in [Grundlegende Implementierung und Lebenszyklus](/help/android/getting-started/dev-qs.md).

1. Importieren Sie die Bibliothek:

   ```java
   import com.adobe.mobile.*;
   ```

1. Vergewissern Sie sich, dass die Datei `ADBMobileConfig.json` `marketingCloudorg` enthält:

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
   >Sie müssen `@AdobeOrg` einschließen.

   Wenn diese IDs nicht konfiguriert sind, sollten Sie eine aktualisierte Datei `ADBMobileConfig.json` aus Adobe Mobile Services herunterladen. Weitere Informationen finden Sie unter [Bevor Sie beginnen](/help/android/getting-started/requirements.md).

Nach Abschluss der Konfiguration wird eine Experience Cloud-ID generiert, die in allen Treffern enthalten ist. Andere IDs, z. B. benutzerdefinierte und automatisch generierte IDs, werden bei jedem Treffer weiterhin gesendet.
