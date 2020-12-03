---
description: Mit der Target-Vorschau können Sie einfach Ende-zu-Ende-Qualitätssicherung für Target-Aktivitäten betreiben und diese Aktivitäten auf Ihrem Gerät ansehen.
seo-description: Mit der Target-Vorschau können Sie einfach Ende-zu-Ende-Qualitätssicherung für Target-Aktivitäten betreiben und diese Aktivitäten auf Ihrem Gerät ansehen.
seo-title: Target-Vorschau auf Android
title: Target-Vorschau auf Android
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
translation-type: tm+mt
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 87%

---


# Target-Vorschau auf Android {#target-preview-on-android}

Mit der Target-Vorschau können Sie einfach Ende-zu-Ende-Qualitätssicherung für Target-Aktivitäten betreiben und diese Aktivitäten auf Ihrem Gerät ansehen.

For more information on how to set up and use Target Preview, go to [Target Mobile Preview](https://docs.adobe.com/content/help/de-DE/target/using/implement-target/mobile-apps/target-mobile-preview.html).

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
      Target.setPreviewRestartDeeplink(“myapp://myhost”); 
      ```

