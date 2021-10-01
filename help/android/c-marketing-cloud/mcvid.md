---
description: Der Identity-Dienst für Adobe Experience Platform stellt eine universale Besucher-ID für alle Experience Cloud-Lösungen bereit. Der ID-Service wird von Analytics für Target, Video-Heartbeats und künftige Experience Cloud-Integrationen benötigt.
solution: Experience Cloud,Analytics
title: Experience Cloud ID-Konfiguration
topic-fix: Developer and implementation
uuid: 8ebdf2bf-c581-448f-9542-f99a19784fe7
exl-id: 97dc6768-bf31-4a0d-a460-9caf9ecda5fb
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 100%

---

# Experience Cloud ID-Konfiguration {#experience-cloud-id-configuration}

Der Identity-Dienst für Adobe Experience Platform stellt eine universale Besucher-ID für alle Experience Cloud-Lösungen bereit. Der ID-Service wird von Analytics für Target, Video-Heartbeats und künftige Experience Cloud-Integrationen benötigt.

>[!TIP]
>
>Sie müssen diese ID nicht angeben, wenn Sie den Identity-Dienst für Adobe Experience Platform nicht verwenden. Weitere Informationen finden Sie unter [Identity-Dienst für Adobe Experience Platform](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=de).

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

Nach Abschluss der Konfiguration wird eine Experience Cloud-ID generiert und allen Hits hinzugefügt. Andere IDs, beispielsweise die benutzerdefinierten und automatisch generierten, werden weiterhin mit jedem Treffer gesendet.
