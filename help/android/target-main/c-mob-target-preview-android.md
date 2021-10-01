---
description: Mit der Target-Vorschau können Sie einfach Ende-zu-Ende-Qualitätssicherung für Target-Aktivitäten betreiben und diese Aktivitäten auf Ihrem Gerät ansehen.
title: Target-Vorschau auf Android
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
exl-id: 69103f3a-9521-4808-8ecd-7b960efca04d
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 74%

---

# Target-Vorschau auf Android {#target-preview-on-android}

Mit der Target-Vorschau können Sie einfach Ende-zu-Ende-Qualitätssicherung für Target-Aktivitäten betreiben und diese Aktivitäten auf Ihrem Gerät ansehen.

Weitere Informationen zum Einrichten und Verwenden der Target-Vorschau finden Sie unter [Target Mobile Preview](https://experienceleague.adobe.com/docs/target/using/implement-target/mobile-apps/target-mobile-preview.html) im Adobe Target-Benutzerhandbuch.

>[!IMPORTANT]
>
>Um die Target-Vorschau verwenden zu können, benötigen Sie SDK-Version 4.14.0 oder höher.

* **setPreviewRestartDeeplink**

   Legt einen App-Deeplink fest, der ausgelöst wird, wenn Vorschauauswahlen im Vorschaumodus angewendet werden.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void setPreviewRestartDeeplink(String deeplink);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Target.setPreviewRestartDeeplink("myapp://myhost"); 
      ```
